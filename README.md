<div align="center">

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║   ███████╗██╗   ██╗ ██████╗ ███╗   ██╗██╗   ██╗    ███╗   ███╗ ██████╗██████╗ ║
║   ██╔════╝██║   ██║██╔═══██╗████╗  ██║╚██╗ ██╔╝    ████╗ ████║██╔════╝██╔══██╗║
║   ███████╗██║   ██║██║   ██║██╔██╗ ██║ ╚████╔╝     ██╔████╔██║██║     ██████╔╝║
║   ╚════██║╚██╗ ██╔╝██║   ██║██║╚██╗██║  ╚██╔╝      ██║╚██╔╝██║██║     ██╔═══╝ ║
║   ███████║ ╚████╔╝ ╚██████╔╝██║ ╚████║   ██║       ██║ ╚═╝ ██║╚██████╗██║     ║
║   ╚══════╝  ╚═══╝   ╚═════╝ ╚═╝  ╚═══╝   ╚═╝       ╚═╝     ╚═╝ ╚═════╝╚═╝     ║
║                                                                               ║
║            🔮 Advanced Reverse Engineering Intelligence Platform 🔮           ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-00ff00?style=for-the-badge&logo=python&logoColor=white&labelColor=0d1117" alt="Python"/>
  <img src="https://img.shields.io/badge/Node.js-18+-00ff00?style=for-the-badge&logo=nodedotjs&logoColor=white&labelColor=0d1117" alt="Node.js"/>
  <img src="https://img.shields.io/badge/MCP-Protocol-00ff00?style=for-the-badge&logo=api&logoColor=white&labelColor=0d1117" alt="MCP"/>
  <img src="https://img.shields.io/badge/RAG-Hybrid-00ff00?style=for-the-badge&logo=elasticsearch&logoColor=white&labelColor=0d1117" alt="RAG"/>
</p>

<p align="center">
  <strong>🎯 166,043 Indexed Chunks</strong> • 
  <strong>🔍 55,871 Symbols</strong> • 
  <strong>⚡ Hybrid BM25 + Semantic Search</strong> •
  <strong>📡 301+ Protocol Commands</strong>
</p>

---

</div>

## 🚀 Overview

**Svony MCP** is an advanced Model Context Protocol server providing AI-powered reverse engineering intelligence for game protocol analysis. It combines lexical search (BM25) with semantic embeddings to deliver precise code discovery and protocol analysis.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        SVONY INTELLIGENCE ENGINE                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   ┌───────────────┐     ┌───────────────┐     ┌───────────────┐            │
│   │   WINDSURF    │────▶│   MCP SERVER  │────▶│  RAG ENGINE   │            │
│   │     IDE       │◀────│   (stdio)     │◀────│  (hybrid)     │            │
│   └───────────────┘     └───────────────┘     └───────────────┘            │
│          │                     │                      │                     │
│          │              ┌──────┴──────┐        ┌──────┴──────┐             │
│          │              │   Node.js   │        │   166,043   │             │
│          ▼              │   Wrapper   │        │   Chunks    │             │
│   ┌───────────────┐     └─────────────┘        └─────────────┘             │
│   │   AI TOOLS    │            │                      │                     │
│   │  • search     │     ┌──────┴──────┐        ┌──────┴──────┐             │
│   │  • stats      │     │  No stderr  │        │   55,871    │             │
│   │  • mode       │     │  File logs  │        │   Symbols   │             │
│   └───────────────┘     └─────────────┘        └─────────────┘             │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 📊 Knowledge Base

<table>
<tr>
<td>

### 📁 Indexed Content
| Category | Files | Description |
|----------|-------|-------------|
| Source Code | 7,469 | ActionScript, Python, JS |
| Protocol | 85 | AMF, Commands, Packets |
| Scripts | 106 | AutoEvony, Automation |
| Keys | 1,230 | Encryption, Signatures |
| Exploits | 26 | Vulnerabilities |

</td>
<td>

### 🔧 Search Capabilities
| Feature | Specification |
|---------|---------------|
| Chunks | 166,043 indexed |
| Symbols | 55,871 extracted |
| BM25 | Lexical matching |
| Embeddings | 384-dimensional |
| Fusion | Reciprocal Rank |

</td>
</tr>
</table>

---

## 🛠️ MCP Tools

```
╔══════════════════════════════════════════════════════════════════════════════╗
║  TOOL              ║  DESCRIPTION                           ║  PARAMETERS   ║
╠══════════════════════════════════════════════════════════════════════════════╣
║  evony_search      ║  Hybrid lexical+semantic search        ║  query, k     ║
║  evony_stats       ║  Knowledge base statistics             ║  -            ║
║  evony_mode        ║  Get/set query mode                    ║  mode?        ║
╚══════════════════════════════════════════════════════════════════════════════╝
```

### 🔐 Query Modes

| Mode | Access Level | Use Case |
|------|--------------|----------|
| `research` | Standard | General protocol analysis |
| `forensics` | Extended | Deep vulnerability research |
| `full_access` | Complete | Unrestricted data access |

---

## ⚡ Quick Start

### 1️⃣ Clone & Install
```bash
git clone https://github.com/Ghenghis/Svony-mcp.git
cd Svony-mcp
pip install -r requirements.txt
```

### 2️⃣ Configure Windsurf
Add to `~/.codeium/windsurf/mcp_config.json`:
```json
{
  "mcpServers": {
    "evony-knowledge": {
      "command": "node",
      "args": ["/path/to/Svony-mcp/evony_mcp_wrapper.js"]
    }
  }
}
```

### 3️⃣ Search!
```python
evony_search("ACTION_KEY encryption")      # Find encryption keys
evony_search("army.newArmy protocol")      # Protocol commands
evony_search("overflow exploit threshold") # Vulnerability research
```

---

## 🔐 Encryption Keys Reference

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         EXTRACTED ENCRYPTION KEYS                            │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ACTION_KEY     │ TAO_{313-894*&*($*#-FDIU(430}-{facebook_dioe(&*%$l}      │
│  USER_INFO_KEY  │ IUGI_md5_key_{djfiji3*4930}-{fjdi3284$9dlld}             │
│  API_KEY        │ 9f758e2deccbe6244f734371b9642eda                         │
│  XOR_KEY        │ 0xAA (170 decimal)                                       │
│  LOGIN_SALT     │ evony                                                    │
│                                                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│  SIGNATURE: MD5(data + ACTION_KEY)                                          │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 💥 Exploit Thresholds

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                     INTEGER OVERFLOW THRESHOLDS                              │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Troop Type     │  Cost  │  Overflow Threshold  │  Formula                 │
│  ──────────────────────────────────────────────────────────────────────    │
│  Archer         │  350   │  6,135,037           │  INT32_MAX / 350 + 1     │
│  Worker         │  50    │  42,949,673          │  INT32_MAX / 50 + 1      │
│  Catapult       │  3000  │  715,828             │  INT32_MAX / 3000 + 1    │
│  Cavalry        │  500   │  4,294,968           │  INT32_MAX / 500 + 1     │
│  Warrior        │  100   │  21,474,837          │  INT32_MAX / 100 + 1     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 🏗️ Architecture

```
svony-mcp/
│
├── 📄 evony_mcp_wrapper.js        # Node.js stdio wrapper (ignores stderr)
├── 📄 requirements.txt            # Python dependencies
├── 📄 README.md                   # This file
│
├── 📁 evony_rag/                  # ═══════════════════════════════════════
│   ├── 🔧 mcp_server_clean.py     # MCP server - NO STDERR (Windsurf fix)
│   ├── 🔧 rag_v2.py               # RAG orchestrator engine
│   ├── 🔧 hybrid_search.py        # BM25 + semantic fusion (RRF)
│   ├── 🔧 embeddings.py           # Vector embeddings (384-dim)
│   ├── 🔧 policy.py               # Query mode access control
│   ├── 🔧 config.py               # Configuration constants
│   └── 📁 logs/                   # File-only logging
│
└── 📁 docs/                       # ═══════════════════════════════════════
    ├── 📖 README.md               # Documentation index
    ├── 📁 keys/                   # Encryption keys & signatures
    │   └── ENCRYPTION_KEYS.md
    ├── 📁 protocols/              # Protocol reference (301+ commands)
    │   ├── COMMANDS.md
    │   └── AMF_PROTOCOL.md
    ├── 📁 exploits/               # Vulnerability documentation
    │   └── EXPLOITS.md
    └── 📁 diagrams/               # Architecture diagrams
        └── ARCHITECTURE.md
```

---

## 📡 Protocol Commands (301+)

<details>
<summary><strong>🗡️ Army Commands</strong></summary>

| Command | Description | Parameters |
|---------|-------------|------------|
| `army.newArmy` | Create army | cityId, heroId, troops[] |
| `army.getArmyByCity` | Get armies | cityId |
| `army.attackOtherPlayer` | Attack | armyId, targetCityId |
| `army.scout` | Scout target | armyId, x, y |
| `army.disbandArmy` | Disband | armyId |

</details>

<details>
<summary><strong>🏃 Troop Commands</strong></summary>

| Command | Description | Parameters |
|---------|-------------|------------|
| `troop.produceTroop` | Train troops | cityId, type, num |
| `troop.cancelProduceTroop` | Cancel | cityId, type |
| `troop.disbandTroop` | Disband | cityId, type, num |
| `troop.getProduceQueue` | Get queue | cityId |

</details>

<details>
<summary><strong>🏰 Building Commands</strong></summary>

| Command | Description | Parameters |
|---------|-------------|------------|
| `castle.newBuilding` | Build | cityId, posId, typeId |
| `castle.upgradeBuilding` | Upgrade | cityId, posId |
| `castle.destructBuilding` | Destroy | cityId, posId |
| `castle.speedUpBuilding` | Speed up | cityId, posId, itemId |

</details>

<details>
<summary><strong>👤 Hero Commands</strong></summary>

| Command | Description | Parameters |
|---------|-------------|------------|
| `hero.fireHero` | Dismiss | heroId |
| `hero.promoteHero` | Promote | heroId |
| `hero.resetAttrPoint` | Reset stats | heroId |
| `hero.addAttrPoint` | Add points | heroId, attr, num |

</details>

---

## 🔬 Search Pipeline

```
                              HYBRID SEARCH PIPELINE
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   Query: "ACTION_KEY encryption"                                            │
│                    │                                                        │
│          ┌────────┴────────┐                                                │
│          ▼                 ▼                                                │
│   ┌─────────────┐   ┌─────────────┐                                         │
│   │    BM25     │   │  Semantic   │                                         │
│   │   Lexical   │   │  Embedding  │                                         │
│   │   Search    │   │   Search    │                                         │
│   └──────┬──────┘   └──────┬──────┘                                         │
│          │                 │                                                │
│          │   k=20          │   k=20                                         │
│          │                 │                                                │
│          └────────┬────────┘                                                │
│                   ▼                                                         │
│          ┌─────────────────┐                                                │
│          │   RRF Fusion    │  score = Σ(1 / (60 + rank))                    │
│          └────────┬────────┘                                                │
│                   │                                                         │
│                   ▼                                                         │
│          ┌─────────────────┐                                                │
│          │  Top K Results  │  Ranked by combined score                      │
│          └─────────────────┘                                                │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## ⚙️ Technical Specifications

| Component | Specification |
|-----------|---------------|
| **Search Engine** | Hybrid BM25 + Semantic |
| **Embedding Model** | all-MiniLM-L6-v2 (384d) |
| **Index Size** | 166,043 chunks |
| **Symbol Index** | 55,871 symbols |
| **Fusion Algorithm** | Reciprocal Rank Fusion |
| **MCP Transport** | stdio (JSON-RPC) |
| **Logging** | File-only (no stderr) |

---

## 🔒 Security Notes

- ⚠️ **Review before transfer** - The current tree includes account-, login-, and key-related material. Do not copy the full repository into a lab or share it without an explicit allowlist and secret review.
- ✅ **Policy-controlled access** - Three query modes
- ✅ **Windsurf compatible** - No stderr output (causes Error status)
- ✅ **Input sanitization** - BOM stripping, JSON validation

---

## 📚 Documentation

| Document | Description | Link |
|----------|-------------|------|
| 🔐 Encryption Keys | All keys & signatures | [View](docs/keys/ENCRYPTION_KEYS.md) |
| 📡 Protocol Commands | 301+ game commands | [View](docs/protocols/COMMANDS.md) |
| 📦 AMF Protocol | AMF3 serialization | [View](docs/protocols/AMF_PROTOCOL.md) |
| 💥 Exploits | Vulnerabilities | [View](docs/exploits/EXPLOITS.md) |
| 🏗️ Architecture | System diagrams | [View](docs/diagrams/ARCHITECTURE.md) |
| 🧪 Offline Hyper-V lab | Safe implementation plan, gates, and evidence requirements | [View](Docs/EVONY_RAG_LAB_PLAN.md) |

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/amazing`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing`)
5. Open Pull Request

---

## 📜 License

MIT License - See [LICENSE](LICENSE) for details.

---

<div align="center">

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║                    Built with 💚 for Reverse Engineering                      ║
║                                                                               ║
║              ⭐ Star this repo if you find it useful! ⭐                      ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

</div>
