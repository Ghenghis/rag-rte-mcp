# Evony RAG Lab: Offline Hyper-V implementation plan

Status: planned and partially verified on 2026-10-29.

This plan turns the existing `Evony-RAG-Lab` Hyper-V VM into a reproducible, offline environment for local RAG analysis and static or simulated RTE verification. It explicitly excludes connections to game servers, real game actions, purchases, live packet capture, and production-mode exploit execution.

## Verified starting point

- The VM `Evony-RAG-Lab` is running in Hyper-V Manager.
- It is a Generation 2 VM using configuration version 12.0.
- Hyper-V Manager shows an automatic checkpoint created on 2026-10-28 at 21:50:53.
- The disk chain contains `D:\hyper\VHDX\Evony-RAG-Lab.vhdx` and an `Evony-RAG-Lab_*.avhdx` differencing disk. Any backup or export must preserve this chain through Hyper-V rather than copying only the base VHDX.
- `D:\hyper\Backups` did not exist during the check. The `D:` drive had about 117.9 GiB free.
- The host repository was clean at commit `ce2ccf9ffbbd33ebf65e6c3536d5c9ea379a3607`.
- The repository contained about 3.16 GiB across 56,717 files.
- Python 3.11.9 was available on the host, but the checked repository virtual environment did not contain the declared RAG dependencies.
- Static parsing succeeded for 115 top-level RAG/RTE Python files.

## Safety boundary

The following rules apply to every phase:

1. Keep the VM's virtual network adapter disconnected from all virtual switches unless a separate, explicit change request authorizes a specific connection.
2. Do not connect to Evony or other game servers.
3. Do not execute real game commands, purchases, refreshes, logins, proxy forwarding, packet capture, or production exploit paths.
4. Do not run `evony_rte.server_launcher`, `evony_rte.proxy_hook`, or network-capable game handlers during validation.
5. Treat RTE source and captured material as untrusted data. Execute only a reviewed, network-denied test harness with synthetic packets.
6. Do not transfer account files, login exports, key material, host virtual environments, caches, or Git metadata into the guest.
7. Record every change, resulting path, verification result, and unresolved prerequisite.

## Work items

| ID | Priority | Work item | Depends on | Completion evidence |
|---|---|---|---|---|
| LAB-01 | P0 | Capture an elevated, read-only Hyper-V inventory | None | VM state, firmware, Secure Boot, vTPM, boot order, disk chain, CPU, RAM, network adapter, integration services, and checkpoints recorded without changing the VM |
| LAB-02 | P0 | Enforce offline isolation and disable sharing paths | LAB-01 | NIC has no switch; enhanced-session clipboard, drive, printer, audio, and device sharing are disabled; Guest Service Interface is disabled except during an approved one-way transfer |
| LAB-03 | P0 | Complete and verify the Windows 11 guest baseline | LAB-02 | Windows edition/build, local account state, Defender, Firewall, activation state, Python availability, and guest free space recorded; no Internet connection used |
| LAB-04 | P0 | Create a named clean checkpoint and full Hyper-V export | LAB-03 | Checkpoint name and timestamp recorded; export exists below `D:\hyper\Backups\Evony-RAG-Lab\<timestamp>` and contains configuration, snapshots, and virtual disks; export size and file hashes recorded |
| LAB-05 | P0 | Build a sanitized transfer bundle | LAB-01 | Bundle manifest, exclusion report, file count, size, and SHA-256 hashes recorded; sensitive paths and executable host environment are absent |
| LAB-06 | P1 | Prepare Python 3.11 and an offline dependency wheelhouse | LAB-03 | Python 3.11 guest version recorded; pinned wheelhouse and package hashes exist; installation works with package index access disabled |
| LAB-07 | P1 | Run a local-only RAG smoke test | LAB-05, LAB-06 | Test uses local documents and local embeddings only; LM Studio/OpenAI endpoints are disabled; network-deny guard reports no attempted external connection; query and citation output are archived |
| LAB-08 | P1 | Run static and simulated RTE verification | LAB-05, LAB-06 | Source scan completes; synthetic AMF3 encode/decode tests pass under socket/HTTP deny patches; no proxy, packet capture, game handler, server launcher, purchase, or login path runs |
| LAB-09 | P2 | Archive evidence and synchronize documentation | LAB-04, LAB-07, LAB-08 | GitHub, Notion, and Obsidian contain matching status, evidence links, blockers, and next decision; no secret or account content is copied into documentation |

GitHub tracking: [LAB-01](https://github.com/Ghenghis/rag-rte-mcp/issues/2), [LAB-02](https://github.com/Ghenghis/rag-rte-mcp/issues/3), [LAB-03](https://github.com/Ghenghis/rag-rte-mcp/issues/4), [LAB-04](https://github.com/Ghenghis/rag-rte-mcp/issues/5), [LAB-05](https://github.com/Ghenghis/rag-rte-mcp/issues/6), [LAB-06](https://github.com/Ghenghis/rag-rte-mcp/issues/7), [LAB-07](https://github.com/Ghenghis/rag-rte-mcp/issues/8), [LAB-08](https://github.com/Ghenghis/rag-rte-mcp/issues/9), and [LAB-09](https://github.com/Ghenghis/rag-rte-mcp/issues/10).

## Sanitized transfer specification

The full working tree is not a safe transfer unit. The bundle must be generated from an explicit allowlist and reviewed before it is copied.

Include only:

- reviewed RAG and RTE Python source required for static analysis and synthetic packet tests;
- neutral documentation and protocol descriptions required by the RAG corpus;
- dedicated synthetic fixtures created for the lab;
- pinned dependency manifests, hashes, and the offline test harness;
- a machine-readable manifest containing relative paths, sizes, and SHA-256 hashes.

Exclude at minimum:

- `.git`, `.venv`, `__pycache__`, caches, logs, generated output, and host-specific configuration;
- `Accounts`, `Keys`, account exports, login files, wallet or credential material;
- `BorgToolkit/data/accounts`, `BorgToolkit/data/exports`, `BorgToolkit/data/final_accounts`, and `BorgToolkit/data/login_files`;
- `Evony_Dataset/game_data` and similarly named duplicated datasets until each file is explicitly classified;
- live captures, proxy configuration, production launchers, and any file containing private credentials or personal data.

The preferred transfer path is a one-way Hyper-V Guest Service copy while the VM has no virtual switch. Enable the Guest Service Interface only for the transfer, verify the destination, copy the reviewed bundle, and disable the service immediately afterward. If the guest service is unavailable, use a separately created, read-only transfer image after a dedicated review; do not mount or modify the active OS checkpoint chain directly.

## Offline dependency approach

Dependency installation inside the isolated guest requires a host-prepared wheelhouse. Resolve and download only the pinned Python 3.11 wheels needed by the selected smoke test, record hashes, scan the bundle, then install with package-index access disabled. Do not copy the host `.venv` into the guest.

The first smoke test should prefer the smallest dependency set that proves local retrieval. Optional HTTP clients and UI/server packages are excluded unless a later test specifically requires them. Model artifacts must already exist locally and must be added to the manifest; the guest must not download models.

## Validation gates

### Gate A: inventory complete

- [ ] Exact VM settings are captured with elevated read-only Hyper-V commands.
- [ ] Current guest state and Windows build are known.
- [ ] The active disk and checkpoint relationships are verified.

### Gate B: isolation complete

- [ ] The virtual NIC is disconnected from every switch.
- [ ] Enhanced-session resource sharing is disabled.
- [ ] No host folder, clipboard, drive, printer, or device remains shared.
- [ ] A network-deny test confirms that the guest cannot reach external addresses.

### Gate C: recoverability complete

- [ ] The clean checkpoint exists.
- [ ] The full export is stored below `D:\hyper\Backups`, separate from active VM files.
- [ ] Export contents and hashes are verified.

### Gate D: local analysis complete

- [ ] The sanitized bundle passes its exclusion checks.
- [ ] Python and dependencies install offline from verified local wheels.
- [ ] Local RAG retrieval succeeds without remote endpoints.
- [ ] RTE validation uses only static analysis and synthetic packets with network calls blocked.

## Current blockers

- The normal user token cannot read detailed Hyper-V settings. LAB-01 requires an elevated, read-only diagnostic session approved through Windows UAC.
- Windows guest setup status, build, edition, account state, and installed software are not yet verified.
- A pinned Python 3.11 wheelhouse and local embedding model bundle do not yet exist.
- A safe synthetic RTE test harness that fails closed on every socket and HTTP attempt still needs to be added and reviewed.

## Documentation record

Every completed task must record:

- timestamp and operator;
- exact source and destination paths;
- commands or UI actions used;
- resulting state and verification output;
- hashes for exported or transferred artifacts;
- blockers and the next approval point.

