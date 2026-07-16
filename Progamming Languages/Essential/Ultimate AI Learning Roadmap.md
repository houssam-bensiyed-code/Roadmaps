# 🤖 Python AI Engineering Roadmap — Phase 4: AI-Era Engineering
> Aligned with Phase 4 of the Software Engineering Mastery Roadmap
> Python is THE language for AI engineering — this roadmap goes deep.
> **Estimated Duration: 4–6 months**

---

## Prerequisites (Completed in Prior Phases)
> ✅ Python Mastery (OOP, async, concurrency, decorators, type hints, metaprogramming)
> ✅ FastAPI (REST APIs, Pydantic, dependency injection, async SQLAlchemy, WebSockets)
> ✅ Databases (PostgreSQL, Redis, Elasticsearch)
> ✅ Docker, Kubernetes, CI/CD, Observability
> ✅ Testing (pytest, Testcontainers, load testing)
> ✅ Design Patterns, Clean Architecture, DDD

---
---

## 🟤 PHASE 0: Python AI Foundations — The Scientific Stack & ML Essentials
> **Goal:** Build the mathematical intuition and Python tooling foundation that everything in AI engineering stands on. You don't need to become a data scientist — you need to understand what's happening well enough to engineer production systems around it.
> **Duration:** ~3–4 weeks

---

### 📦 Module 0.1: Python Scientific Computing Stack
- Why This Stack Matters for AI Engineering (Not Just Data Science)
- **NumPy — The Foundation Under Everything**
  - Arrays vs Python Lists (Performance, Memory Layout)
  - Array Creation, Indexing, Slicing, Reshaping
  - Broadcasting Rules (How Operations Work Across Different Shapes)
  - Vectorized Operations (Why Loops Are Slow, Vectorization Is Fast)
  - Linear Algebra Basics (`dot`, `matmul`, Matrix Operations)
  - Understanding Shapes and Dimensions (Critical for Working with Embeddings)
  - Random Number Generation (`np.random`)
  - **💡 Embeddings are NumPy arrays. Similarity search is matrix multiplication. You need this.**
- **Pandas — Data Manipulation for AI Pipelines**
  - DataFrames and Series
  - Reading/Writing Data (CSV, JSON, Parquet)
  - Filtering, Grouping, Aggregating
  - Handling Missing Data
  - Merging and Joining DataFrames
  - Apply and Transform Functions
  - **💡 You'll use Pandas for dataset preparation, evaluation results analysis, and metrics aggregation**
- **Matplotlib & Plotly — Visualization for Understanding**
  - Basic Plots (Line, Bar, Scatter, Histogram)
  - Plotly Interactive Charts
  - Visualizing Embeddings (t-SNE, UMAP Plots)
  - Evaluation Metrics Visualization
  - **💡 Visualizing retrieval results, model performance, latency distributions**

### 📦 Module 0.2: Machine Learning Essentials (Engineer's Perspective)
- **Supervised Learning Concepts**
  - Classification (What It Is, Common Algorithms — Awareness)
  - Regression (What It Is, When You'd Use It)
  - Training vs Inference (The Two Completely Different Phases)
  - Training Data, Validation Data, Test Data (Why You Split)
  - Overfitting and Underfitting (Conceptual — Why It Matters for Fine-Tuning)
  - Features and Labels (The Input/Output Mental Model)
- **Unsupervised Learning Concepts**
  - Clustering (K-Means, DBSCAN — What They Do, Not How to Implement)
  - Dimensionality Reduction (PCA, t-SNE, UMAP — For Visualizing Embeddings)
- **Reinforcement Learning (Awareness)**
  - RLHF (Reinforcement Learning from Human Feedback) — How LLMs Are Aligned
  - Reward Models — Conceptual Understanding
- **Key ML Vocabulary You Must Know**
  - Model, Weights, Parameters, Hyperparameters
  - Loss Function, Gradient Descent (Conceptual — The Model Learns by Minimizing Error)
  - Epoch, Batch, Learning Rate
  - Inference Latency vs Throughput
  - GPU vs CPU (Why GPUs Matter for AI)
  - VRAM (Why Model Size Is Limited by GPU Memory)
- **Scikit-Learn — Just Enough**
  - Text Classification with TF-IDF + Logistic Regression (Simple Baseline)
  - Understanding Train/Test Split, Cross-Validation
  - Evaluation Metrics (Accuracy, Precision, Recall, F1 — You'll Use These for RAG)
  - Confusion Matrix
  - **💡 Before reaching for an LLM, can a simple ML model solve your problem?**

### 📦 Module 0.3: Vectors, Embeddings & Similarity
- **What Are Embeddings (The Most Important Concept in Modern AI)**
  - Words as Vectors (Word2Vec, GloVe — Historical Context)
  - Sentences/Paragraphs/Documents as Vectors
  - Images as Vectors, Code as Vectors — Everything Becomes a Vector
  - Embedding Dimensions (384, 768, 1024, 1536 — What the Numbers Mean)
  - Semantic Meaning Captured in Vector Space
    - Similar Meanings → Close Vectors
    - Different Meanings → Distant Vectors
- **Similarity Measures**
  - Cosine Similarity (Direction — Most Common for Text Embeddings)
  - Euclidean Distance (Magnitude)
  - Dot Product (Combines Direction and Magnitude)
  - Manhattan Distance (Awareness)
  - When to Use Which Measure
  - Computing Similarity with NumPy (Hands-On)
- **Generating Embeddings**
  - OpenAI Embedding Models (`text-embedding-3-small`, `text-embedding-3-large`)
  - Open-Source Embedding Models (BGE, E5, Nomic Embed, Jina)
  - Sentence Transformers Library (`sentence-transformers`)
    - Loading Models, Encoding Text, Batch Encoding
    - Model Selection (Speed vs Quality vs Dimensions)
  - MTEB Leaderboard (How to Compare Embedding Models)
- **Vector Operations at Scale**
  - Why Brute-Force Similarity Search Doesn't Scale
  - Approximate Nearest Neighbor (ANN) Search — Conceptual
  - Indexing Strategies (HNSW, IVF, Flat — What They Trade Off)
  - **💡 This is the conceptual foundation for vector databases in Phase 2**

### 📦 Module 0.4: Neural Networks & Transformers (Conceptual)
- **Neural Networks — High-Level Understanding**
  - Neurons, Layers, Activation Functions (Conceptual)
  - Input Layer → Hidden Layers → Output Layer
  - Forward Pass (Input → Prediction)
  - Backpropagation (How the Model Learns — Conceptual)
  - Why Deep Networks Work Better (Feature Hierarchy)
- **Transformers — The Architecture Behind Everything**
  - Attention Mechanism (Conceptual — Not Math-Heavy)
    - "Pay Attention to Relevant Parts of the Input"
    - Self-Attention (Each Token Looks at All Other Tokens)
    - Multi-Head Attention (Multiple Attention Patterns in Parallel)
  - Encoder vs Decoder vs Encoder-Decoder
    - Encoder-Only (BERT — Understanding, Embeddings, Classification)
    - Decoder-Only (GPT, Llama — Generation)
    - Encoder-Decoder (T5, BART — Translation, Summarization)
  - Tokenization
    - What Tokenizers Do (Text → Token IDs)
    - Subword Tokenization (BPE, WordPiece, SentencePiece)
    - Token ≠ Word (Why "strawberry" Has Multiple Tokens)
    - Tokenizer Affects Model Behavior and Cost
  - Context Window
    - What It Means (Maximum Tokens the Model Can See at Once)
    - Context Window Sizes (4K, 8K, 32K, 128K, 1M+)
    - Why Bigger Isn't Always Better (Attention Is Quadratic — Conceptual)
    - Lost-in-the-Middle Problem
  - Positional Encoding (How Models Know Token Order — Awareness)
  - **💡 Understanding transformers explains why RAG works, why context windows matter, and why prompts behave the way they do**

### 📦 Module 0.5: LLM Landscape & Access Patterns
- **Foundation Models Landscape**
  - OpenAI (GPT-4o, GPT-4o-mini, o1, o3)
  - Anthropic (Claude 4 Opus, Sonnet, Haiku)
  - Google (Gemini 2.5 Pro, Flash)
  - Meta (Llama 3, 4)
  - Mistral (Mistral Large, Small, Codestral)
  - Cohere (Command R+)
  - Comparing Capabilities, Speed, Cost, Context Windows
- **Closed-Source vs Open-Source Trade-offs**
  - Closed: Better Performance, Easier Start, Vendor Lock-in, Data Leaves Your Infra
  - Open: Full Control, Privacy, Self-Hosting Cost, Smaller Models
  - Open-Weights vs Truly Open (Licensing: Apache 2.0, Llama License, etc.)
- **Model Size and Capability**
  - Parameters (7B, 13B, 70B, 405B — What the Numbers Mean)
  - When Small Models Win (Latency, Cost, Privacy)
  - Quantization (Reducing Precision: FP16, INT8, INT4 — Smaller + Faster)
- **Multimodal Models**
  - Text + Vision (GPT-4o, Claude, Gemini)
  - Text + Audio (Whisper for STT, Gemini for Multimodal)
  - Text + Code (Codestral, CodeLlama, DeepSeek Coder)
- **Accessing LLMs from Python**
  - Provider SDKs (`openai`, `anthropic`, `google-generativeai`)
  - Chat Completions API Pattern (Messages Array, System/User/Assistant Roles)
  - Streaming Responses (Iterating over Chunks)
  - Temperature, Top-p, Max Tokens (Controlling Output)
  - Structured Output (JSON Mode, Response Format)
  - Function Calling (Tool Use — How Models Call Your Functions)
  - Cost Calculation (Input Tokens + Output Tokens × Price per Token)
- **Running Local Models**
  - Ollama (Simplest Way to Run Local Models)
    - Installing, Pulling Models, Running
    - OpenAI-Compatible API (`/v1/chat/completions`)
  - vLLM (High-Performance Model Serving)
  - llama.cpp / llama-cpp-python (CPU-Friendly Inference)
  - Hugging Face Transformers Library
    - `AutoModel`, `AutoTokenizer`, `pipeline()`
    - Loading Models, Running Inference
    - Model Hub (Downloading Pre-Trained Models)
  - When to Run Local vs Use API

### 📦 Module 0.6: Hugging Face Ecosystem
- Hugging Face Hub
  - Model Cards (Understanding Model Documentation)
  - Model Discovery (Tasks, Tags, Trending)
  - Downloading Models and Tokenizers
- Transformers Library
  - `pipeline()` for Quick Inference (Sentiment, Summarization, Translation, QA)
  - `AutoModel` and `AutoTokenizer` for Custom Workflows
  - Model Types (ForCausalLM, ForSequenceClassification, ForTokenClassification)
  - GPU vs CPU Inference
- Datasets Library
  - Loading Datasets (`load_dataset`)
  - Dataset Operations (Map, Filter, Select)
  - Custom Datasets
  - Streaming Large Datasets
- Tokenizers Library
  - Understanding Tokenizer Output (input_ids, attention_mask)
  - Encoding and Decoding
  - Special Tokens
- Spaces (Gradio, Streamlit — Quick UI for ML Models — Awareness)

> ### 🛠 Phase 0 Milestone Project: **Semantic Search Engine (From Scratch)**
> Build a semantic search engine without any vector database or framework:
> - Load a corpus of documents (Wikipedia articles or custom dataset)
> - Generate embeddings using Sentence Transformers (open-source model)
> - Store embeddings as NumPy arrays (understand the raw representation)
> - Implement brute-force cosine similarity search with NumPy
> - Implement basic HNSW-like approximate search (simplified)
> - Compare search quality: keyword (TF-IDF with scikit-learn) vs semantic (embeddings)
> - Visualize embedding clusters with t-SNE/UMAP using Plotly
> - Benchmark: query latency at different corpus sizes (100, 1K, 10K, 100K documents)
> - Compare OpenAI embeddings vs open-source Sentence Transformer embeddings (quality and cost)
> - Simple CLI interface for querying
>
> **Why:** You'll deeply understand what embeddings are, how similarity search works, why vector databases exist, and the trade-offs between keyword and semantic search — all before touching any framework.

---

### ✅ After Phase 0 — You Understand:
- Python's scientific computing stack and can manipulate arrays/data
- ML concepts enough to have informed conversations and make architecture decisions
- What embeddings are and how similarity search works at a fundamental level
- Transformer architecture conceptually and why it powers modern AI
- The LLM landscape, pricing models, and how to access them from Python
- Hugging Face ecosystem for models, datasets, and tokenizers
- **You have the foundation to build on — now you engineer production AI systems**

---
---

## 🟢 PHASE 1: LLM Foundations & Prompt Engineering
> **Goal:** Master LLM interaction patterns, prompt engineering, and structured output — the building blocks of every AI feature.
> **Duration:** ~3–4 weeks

---

### 📦 Module 1.1: LLM Client Architecture
- **LiteLLM — Unified LLM Interface**
  - Single API for OpenAI, Anthropic, Google, Local Models
  - Provider Abstraction (Switch Models Without Code Changes)
  - Cost Tracking Built-In
  - Fallback Chains (Primary → Secondary → Tertiary Provider)
  - Why Abstraction Matters (Avoid Vendor Lock-In)
- **Direct Provider SDKs (Know What's Underneath)**
  - OpenAI Python SDK (`openai.OpenAI()`, `openai.AsyncOpenAI()`)
  - Anthropic Python SDK (`anthropic.Anthropic()`, `anthropic.AsyncAnthropic()`)
  - Google Generative AI SDK (`google.generativeai`)
  - Async Clients (Critical for FastAPI Integration)
- **Chat Completion Patterns**
  - Message Roles (System, User, Assistant)
  - Multi-Turn Conversations (Message History Management)
  - System Prompt Design (Setting Behavior, Persona, Constraints)
  - Conversation Memory (Appending Messages, Sliding Window, Summarization)
- **Streaming Responses**
  - Why Streaming (Time-to-First-Token, User Experience)
  - Async Generator Pattern for Streaming
  - Server-Sent Events (SSE) with FastAPI
  - WebSocket Streaming
  - Token-by-Token Processing
- **Model Parameters Deep Dive**
  - Temperature (Creativity vs Determinism — 0.0 to 2.0)
  - Top-p (Nucleus Sampling — Alternative to Temperature)
  - Max Tokens (Output Length Control)
  - Stop Sequences (Controlled Termination)
  - Frequency Penalty and Presence Penalty
  - Seed (Reproducible Outputs — When Supported)
  - Choosing Parameters for Different Use Cases

### 📦 Module 1.2: Prompt Engineering
- **Foundational Prompting Techniques**
  - Zero-Shot Prompting (No Examples — Just Instructions)
  - Few-Shot Prompting (Provide Examples to Steer Output)
  - One-Shot Prompting (Single Example — Minimal but Effective)
  - Choosing Number of Examples (Quality vs Context Window Budget)
- **Advanced Prompting Techniques**
  - Chain-of-Thought (CoT) Prompting ("Think step by step")
  - Self-Consistency (Multiple CoT Paths → Majority Vote)
  - Tree of Thought (Branching Reasoning Paths)
  - Step-Back Prompting (Abstract the Problem First, Then Solve)
  - ReAct Prompting (Reasoning + Acting — Foundation for Agents)
  - Prompt Chaining (Break Complex Task into Sequential Prompts)
  - Decomposition (Split One Hard Prompt into Multiple Simpler Ones)
- **System Prompt Design**
  - Persona and Role Definition
  - Behavioral Constraints (What to Do, What NOT to Do)
  - Output Format Specification
  - Tone and Style Guidelines
  - Knowledge Boundaries ("If you don't know, say so")
  - Multi-Section System Prompts (Instructions, Context, Examples, Constraints)
- **Prompt Patterns and Templates**
  - Extraction Pattern (Pull Structured Data from Unstructured Text)
  - Classification Pattern (Categorize Input into Predefined Categories)
  - Transformation Pattern (Rewrite, Translate, Summarize)
  - Generation Pattern (Create Content from Constraints)
  - Analysis Pattern (Evaluate, Compare, Critique)
  - Conversation Pattern (Multi-Turn Dialogue Design)

### 📦 Module 1.3: Structured Output
- **JSON Mode (Provider-Specific)**
  - OpenAI `response_format={"type": "json_object"}`
  - Anthropic JSON Tool Use Pattern
  - Ensuring Valid JSON Output
- **Function Calling / Tool Use**
  - Defining Functions with JSON Schema
  - OpenAI Function Calling (`tools` Parameter)
  - Anthropic Tool Use
  - Google Function Calling
  - Parallel Function Calls
  - Forced Function Calls vs Auto-Detection
- **Pydantic-Based Structured Output**
  - `instructor` Library (Pydantic + LLM = Guaranteed Structured Output)
    - Patching OpenAI/Anthropic Clients
    - Response Models as Pydantic Classes
    - Automatic Retry on Validation Failure
    - Nested Models, Lists, Enums
    - Streaming Partial Models
    - Validators for LLM Output
  - `langchain` Structured Output (`.with_structured_output()`)
  - `marvin` Library (Awareness — Type-Driven AI Functions)
- **Constrained Generation**
  - GBNF Grammars (For Local Models via llama.cpp)
  - Outlines Library (Structured Generation with Open Models)
  - Guidance Library (Awareness)
  - When Constrained Generation vs Prompt + Validation

### 📦 Module 1.4: Prompt Management & Versioning
- Prompts as Software Artifacts (Not Hardcoded Strings)
- Prompt Templates (Jinja2 for Dynamic Prompts)
  - Variable Interpolation
  - Conditional Sections
  - Loop Constructs (For Dynamic Few-Shot Examples)
- Prompt Versioning Strategies
  - File-Based (YAML/JSON Prompt Files with Version Numbers)
  - Database-Backed (Prompt Registry)
  - Git-Based (Prompts in Repository with Change History)
- Prompt Testing (Automated Evaluation Against Expected Outputs)
- Prompt Documentation (What Each Prompt Does, Why Choices Were Made)
- A/B Testing Prompts in Production
- Prompt Libraries and Catalogs (Organization-Level Reuse)

### 📦 Module 1.5: Token Economics & Cost Management
- Understanding Tokenization in Practice
  - `tiktoken` (OpenAI Tokenizer)
  - Token Counting Before API Calls
  - Context Window Budget Planning
- Cost Calculation Patterns
  - Input Tokens × Price + Output Tokens × Price
  - Cost Per Request Estimation
  - Daily/Monthly Cost Projection
- Cost Optimization Strategies
  - Model Routing by Task Complexity (Hard → GPT-4o, Easy → GPT-4o-mini)
  - Prompt Optimization (Shorter Prompts = Less Cost)
  - Caching Identical/Similar Requests
  - Batch API Usage (50% Cheaper, Higher Latency)
  - Open-Source Models for High-Volume Low-Complexity Tasks
- Implementing Cost Tracking in FastAPI
  - Token Usage Logging Per Request
  - Per-User Cost Attribution
  - Budget Alerts and Hard Limits

> ### 🛠 Phase 1 Milestone Project: **Intelligent Document Processor**
> Build a document processing API with FastAPI that:
> - Accepts text documents (paste, upload, URL)
> - Extracts structured information using `instructor` + Pydantic (entities, dates, amounts, categories)
> - Classifies documents by type (invoice, contract, resume, report) using few-shot prompting
> - Summarizes documents at different levels (one-line, paragraph, executive summary) using chain-of-thought
> - Translates documents with tone preservation
> - Streams responses via SSE for long operations
> - Uses LiteLLM for provider abstraction with fallback chains
> - Tracks token usage and cost per request (stored in PostgreSQL)
> - Prompt templates stored as versioned YAML files
> - Model routing (complex extraction → Claude, simple classification → GPT-4o-mini)
> - Comprehensive test suite with mocked LLM responses

---

## 🔵 PHASE 2: Retrieval-Augmented Generation (RAG)
> **Goal:** Build production-grade RAG pipelines that ground LLMs in your data with proper evaluation.
> **Duration:** ~4–6 weeks

---

### 📦 Module 2.1: RAG Architecture & Pipeline Design
- Why RAG Exists (LLMs Hallucinate, Have Knowledge Cutoffs, Don't Know Your Data)
- End-to-End RAG Pipeline
  - Ingest → Chunk → Embed → Store → Retrieve → Augment → Generate
- RAG vs Fine-Tuning vs Prompt Engineering — Decision Framework
  - RAG: Dynamic Knowledge, Frequent Updates, Source Attribution
  - Fine-Tuning: Style/Format Changes, Domain Vocabulary, Consistent Behavior
  - Prompt Engineering: Simple Tasks, Small Context, No External Knowledge
  - Combining Approaches (Fine-Tuned Model + RAG)
- RAG Architecture Patterns
  - Naive RAG (Simple Retrieve → Stuff into Prompt → Generate)
  - Advanced RAG (Query Transform → Multi-Step Retrieval → Re-Rank → Generate)
  - Modular RAG (Composable Pipeline Components)
- RAG Pipeline as FastAPI Service (API Design for RAG)

### 📦 Module 2.2: Document Loading & Preprocessing
- Document Loading Strategies
  - PDF Parsing (`PyMuPDF`/`fitz`, `pdfplumber`, `unstructured`)
    - Text Extraction, Table Extraction, Image Extraction
    - OCR for Scanned PDFs (`pytesseract`, `EasyOCR`)
  - Web Pages (`BeautifulSoup`, `trafilatura` for Clean Text Extraction)
  - Markdown and Text Files
  - Office Documents (DOCX, PPTX, XLSX via `python-docx`, `openpyxl`)
  - Structured Data (CSV, JSON → Text Representation)
  - Code Repositories (File Traversal, Language-Aware Splitting)
  - APIs (Confluence, Notion, Google Drive, Slack)
- `unstructured` Library (Multi-Format Document Processing Pipeline)
  - Partitioning Strategies
  - Element Types (Title, NarrativeText, Table, ListItem)
  - Cleaning and Normalization
- Document Metadata Extraction
  - Source, Page Number, Section Title, Last Modified
  - Custom Metadata (Tags, Categories, Access Control)
  - Metadata as Retrieval Filter

### 📦 Module 2.3: Chunking Strategies
- Why Chunking Matters (Context Window Limits, Retrieval Precision)
- Chunking Methods
  - Fixed-Size Chunking (Character Count, Token Count)
    - Overlap (Why and How Much — Typically 10-20%)
  - Recursive Character Splitting (LangChain's Default)
    - Split by Paragraphs → Sentences → Words → Characters
  - Semantic Chunking
    - Embedding-Based Boundary Detection
    - Split When Semantic Similarity Drops Between Sentences
  - Document Structure-Aware Chunking
    - Markdown Header Splitting (Preserve Document Hierarchy)
    - HTML Section Splitting
    - Code-Aware Splitting (By Function, Class, Module)
  - Agentic Chunking (LLM Decides Chunk Boundaries — Expensive)
- Parent-Child Chunking (Small Chunks for Retrieval, Large Chunks for Context)
  - Store Small Chunks with Embeddings
  - Link to Parent Document or Larger Chunk
  - Retrieve Small, Return Large
- Chunk Size and Overlap Tuning
  - Smaller Chunks → More Precise Retrieval, Less Context
  - Larger Chunks → More Context, Less Precise Retrieval
  - Empirical Testing (No Universal Best Size)
  - Typical Ranges (256–1024 Tokens, 50–200 Token Overlap)

### 📦 Module 2.4: Embedding Models — Selection & Optimization
- Embedding Model Categories
  - Closed-Source (OpenAI `text-embedding-3-small/large`, Cohere `embed-v4`, Google `text-embedding-004`)
  - Open-Source (BGE, E5, Nomic Embed, Jina Embeddings, GTE)
  - Code-Specialized (CodeBERT, StarEncoder)
  - Multilingual Models
- Selection Criteria
  - Quality (MTEB Leaderboard Benchmarks)
  - Dimensions (Trade-off: Quality vs Storage vs Speed)
  - Context Window (Most: 512 Tokens, Some: 8K+)
  - Speed (Latency per Embedding)
  - Cost (API Pricing or Self-Hosting Cost)
  - Matryoshka Embeddings (Variable Dimensions from One Model)
- Embedding Generation Pipeline
  - Batch Embedding (Process Many Documents Efficiently)
  - Async Embedding (Parallel API Calls)
  - Caching Embeddings (Don't Re-Embed Unchanged Documents)
  - Embedding Versioning (What Happens When You Change Models)
- Instruction-Tuned Embeddings (Separate Instructions for Queries vs Documents)

### 📦 Module 2.5: Vector Databases & Search
- **Vector Database Options**
  - pgvector (PostgreSQL Extension — Great When You Already Use PostgreSQL)
    - `vector` Column Type, HNSW Index, IVFFlat Index
    - Async Access with SQLAlchemy + asyncpg
    - Filtering + Vector Search Together
  - Qdrant (Purpose-Built, Rich Filtering, Python SDK)
    - Collections, Points, Payloads
    - Named Vectors (Multiple Embeddings per Document)
    - Filtering with Conditions
  - Chroma (Simple, Embedded, Good for Prototyping)
  - Weaviate (GraphQL Interface, Multi-Tenancy)
  - Pinecone (Fully Managed, Serverless — Awareness)
  - Milvus (Scalable, Open-Source — Awareness)
- **Indexing Algorithms (Understanding Trade-offs)**
  - Flat (Exact, Slow, 100% Recall)
  - IVF (Inverted File — Partition + Search Subset)
  - HNSW (Hierarchical Navigable Small World — Best Quality/Speed)
  - Index Parameters Tuning (ef_construction, M for HNSW)
- **Hybrid Search (Vector + Keyword)**
  - Why Hybrid (Vector Misses Exact Matches, Keyword Misses Semantic)
  - BM25 for Keyword Search
  - Reciprocal Rank Fusion (RRF) — Combining Vector and Keyword Results
  - pgvector + `tsvector` (Full-Text Search + Vector Search in PostgreSQL)
  - Qdrant Hybrid Search (Sparse + Dense Vectors)
- **Metadata Filtering**
  - Pre-Filtering (Filter Before Vector Search — Faster but Smaller Search Space)
  - Post-Filtering (Search First, Then Filter — More Results but Wasteful)
  - Structured Metadata Design (Tags, Categories, Dates, Access Control)
- **Re-Ranking**
  - Why Re-Rank (Embedding Similarity ≠ Answer Relevance)
  - Cross-Encoder Re-Rankers (More Accurate but Slower)
    - `sentence-transformers` Cross-Encoders
    - Cohere Rerank API
    - BGE Reranker
    - Jina Reranker
  - ColBERT (Late Interaction — Awareness)
  - Two-Stage Pipeline: Fast Retrieval (Top 50) → Re-Rank (Top 10) → LLM (Top 5)

### 📦 Module 2.6: Advanced RAG Techniques
- **Query Transformation**
  - Query Rewriting (LLM Rewrites User Query for Better Retrieval)
  - HyDE (Hypothetical Document Embeddings — Generate Answer, Embed That, Search)
  - Query Decomposition (Break Complex Query into Sub-Queries)
  - Step-Back Prompting (Abstract the Query to a Higher-Level Concept)
- **Multi-Query RAG**
  - Generate Multiple Query Variations
  - Retrieve for Each Variation
  - Merge and Deduplicate Results
- **Multi-Index RAG**
  - Different Indexes for Different Data Types (Docs, Code, FAQs)
  - Query Routing (LLM or Classifier Decides Which Index to Search)
  - Merging Results Across Indexes
- **Contextual Retrieval**
  - Contextual Chunking (Add Document-Level Context to Each Chunk Before Embedding)
  - Contextual Embeddings (Prepend Context to Chunk Before Embedding)
- **Graph RAG**
  - Knowledge Graphs + Vector Search (Microsoft's GraphRAG Approach)
  - Entity Extraction → Relationship Extraction → Graph Construction
  - Community Detection and Summarization
  - Graph-Based Retrieval (Traverse Relationships)
  - When Graph RAG Adds Value (Complex Multi-Hop Questions)
  - `neo4j` + Vector Search (Awareness)
- **Agentic RAG**
  - Retriever as a Tool the Agent Decides to Use
  - Agent Decides: Search, Search Again with Different Query, or Answer
  - Self-Reflective RAG (Check Retrieved Context Relevance Before Generating)
  - Iterative Retrieval (Retrieve → Generate Partial → Retrieve More → Complete)

### 📦 Module 2.7: RAG Evaluation
- **Retrieval Evaluation Metrics**
  - Recall@K (Did We Retrieve the Relevant Documents?)
  - Precision@K (Are the Retrieved Documents Relevant?)
  - MRR — Mean Reciprocal Rank (How High Is the First Relevant Result?)
  - NDCG — Normalized Discounted Cumulative Gain
  - Hit Rate (At Least One Relevant Document Retrieved?)
- **Generation Evaluation Metrics**
  - Faithfulness (Is the Answer Grounded in the Retrieved Context?)
  - Answer Relevance (Does the Answer Actually Address the Question?)
  - Context Relevance (Are the Retrieved Contexts Useful for the Question?)
  - Hallucination Rate (Does the Answer Contain Information Not in Context?)
- **Evaluation Frameworks**
  - RAGAS (`ragas` Library — RAG Assessment)
    - Faithfulness, Answer Relevance, Context Precision, Context Recall
    - Automated Evaluation with LLM-as-Judge
  - DeepEval (`deepeval` Library)
    - RAG Metrics, Conversational Metrics
    - Custom Metrics
  - Building Custom Evaluation Pipelines
- **Evaluation Dataset Creation**
  - Manual Golden Dataset (Question → Expected Answer → Source Documents)
  - Synthetic Dataset Generation (LLM Generates Q&A Pairs from Your Corpus)
  - Continuous Evaluation (Production Query Sampling)
- **Debugging RAG Failures**
  - Retrieval Failures (Relevant Document Not Retrieved — Embedding/Chunking Problem)
  - Generation Failures (Relevant Document Retrieved But Answer Wrong — Prompt/Model Problem)
  - Systematic Debugging Workflow

> ### 🛠 Phase 2 Milestone Project: **Enterprise Knowledge Base RAG System**
> Build a production RAG system with FastAPI that:
> - Ingests multiple document formats (PDF, Markdown, Web pages, Confluence API) using `unstructured`
> - Implements three chunking strategies (recursive, semantic, parent-child) with configurable parameters
> - Generates embeddings with both OpenAI and open-source models (switchable)
> - Stores in pgvector with metadata filtering and full-text search
> - Hybrid search (vector + BM25) with re-ranking (Cohere or cross-encoder)
> - Advanced RAG: query rewriting, HyDE, multi-query retrieval
> - Streaming chat responses via SSE with source citations
> - Evaluation pipeline with RAGAS (automated in CI/CD)
> - Golden evaluation dataset (50+ question-answer pairs with source documents)
> - Admin API for document management (upload, delete, re-index)
> - Usage tracking (queries, latency, retrieval quality per query)
> - Redis caching for frequent queries
> - Dockerized with docker-compose (FastAPI + PostgreSQL/pgvector + Redis)

---

## 🟡 PHASE 3: AI Agents
> **Goal:** Design, build, and orchestrate AI agents that reason, plan, and take action using tools.
> **Duration:** ~4–6 weeks

---

### 📦 Module 3.1: Agent Fundamentals
- **What is an Agent (Beyond a Chatbot)**
  - Perception → Reasoning → Action Loop
  - Agents Decide What to Do Next (Not Just Respond)
  - The Agent Has a Goal and a Set of Tools
  - Agent = LLM + Tools + Memory + Orchestration Logic
- **ReAct Pattern (Reasoning + Acting)**
  - Thought → Action → Observation → Thought → ... → Final Answer
  - LLM Reasons About What Tool to Use
  - LLM Observes Tool Output and Decides Next Step
  - When to Stop (Convergence, Max Iterations)
- **Tool Use — Teaching LLMs to Call Functions**
  - Function Calling (OpenAI, Anthropic, Google Patterns)
  - Tool Definition (Name, Description, Parameters JSON Schema)
  - Tool Execution (Agent Requests Tool Call → You Execute → Return Result)
  - Tool Selection by LLM (How Models Decide Which Tool to Use)
  - Error Handling (Tool Fails → Agent Should Retry or Try Alternative)
- **Planning — Task Decomposition**
  - Plan-and-Execute Pattern (Plan Steps First, Then Execute Each)
  - Iterative Planning (Replan After Each Step Based on Results)
  - Planning With and Without Tools
  - Planning Limitations (LLMs Are Bad at Complex Multi-Step Plans)
- **Memory Types**
  - Short-Term Memory (Current Conversation / Working Memory)
  - Long-Term Memory (Persistent Storage — Vector DB, Database)
  - Episodic Memory (Past Interactions and Their Outcomes)
  - Semantic Memory (Facts and Knowledge)
  - Memory Retrieval (When and How to Pull Relevant Memories)

### 📦 Module 3.2: LangChain & LangGraph
- **LangChain Core Concepts**
  - Chat Models (LLM Abstraction)
  - Prompt Templates (`ChatPromptTemplate`, `MessagesPlaceholder`)
  - Output Parsers (String, JSON, Pydantic)
  - Chains (Sequential LLM Calls)
    - LCEL (LangChain Expression Language) — Pipe Operator
    - RunnablePassthrough, RunnableLambda, RunnableParallel
  - Tools and Tool Calling
    - `@tool` Decorator
    - `StructuredTool`
    - Binding Tools to Models (`.bind_tools()`)
  - Retrievers (RAG Integration)
  - Document Loaders and Text Splitters (Already Covered — Use LangChain's)
- **LangGraph — Stateful Agent Orchestration**
  - Why LangGraph Over LangChain Agents (Explicit Control Flow, State Management)
  - State Graphs
    - `StateGraph` (Define Agent as a Graph of Nodes and Edges)
    - State Schema (TypedDict or Pydantic — What Data Flows Between Nodes)
  - Nodes (Functions That Process State)
    - LLM Nodes (Call Model, Parse Output)
    - Tool Nodes (Execute Tools)
    - Custom Logic Nodes (Validation, Transformation)
  - Edges (Control Flow Between Nodes)
    - Normal Edges (Always Go Here)
    - Conditional Edges (Route Based on State — If/Else Branching)
  - Built-in Nodes
    - `ToolNode` (Automatic Tool Execution)
  - Compilation and Execution (`graph.compile()`, `graph.invoke()`)
  - Streaming (Node-by-Node, Token-by-Token)
  - Persistence and Checkpointing
    - `MemorySaver` (In-Memory — Development)
    - `AsyncPostgresSaver` / `AsyncSqliteSaver` (Persistent — Production)
    - Resume from Checkpoint (Long-Running Agents)
    - Thread-Based Conversations
  - Human-in-the-Loop
    - Interrupt Before/After Nodes
    - Approval Gates (Agent Pauses, Human Approves, Agent Continues)
    - Human Input Nodes
  - Subgraphs (Composing Graphs Within Graphs)

### 📦 Module 3.3: Building Custom Tools
- **API Wrapper Tools**
  - Wrapping REST APIs as Agent Tools
  - HTTP Client Tools (`httpx` Based)
  - API Authentication in Tools (API Keys, OAuth Tokens)
  - Rate Limiting in Tools
  - Error Handling and Retry in Tools
- **Database Query Tools**
  - SQL Query Tools (Text-to-SQL with LLM)
    - Schema Awareness (Pass Table Schemas to LLM)
    - Query Validation (Don't Execute Destructive Queries)
    - Read-Only Database Connections for Safety
  - Vector Search Tools (RAG as a Tool)
  - Redis Lookup Tools
- **File Operation Tools**
  - File Reading, Writing, Listing
  - CSV/JSON/PDF Processing Tools
  - Sandboxed File Access (Don't Let Agents Access Your Whole File System)
- **Code Execution Tools**
  - Code Execution Sandboxes
    - E2B (Cloud Sandbox — Preferred for Production)
    - Docker-Based Sandbox (Self-Hosted)
    - `subprocess` with Restrictions (Dangerous — Use Carefully)
  - Python REPL Tool (Agent Writes and Executes Python)
  - Output Capture and Error Handling
- **Browser Automation Tools**
  - Playwright as Agent Tool (Navigate, Click, Extract, Screenshot)
  - Web Scraping Tools
  - Form Filling and Data Entry
- **Domain-Specific Tools**
  - Calculator and Math Tools
  - Date/Time Tools
  - Search Engine Tools (Tavily, SerpAPI, Brave Search API)
  - Email Sending Tools
  - Slack/Discord Integration Tools

### 📦 Module 3.4: MCP (Model Context Protocol)
- What is MCP (Anthropic's Protocol for Connecting Agents to External Services)
- MCP Architecture (Client, Server, Transport)
- MCP Server Types
  - Resource Servers (Provide Data — Files, Database Records)
  - Tool Servers (Provide Actions — API Calls, Computations)
  - Prompt Servers (Provide Prompt Templates)
- Building MCP Servers in Python (`mcp` SDK)
  - Defining Resources
  - Defining Tools
  - Server Configuration
- Using MCP Clients in Your Agents
- Existing MCP Servers (GitHub, Slack, Google Drive, PostgreSQL, etc.)
- MCP vs Direct Tool Integration (When MCP Adds Value)

### 📦 Module 3.5: Multi-Agent Systems
- **Why Multi-Agent (Single Agent Limitations)**
  - Context Window Overwhelm
  - Tool Overload (Too Many Tools Confuse the LLM)
  - Specialization (Different Models for Different Tasks)
- **Agent Roles and Specialization**
  - Researcher Agent (Searches and Gathers Information)
  - Analyst Agent (Synthesizes, Compares, Evaluates)
  - Writer Agent (Produces Structured Output)
  - Reviewer Agent (Critiques and Suggests Improvements)
  - Coder Agent (Writes and Tests Code)
  - Orchestrator/Supervisor Agent (Delegates and Coordinates)
- **Multi-Agent Topologies**
  - Supervisor Pattern (One Agent Delegates to Others)
  - Sequential/Pipeline (Agent A → Agent B → Agent C)
  - Hierarchical (Supervisor → Sub-Supervisors → Workers)
  - Peer-to-Peer / Debate (Agents Discuss and Converge)
  - Swarm Pattern (Dynamic Agent Selection)
- **Implementation with LangGraph**
  - Multi-Agent as Subgraphs
  - Shared State Between Agents
  - Agent Handoff (Transfer Conversation/Context to Another Agent)
  - Supervisor Node (Routes to Appropriate Agent)
- **Other Multi-Agent Frameworks (Awareness)**
  - CrewAI (Role-Based Agent Teams)
  - AutoGen (Microsoft — Conversational Agent Framework)
  - OpenAI Agents SDK (Swarm-Like)
  - Choosing Between Frameworks
- **Agent Communication**
  - Context Passing Between Agents (What to Share, What to Summarize)
  - Shared Memory/Scratchpad
  - Message Protocols Between Agents
  - Avoiding Context Explosion (Summarization Between Handoffs)

### 📦 Module 3.6: Agent Reliability & Observability
- **Agent Failure Modes**
  - Infinite Loops (Agent Never Converges)
  - Tool Misuse (Wrong Tool, Wrong Parameters)
  - Hallucinated Tool Calls (Tool Doesn't Exist)
  - Context Window Exhaustion (Conversation Too Long)
  - Cost Explosion (Too Many LLM Calls)
- **Reliability Guardrails**
  - Max Iteration Caps (Hard Stop After N Steps)
  - Max Token Budget (Stop When Cost Exceeds Threshold)
  - Timeout Limits (Wall-Clock Time Limits)
  - Tool Call Validation (Verify Parameters Before Execution)
  - Human Approval for High-Risk Actions
  - Fallback Behavior (What to Do When Agent Fails)
- **Agent Observability**
  - LangSmith (LangChain's Observability Platform)
    - Trace Visualization (Every LLM Call, Tool Call, Decision)
    - Run Evaluation
    - Prompt Playground
    - Feedback Collection
  - Arize Phoenix (Open-Source Alternative)
  - Langfuse (Open-Source Tracing)
  - Custom Tracing with OpenTelemetry
  - Logging Agent Decisions (Thought, Action, Observation Chain)
  - Cost Tracking Per Agent Run

> ### 🛠 Phase 3 Milestone Project: **AI Research Assistant (Multi-Agent)**
> Build a multi-agent research assistant with FastAPI and LangGraph:
> - **Orchestrator Agent** (Supervisor — Routes Queries to Appropriate Agent)
> - **Research Agent** (Searches web via Tavily, queries internal knowledge base via RAG)
> - **Analyst Agent** (Synthesizes findings, compares sources, identifies contradictions)
> - **Writer Agent** (Produces structured reports in Markdown with citations)
> - **Fact-Checker Agent** (Verifies key claims against retrieved sources)
> - LangGraph state graph with conditional routing and human-in-the-loop approval
> - Persistent checkpointing with AsyncPostgresSaver (resume interrupted research)
> - Custom tools: web search, RAG retrieval, calculator, code executor (E2B sandbox)
> - MCP server for internal document access
> - Streaming progress updates via WebSocket (which agent is working, current status)
> - Full tracing with Langfuse (every LLM call, tool call, agent handoff)
> - Cost tracking and budget limits per research session
> - Max iteration caps and timeout guardrails
> - FastAPI endpoints: start research, check status, get results, provide feedback

---

## 🟠 PHASE 4: Production AI Systems
> **Goal:** Build AI features that are reliable, evaluated, safe, and cost-effective in production.
> **Duration:** ~4–6 weeks

---

### 📦 Module 4.1: LLM Application Architecture
- **LLM Gateway Pattern**
  - Abstraction Layer Over Multiple Providers
  - LiteLLM as Gateway (Proxy Mode — Centralized LLM Access for Your Org)
  - Custom Gateway with FastAPI
    - Unified Request/Response Format
    - Provider Routing Logic
    - Authentication and Rate Limiting
    - Request/Response Logging
- **Fallback Chains**
  - Primary Model → Fallback Model → Graceful Degradation
  - Fallback Triggers (Timeout, Rate Limit, Error, Cost Threshold)
  - Model-Specific Error Handling
  - Health Checks on LLM Providers
- **Streaming Architecture**
  - SSE (Server-Sent Events) for Chat Interfaces
  - WebSocket for Bidirectional Agent Communication
  - Streaming with FastAPI (`StreamingResponse`)
  - Token Buffering (Don't Send Every Single Token — Batch for Efficiency)
  - Error Handling in Streams (What Happens When Stream Fails Mid-Response)
- **Semantic Caching**
  - Exact Match Caching (Same Query → Same Response)
  - Semantic Similarity Caching (Similar Query → Cached Response)
    - Embed Query → Search Cache → If Similar Enough → Return Cached
    - Cache Hit Threshold Tuning
  - Cache Invalidation (TTL, Source Document Changes)
  - Redis + pgvector for Semantic Cache
  - GPTCache Library (Awareness)
- **Latency Optimization**
  - Streaming (Time-to-First-Token Reduction)
  - Smaller Models for Simple Tasks
  - Prompt Optimization (Shorter Prompts = Faster)
  - Batch Processing (Parallel Requests for Non-Interactive Tasks)
  - Pre-Computation (Generate and Cache Responses for Predictable Queries)
  - Connection Pooling for LLM API Clients

### 📦 Module 4.2: Evaluation & Testing
- **Evaluation Frameworks**
  - DeepEval
    - Metrics: Faithfulness, Relevance, Hallucination, Toxicity, Bias
    - Custom Metrics
    - Test Cases as Python Tests (`pytest` Integration)
    - CI/CD Integration (Evaluation as Pipeline Gate)
  - RAGAS (RAG-Specific Evaluation — Covered in Phase 2, Applied Here)
  - promptfoo (Prompt Evaluation — YAML-Based Test Suites)
    - Assertions (Contains, JSON Schema, Similarity, Custom)
    - Matrix Testing (Multiple Prompts × Multiple Models × Multiple Inputs)
    - Regression Detection
  - Building Custom Evaluation Pipelines
- **LLM-as-Judge**
  - Using One LLM to Evaluate Another's Output
  - Judge Prompt Design (Rubric-Based, Pairwise Comparison)
  - Calibration (Does the Judge Agree with Human Evaluators?)
  - Judge Model Selection (Stronger Model Judges Weaker Model)
  - Multi-Judge Consensus (Multiple Judge Prompts, Majority Vote)
  - Limitations of LLM-as-Judge (Bias Toward Verbose Answers, Position Bias)
- **Regression Testing for AI Features**
  - Golden Dataset of Input/Expected Output Pairs
  - Automated Regression Suite in CI/CD
  - Threshold-Based Pass/Fail (e.g., Faithfulness > 0.85)
  - Alerting on Quality Degradation
  - Version Comparison (New Prompt vs Old Prompt)
- **A/B Testing AI Features**
  - Feature Flags for AI Variants
  - Metrics Collection (Quality, Latency, User Satisfaction)
  - Statistical Significance
  - Gradual Rollout

### 📦 Module 4.3: Safety & Guardrails
- **Input Guardrails**
  - Prompt Injection Detection
    - What is Prompt Injection (User Manipulates System Prompt)
    - Detection Strategies (Classifier, Heuristic, LLM-Based)
    - Input Sanitization
  - Content Filtering (Block Toxic, Harmful, Off-Topic Inputs)
  - PII Detection in Inputs (Detect Before Sending to External LLM)
    - `presidio` Library (Microsoft — PII Detection and Anonymization)
    - Regex-Based Detection (Email, Phone, SSN)
  - Topic Restriction (Only Answer Questions About Your Domain)
  - Input Length Limits
- **Output Guardrails**
  - PII Detection in Outputs (Don't Return Sensitive Data)
  - Toxicity Filtering
  - Fact-Checking Against Retrieved Sources (Hallucination Guard)
  - Output Format Validation (Pydantic for Structured, Regex for Unstructured)
  - Banned Phrases and Topics
  - Competitor Mention Filtering
- **Guardrail Frameworks**
  - Guardrails AI (`guardrails-ai`)
    - Guard Object (Input Validators → LLM → Output Validators)
    - Built-in Validators
    - Custom Validators
    - Retry on Failure
  - NeMo Guardrails (NVIDIA)
    - Colang Language (Dialog Rails, Topical Rails, Safety Rails)
    - Programmable Guardrails
  - Building Custom Guardrails (When Frameworks Are Too Heavy)
    - Guardrail as FastAPI Middleware
    - Guardrail as LangGraph Node (Before/After LLM)
- **OWASP Top 10 for LLM Applications**
  - Prompt Injection (Direct and Indirect)
  - Insecure Output Handling
  - Training Data Poisoning (Awareness)
  - Model Denial of Service
  - Supply Chain Vulnerabilities (Malicious Models, Plugins)
  - Sensitive Information Disclosure
  - Insecure Plugin Design
  - Excessive Agency (Agent Does More Than It Should)
  - Overreliance
  - Model Theft (Awareness)
- **Indirect Prompt Injection**
  - Data Poisoning the Context (Malicious Content in Retrieved Documents)
  - Mitigation Strategies (Input Sanitization on Retrieved Content, Delimiter Tokens)
- **Red Teaming and Adversarial Testing**
  - Manual Adversarial Testing (Try to Break Your System)
  - Automated Red Teaming (Generate Adversarial Inputs)
  - Jailbreak Detection and Prevention
  - Reporting and Fixing Vulnerabilities
- **AI Ethics and Regulation Awareness**
  - EU AI Act (Risk Categories, Compliance Requirements)
  - Responsible AI Principles (Fairness, Transparency, Accountability)
  - Bias Detection and Mitigation
  - Model Cards and System Cards

### 📦 Module 4.4: Feedback Loops & Continuous Improvement
- **User Feedback Collection**
  - Thumbs Up/Down (Simplest Signal)
  - Star Ratings
  - Free-Text Feedback
  - Implicit Feedback (Regenerate, Copy, Edit Response)
  - Feedback API Design in FastAPI
  - Feedback Storage (PostgreSQL)
- **Feedback Analysis**
  - Classifying Feedback by Failure Mode (Wrong, Incomplete, Off-Topic, Hallucination)
  - LLM-Based Feedback Analysis (Categorize Free-Text Feedback)
  - Quality Trend Monitoring (Is Quality Improving or Degrading Over Time?)
  - Identifying Systematic Failures (Clusters of Similar Bad Queries)
- **Closing the Loop**
  - Feedback → Prompt Improvement
  - Feedback → RAG Pipeline Tuning (Better Chunking, More Sources)
  - Feedback → Few-Shot Example Selection (Use Good Responses as Examples)
  - Feedback → Fine-Tuning Dataset (Curate Best Q&A Pairs)
  - Feedback → Guardrail Updates (New Rules Based on Observed Failures)

### 📦 Module 4.5: MLOps for LLM Applications
- **Experiment Tracking**
  - MLflow (Experiment Tracking, Model Registry)
    - Logging Parameters, Metrics, Artifacts
    - Comparing Experiments (Prompt A vs Prompt B vs Prompt C)
    - Model Versioning
  - Weights and Biases (Awareness)
  - Custom Tracking with PostgreSQL (Lightweight Alternative)
- **CI/CD for AI Features**
  - Evaluation as Pipeline Gate (Quality Metrics Must Pass Before Deploy)
  - Prompt Regression Tests in CI
  - Model Performance Benchmarks in CI
  - Automated Quality Reports
  - Deployment Strategy (Blue/Green for AI Features)
- **Production Monitoring**
  - Quality Degradation Detection
    - Automated Evaluation on Sampled Production Queries
    - Quality Score Trending (Prometheus Metrics + Grafana)
  - Drift Detection
    - Input Distribution Drift (Users Asking Different Types of Questions)
    - Output Quality Drift (Model Quality Changing Over Time — Provider Updates)
  - Latency Monitoring (Per Endpoint, Per Model, Per Operation)
  - Cost Monitoring (Per Day, Per User, Per Feature)
  - Error Rate Monitoring (LLM Errors, Tool Errors, Guardrail Triggers)
- **Fine-Tuning When Needed**
  - When to Fine-Tune (Decision Framework)
    - Consistent Style/Format Needed
    - Domain-Specific Vocabulary
    - Cost Reduction (Smaller Fine-Tuned Model Replaces Larger General Model)
  - LoRA and QLoRA (Efficient Fine-Tuning — Conceptual)
    - Low-Rank Adaptation (Freeze Base, Train Small Adapters)
    - QLoRA (Quantized Base + LoRA — Fits on Consumer GPUs)
  - Dataset Preparation for Fine-Tuning
    - JSONL Format (Messages Array)
    - Data Quality Over Quantity (100 Great Examples > 10,000 Mediocre)
    - Data Augmentation
  - Fine-Tuning Services
    - OpenAI Fine-Tuning API
    - Together AI, Fireworks AI
    - Hugging Face + PEFT/TRL (Self-Hosted)
  - Evaluation After Fine-Tuning (Compare Base vs Fine-Tuned)
- **Model Serving (Self-Hosted)**
  - vLLM (High-Performance Serving)
    - PagedAttention (Efficient Memory Management)
    - Continuous Batching
    - Tensor Parallelism
    - OpenAI-Compatible API
  - Text Generation Inference — TGI (Hugging Face)
  - Ollama (Simple Local Serving)
  - Cloud-Managed Endpoints (AWS Bedrock, Google Vertex AI, Azure OpenAI)
  - Choosing Between Self-Hosted and Managed

> ### 🛠 Phase 4 Milestone Project: **Production AI Platform Infrastructure**
> Build the production infrastructure layer for AI features:
> - **LLM Gateway** (FastAPI service with LiteLLM) — unified API for all LLM access, provider fallback, cost tracking per user/team, rate limiting, request/response logging
> - **Semantic Cache** (Redis + pgvector) — cache hit rate monitoring, TTL management, cache invalidation API
> - **Guardrail Service** (FastAPI middleware layer) — prompt injection detection (classifier-based), PII detection with `presidio`, output validation, content filtering, topic restriction
> - **Evaluation Pipeline** (CI/CD integrated) — DeepEval test suite with 100+ test cases, RAGAS evaluation for RAG quality, promptfoo regression tests, automated quality reports as CI artifacts
> - **Feedback System** — feedback API (thumbs up/down + free text), feedback storage in PostgreSQL, LLM-based feedback categorization, weekly quality reports
> - **Monitoring Dashboard** — Grafana dashboards for quality scores, latency P50/P95/P99, cost per day/user, error rates, guardrail trigger rates, cache hit rates
> - **Experiment Tracker** — MLflow for prompt experiments, A/B test results
> - All services Dockerized, deployed to Kubernetes, traced with OpenTelemetry

---

## 🔴 PHASE 5: AI-Augmented Engineering
> **Goal:** Integrate AI into your own development workflow and build AI-powered developer tools.
> **Duration:** ~2–3 weeks

---

### 📦 Module 5.1: AI-Assisted Development
- **AI Coding Assistants**
  - GitHub Copilot (Inline Completion, Chat, Edits)
  - Cursor (AI-First Editor — Chat, Composer, Multi-File Edits)
  - Cline (VS Code Extension — Agentic Coding)
  - Windsurf (Codeium — Awareness)
  - Claude Code (Terminal-Based Agentic Coding)
  - Choosing Your Primary AI Coding Tool
- **Effective Prompting for Code Generation**
  - Context Matters (Open Relevant Files, Reference Types, Show Examples)
  - Iterative Refinement (Start Broad, Narrow Down)
  - Specifying Constraints (Language, Framework, Style, Error Handling)
  - Prompt Patterns for Code
    - "Implement X that follows Y pattern using Z library"
    - "Refactor this to follow [principle]"
    - "Write tests for this that cover [edge cases]"
    - "Explain this code, then suggest improvements"
- **AI for Code Review**
  - AI-Assisted Pull Request Reviews
  - Detecting Code Smells and Anti-Patterns
  - Security Vulnerability Detection
  - Performance Suggestion
  - Limitations (AI Misses Business Logic Errors, Context Gaps)
- **AI for Debugging**
  - Describing Errors to AI (Stack Trace + Context)
  - Rubber Duck Debugging with AI
  - Root Cause Analysis Assistance
  - Fixing Flaky Tests with AI Assistance
- **AI for Test Generation**
  - Generating Unit Tests from Implementation
  - Generating Edge Cases You Didn't Think Of
  - Property-Based Test Case Discovery
  - Test Coverage Gap Identification
- **Understanding Limitations**
  - AI-Generated Code Often Has Subtle Bugs
  - AI Doesn't Understand Your Architecture Decisions
  - AI May Suggest Deprecated or Insecure Patterns
  - Always Review and Test AI-Generated Code
  - Maintaining Code Quality Standards with AI Assistance

### 📦 Module 5.2: AI in the Software Lifecycle
- **AI-Powered Documentation Generation**
  - Generating Docstrings from Code
  - Generating README Files
  - Generating API Documentation Descriptions
  - Architecture Documentation Assistance
  - Documentation Freshness (Regenerate When Code Changes)
- **AI-Enhanced Codebase Search**
  - Semantic Code Search (Embed Code + Natural Language Queries)
  - Building an Internal Code Knowledge Base with RAG
  - "How does feature X work in our codebase?"
  - "Find all places where we handle authentication"
- **AI in CI/CD**
  - Automated PR Descriptions
  - Changelog Generation from Git History
  - Intelligent Test Selection (Run Tests Most Likely to Fail)
  - Deployment Risk Scoring (Analyze Diff for Risky Changes)
  - AI-Generated Commit Messages (Awareness — Controversial)
- **AIOps**
  - AI for Log Analysis (Anomaly Detection in Log Streams)
  - AI for Incident Response (Suggest Root Cause from Error Patterns)
  - AI for Monitoring (Intelligent Alerting, Noise Reduction)
  - Integrating LLMs into Runbooks (Interactive Troubleshooting)
- **Building Internal AI Developer Tools**
  - Internal Chat-with-Codebase Tool (RAG Over Your Repos)
  - Internal Documentation Q&A Bot
  - Automated Code Migration Assistant (Framework Upgrades)
  - Custom AI Linting Rules (Enforce Team Standards with LLMs)
  - On-Call Assistant (RAG Over Runbooks + Incident History)

> ### 🛠 Phase 5 Milestone Project: **AI-Powered Developer Toolkit**
> Build internal AI developer tools for your team:
> - **Codebase Q&A** — RAG pipeline over your Git repositories (clone, parse, chunk by function/class, embed, search). FastAPI endpoint: "How does X work?" with source file citations
> - **PR Review Bot** — GitHub webhook receives PR events, AI analyzes diff, posts review comments on potential issues (security, performance, style), uses custom team guidelines as system prompt context
> - **Documentation Generator** — Given a Python module, generates docstrings, README, API docs using LLM. Validates generated docs against actual function signatures with AST parsing
> - **Incident Assistant** — RAG over runbooks, past incident reports, and architecture docs. On-call engineer asks "Service X is returning 503s, what should I check?" and gets targeted troubleshooting steps
> - **Prompt Playground** — Internal web UI (FastAPI + simple frontend) for testing prompts against multiple models, comparing outputs side-by-side, saving prompt versions, running evaluation suites
> - All tools share the LLM Gateway from Phase 4 for unified access and cost tracking

---
---

## 🏗️ CAPSTONE PROJECT: AI Research Assistant Platform
> **This is the Phase 4 capstone — it ties everything together.**
>
> Build a production-grade AI research assistant platform:
>
> - **RAG Pipeline** ingesting multiple sources (PDFs, web pages, APIs, internal wikis)
>   - `unstructured` for document processing
>   - Semantic chunking with parent-child strategy
>   - Hybrid search (pgvector + BM25) with Cohere re-ranking
>   - Advanced RAG: query rewriting, HyDE, multi-query retrieval
>   - Contextual retrieval with document-level context prepended to chunks
>
> - **Multi-Agent System** (LangGraph)
>   - Researcher agent: web search (Tavily) + knowledge base RAG retrieval
>   - Analyst agent: synthesizes findings, compares sources, identifies gaps
>   - Writer agent: produces structured reports with citations
>   - Fact-checker agent: verifies claims against retrieved sources
>   - Orchestrator agent: routes queries, manages workflow, handles failures
>   - Persistent checkpointing with AsyncPostgresSaver
>   - Human-in-the-loop approval gates for high-stakes research
>
> - **LLM Gateway** with provider fallback and cost tracking
>   - LiteLLM proxy with model routing (complex reasoning → Claude, summarization → GPT-4o-mini)
>   - Semantic caching for repeated queries (Redis + pgvector)
>   - Per-user cost tracking and budget enforcement
>
> - **Streaming Chat UI** (FastAPI + SSE)
>   - Real-time streaming responses with agent status updates
>   - WebSocket for bidirectional agent interaction
>   - Source citations with click-to-view original document
>   - Conversation history with thread management
>
> - **Guardrails**
>   - Prompt injection defense (classifier-based input guard)
>   - PII filtering with `presidio` (input and output)
>   - Topic restriction (only research-relevant queries)
>   - Output factuality validation against retrieved sources
>   - Max iteration and cost budget guardrails per session
>
> - **Evaluation Suite**
>   - 100+ golden Q&A test cases with source documents
>   - RAGAS evaluation (faithfulness, relevance, context quality)
>   - DeepEval test suite in CI/CD (quality gate — must pass before deploy)
>   - promptfoo regression tests for all prompts
>   - LLM-as-judge for open-ended quality assessment
>
> - **Observability**
>   - Full agent trace logging with Langfuse
>   - OpenTelemetry traces correlated with agent decisions
>   - Prometheus metrics (quality scores, latency, cost, cache hit rate)
>   - Grafana dashboards (RED metrics + AI-specific metrics)
>   - Alerting on quality degradation and cost spikes
>
> - **Feedback Mechanism**
>   - Thumbs up/down + free text feedback per response
>   - Feedback stored in PostgreSQL with query context
>   - Weekly automated feedback analysis (LLM categorizes failure modes)
>   - Feedback-driven prompt improvement loop
>
> - **MLOps**
>   - MLflow experiment tracking for prompt variants
>   - A/B testing infrastructure for new prompts/models
>   - CI/CD with evaluation gates (GitHub Actions)
>   - Blue/green deployment for AI features
>
> - **Infrastructure**
>   - Dockerized all services
>   - docker-compose for local development (FastAPI + PostgreSQL/pgvector + Redis + Langfuse + Prometheus + Grafana)
>   - Kubernetes manifests for production
>   - Terraform for cloud resources
>
> **Why:** Covers RAG, agents, production AI concerns, evaluation, safety, feedback loops, and observability in one cohesive system. This is a portfolio-grade project that demonstrates AI engineering mastery.

---

## ✅ After Completing This Roadmap — You Can:
- Understand ML concepts, embeddings, and transformers well enough to make engineering decisions
- Navigate the LLM landscape and choose models based on cost, quality, and latency trade-offs
- Engineer effective prompts with structured output and proper versioning
- Build production RAG pipelines with proper chunking, hybrid search, re-ranking, and evaluation
- Design and implement single and multi-agent systems with LangGraph
- Build custom tools for agents (APIs, databases, code execution, browsers)
- Implement LLM Gateway with fallback, caching, and cost management
- Evaluate AI system quality systematically (RAGAS, DeepEval, promptfoo)
- Implement guardrails (prompt injection, PII, content filtering, OWASP LLM Top 10)
- Build feedback loops that continuously improve AI features
- Monitor AI systems in production (quality, latency, cost, safety)
- Make informed decisions: RAG vs fine-tuning vs prompt engineering
- Use AI tools to accelerate your own development workflow
- Build internal AI developer tools for your team
- Architect AI-native features within larger software systems
- **You have completed all four phases of the Software Engineering Mastery Roadmap**

---

## 📋 Quick Reference Summary

