# 👻 PROJECT GHOST // DETERMINISTIC TAINT ANALYSIS ENGINE

**Stop trusting LLMs to guess your vulnerabilities.** 

While the industry drowns in AI wrappers that hallucinate fake security flaws, **Project Ghost** relies on cold, hard math. Ghost is a deterministic Static Application Security Testing (SAST) engine that parses code into Abstract Syntax Trees (AST) and mathematically traces the flow of dirty data from the moment it enters the system to the exact millisecond it hits an explosive sink.

If the data flows from a Source to a Sink without passing through a Sanitizer, Ghost flags it. No guessing. No false positives. No cloud dependency.

## 🩸 THE KILLCHAIN

Ghost doesn't just find bugs; it maps the **exploit path**. 

1. **SOURCE:** Identifies where untrusted data enters (e.g., `request.args.get`, `sys.argv`).
2. **SINK:** Identifies where data executes dangerously (e.g., `os.system`, `eval`, `db.execute`).
3. **TRAVERSE:** Uses NetworkX directed graph traversal to find the shortest path between Source and Sink.
4. **VERIFY:** Checks if a Sanitizer (e.g., `escape()`, `int()`) interrupts the path. If not, the killchain is confirmed.

## 🛠️ THE ARSENAL (Tech Stack)

**The Brain (Backend):**
- `FastAPI`: Blazing fast, async API for file ingestion.
- `Tree-Sitter`: Incremental parsing library to build bulletproof ASTs without regex nightmares.
- `NetworkX`: Graph theory library to trace the taint paths mathematically.

**The Face (Frontend):**
- `Next.js` & `TypeScript`: The command center.
- `ReactFlow`: Interactive, cyberpunk-styled node graph to visualize the exploit chain.
- `Tailwind CSS`: Dark-mode, neon-glow HUD aesthetic.

## 🚀 EXECUTION

### Local Deployment
```bash
# Backend
cd backend
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
uvicorn server:app --reload --port 8000

# Frontend
cd frontend
npm install
npm run dev
