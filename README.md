# NeoRAG: A Graph-Based Retrieval‑Augmented Generation System

![NeoRAG Architecture](./docs/architecture.png)

## 🚀 Project Overview

**NeoRAG** leverages the power of **LlamaIndex**, **Neo4j AuraDB**, and **OpenAI's GPT‑4O Mini** to create an enterprise‑grade, **Graph‑RAG (Retrieval‑Augmented Generation)** knowledge engine. By ingesting structured and unstructured data from sources like Wikipedia and the web, NeoRAG builds a rich property graph in AuraDB, enabling:

* **Contextualized Querying** via Cypher and natural language.
* **Dynamic Graph Retrieval** with subgraph extraction optimizations.
* **Accurate LLM Responses** enriched by graph‑based facts and embeddings.
---

## 📦 Key Features

1. **Hybrid Ingestion Pipeline**

   * WikipediaReader for targeted article extraction.
   * SimpleWebPageReader for arbitrary URL scraping.
   * Truncation and metadata preservation for efficient chunking.

2. **Property Graph Construction**

   * `PropertyGraphIndex` auto-generates nodes & relationships in Neo4j.
   * Customizable schema mapping for domain‑specific ontologies.
   * High‑throughput ingestion using `nest_asyncio` compatibility.

3. **Graph-RAG Retriever**

   * `kg_index.as_retriever()` integrates LLM and graph context.
   * Subgraph extraction with verbose Cypher logging for auditability.
   * Embedding‑driven node ranking ensures relevance and precision.

4. **Natural Language → Cypher QA**

   * `KnowledgeGraphQueryEngine` converts NL queries into executable Cypher.
   * Enables analytical queries like: "Which comics company publishes Spider‑Man?"

5. **Interactive Visualization**

   * Neo4j Browser Graph View for immediate feedback.
   * Neo4j Bloom for business‑user exploration with search phrases.
   * Optional Neovis.js integration for embeddable, live dashboards.

6. **Enterprise‑Ready Deployment**

   * Compatibility with Neo4j AuraDB Free & Enterprise tiers.
   * Configurable via environment variables and Google Colab userdata.
   * Lightweight LLM calls with `gpt-4o-mini` and adjustable temperature.

---

## 🛠️ Installation & Setup

1. **Clone the Repository**

   ```bash
   git clone https://github.com/your-org/neorag.git
   cd neorag
   ```

2. **Install Dependencies**

   ```bash
   pip install llama-index neo4j openai \
               llama-index-graph-stores-neo4j \
               llama-index-readers-wikipedia llama-index-readers-web \
               wikipedia nest_asyncio
   ```

3. **Configure Environment Variables**

   ```bash
   export OPENAI_API_KEY="<your_openai_key>"
   export NEO4J_URI="<bolt://your-aura-host:7687>"
   export NEO4J_USER="neo4j"
   export NEO4J_PASSWORD="<your_password>"
   ```



## 🔗 Architecture Diagram

1. **Data Sources** → Wikipedia & Web Readers
2. **Document Chunks** → Metadata enrichment & text chunking
3. **Property Graph Indexer** → Builds nodes/edges via Neo4jPropertyGraphStore
4. **Graph-RAG Retriever** → Subgraph sampling + LLM prompt augmentation
5. **Query Engine** → Synchronous & asynchronous NL queries
6. **Visualization** → Neo4j Browser
<img width="1745" height="1018" alt="visualisation" src="https://github.com/user-attachments/assets/2d1c1df7-2bec-4dda-bd9c-e901a43eb9a1" />

---

## 🎯 Best Practices

* **Schema Design**: Tailor node labels and relationship types to your domain ontology.
* **Chunk Size Tuning**: Balance context window vs. granularity (`Settings.chunk_size`).
* **Verbose Logging**: Enable `verbose=True` for debugging Cypher and subgraph retrieval.
* **Security**: Use managed secrets for API keys and never hardcode credentials.
* **Performance**: Monitor AuraDB metrics (node/relationship count, query latency).


---


