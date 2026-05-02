# Memory Layer Projects - Research Summary

## Context
Researching existing memory systems for AI agents to understand persistent memory solutions that save and reuse context for different purposes.

---

## 1. MemOS

**What it is:** Research-grade "memory operating system" for AI developed by researchers from Shanghai Jiao Tong University and Zhejiang University.

**Status:** Actively growing (released July 2025)

**Key Features:**
- Treats memory as a core computational resource (like OS manages CPU/storage)
- Unifies plaintext, activation-based, and parameter-level memories through "MemCubes"
- MemCubes can be composed, migrated, and fused over time
- 159% improvement in temporal reasoning tasks vs OpenAI's memory systems
- 38.9% overall improvement on LOCOMO benchmark

**Architecture:**
- Three-layer OS-like architecture
- MemCubes as standardized memory units
- Enables flexible transitions between memory types

**Open Source:** Yes, on GitHub with integration for HuggingFace, OpenAI, Ollama

**URL:** https://github.com/MemTensor/MemOS

**Focus:** Research/infrastructure-oriented memory management at the OS level.

---

## 2. Mem0

**What it is:** Universal, self-improving memory layer for LLM applications

**Status:** Very active & growing (40k+ GitHub stars)

**Key Features:**
- Single-line install that adds memory to AI apps
- Works with OpenAI, LangGraph, CrewAI, and more
- Browser extensions for ChatGPT, Claude, Perplexity
- Can run locally on your device (no cloud required)
- Intelligently compresses chat history into optimized memory representations
- SOC 2 & HIPAA compliant

**Architecture:**
- Hybrid datastore: graph + vector + key-value stores
- Advanced embeddings for semantic understanding
- Graph-based enrichment links memories across apps and contexts
- Sub-300ms recall with semantic + keyword search

**Memory Features:**
- Timestamps, versioning, exportable
- Memories update, extend, derive, and expire
- TTL management for each memory

**Use Cases:**
- Customer support chatbots
- AI assistants
- Autonomous systems
- Cross-platform memory sharing

**URLs:** 
- https://github.com/mem0ai/mem0
- https://mem0.ai/

**Focus:** Continuous memory growth and improvement across AI application sessions.

---

## 3. Supermemory

**What it is:** Fast memory engine and API for building your "second brain"

**Status:** Active (11k+ GitHub stars, regular updates through Oct 2025)

**Key Features:**
- Add memories from URLs, PDFs, plain text
- Chat with stored content using natural language
- MCP (Model Context Protocol) integration for major AI tools
- Connects to Notion, Google Drive, OneDrive
- Claims 10x faster than Zep, 25x faster than Mem0
- Universal Memory MCP makes memories available to every LLM

**Architecture:**
- Sub-300ms recall
- Semantic + keyword search
- Graph-based indexing
- Can self-host or use cloud

**Use Cases:**
- Personal knowledge management
- Content aggregation across services
- "Second brain" applications
- Cross-tool memory access

**URLs:**
- https://github.com/supermemoryai/supermemory
- https://supermemory.ai/

**Focus:** Content aggregation and personal knowledge management with speed optimization.

---

## 4. Memoram

**What it is:** Personal memory assistant for cross-AI-tool sharing

**Status:** Early stage (launched ~May 2025)

**Key Features:**
- Securely stores and accesses memories across AI tools
- Real-time sync across devices and applications
- Custom tags for organization
- Fine-grained permissions (control which AI tools can access)
- Unique "MemoryKey" for secure sharing
- Designed for cross-platform portability

**Use Cases:**
- Health apps maintaining patient preferences
- Productivity tools sharing project context
- Legal/research tools with case information
- Any scenario needing memory across different AI applications

**URL:** https://www.memoram.app/

**Focus:** Cross-platform memory access with security and permission controls.

---

## 5. Amazon Bedrock AgentCore Memory (CORE)

**What it is:** Enterprise-grade AWS service for AI agent memory management

**Status:** Preview (released July 2025)

**Key Features:**
- Manages session and long-term memory for AI agents
- Provides relevant context to models
- Helps agents learn from past interactions
- Identity controls and tool integration
- Works with any framework and model
- Built-in observability dashboards

**Architecture:**
- Session memory (short-term context)
- Long-term memory extraction
- Memory lifecycle management
- Enterprise-grade security and compliance

**Use Cases:**
- Production AI agents at scale
- Enterprise deployments
- Complex multi-agent workflows

**Availability:** US East, US West, Asia Pacific Sydney, Europe Frankfurt

**URL:** https://aws.amazon.com/bedrock/agentcore/

**Focus:** Enterprise infrastructure for production AI agents at scale.

---

## 6. myNeutron

**What it is:** Universal memory system that captures and organizes knowledge across all your apps and makes it available to any AI

**Status:** Active (backed by Google Cloud & Worldpay, featured in TechCrunch)

**Key Features:**
- **One-click capture** from Gmail, Drive, Dropbox, web pages, PDFs
- **"Seeds"** - structured knowledge units that are searchable and reusable
- **Context injection** - Drop Seeds directly into ChatGPT, Claude, or Gemini
- **MCP Bridge** - Uses Model Context Protocol (open standard for AI apps)
- **Semantic search** - AI-powered search that understands intent
- **Blockchain preservation** - Optional eternal storage on Vanar chain
- Built-in AI assistant for querying your saved content

**Architecture:**
- Part of Vanar 5-layer stack (memory layer of larger AI infrastructure)
- Compresses knowledge into "Seeds"
- Unified search across all connected apps
- Works with multiple AI platforms simultaneously

**Use Cases:**
- Unified search across email, drive, and web
- Persistent context for AI conversations
- Research organization and retrieval
- Knowledge preservation

**URL:** https://myneutron.ai/

**Focus:** Capture-to-injection workflow with emphasis on cross-AI portability and optional permanent preservation.

**Unique aspects:**
- "Seeds" as structured knowledge units (vs generic memories)
- Blockchain-based eternal preservation option
- Positioned as memory layer of broader AI infrastructure stack
- Emphasizes context injection into any AI rather than just persistence

---

## Comparison Matrix

| System | Primary Focus | Open Source | Cross-Platform | Speed Claim | Unique Feature |
|--------|--------------|-------------|----------------|-------------|----------------|
| MemOS | Infrastructure | Yes | Yes | - | OS-level memory management |
| Mem0 | App Integration | Yes | Yes | Sub-300ms | Hybrid datastore (graph+vector+KV) |
| Supermemory | Second Brain | Yes | Yes | 10x-25x faster | MCP Universal Memory |
| Memoram | Security & Sharing | No | Yes | - | Fine-grained permissions |
| AWS Bedrock | Enterprise Scale | No | Limited | - | AWS-managed service |
| myNeutron | Capture & Inject | No | Yes | - | Seeds + blockchain preservation |

---

## Common Patterns

**What all systems provide:**
- ✅ Persistent memory for AI interactions
- ✅ Semantic search capabilities
- ✅ Cross-platform or cross-tool integration
- ✅ Some form of memory organization/structure
- ✅ API or programmatic access

**Architectural approaches:**
- **Storage:** Vector, graph, key-value, or hybrid combinations
- **Search:** Semantic (all), with some adding keyword search
- **Integration:** APIs, browser extensions, MCP support
- **Deployment:** Cloud-hosted, self-hosted, or both options

**Key differentiators:**
- **Speed:** Supermemory emphasizes performance
- **Security:** Memoram focuses on permissions and control
- **Research:** MemOS provides OS-level abstractions
- **Enterprise:** AWS Bedrock offers managed service at scale
- **Developer-friendly:** Mem0 provides single-line install
- **Permanence:** myNeutron offers blockchain preservation

---

## Technology Standards

**Model Context Protocol (MCP):**
- Open standard for connecting AI applications
- Adopted by: Supermemory (Universal Memory MCP), myNeutron (MCP Bridge)
- Enables AI-agnostic memory systems

**Common Integration Points:**
- OpenAI (ChatGPT)
- Anthropic (Claude)
- Google (Gemini)
- LangChain/LangGraph
- Browser extensions
- Cloud storage (Drive, Dropbox, OneDrive)

---

## Market Positioning

**For Developers:**
- **Mem0** - Easiest integration (single-line install)
- **MemOS** - Most research-oriented
- **Supermemory** - Speed-focused

**For End Users:**
- **myNeutron** - Capture-first workflow with Seeds
- **Memoram** - Security and cross-tool sharing
- **Supermemory** - Second brain aggregation

**For Enterprises:**
- **AWS Bedrock** - Managed service with compliance
- **Mem0** - SOC 2 & HIPAA compliant

---

## Use Case Mapping

**Personal Knowledge Management:**
- Supermemory, myNeutron

**Cross-AI Memory Sharing:**
- Mem0, Memoram, myNeutron, Supermemory

**Application Development:**
- Mem0, MemOS

**Enterprise Deployment:**
- AWS Bedrock, Mem0

**Research & Experimentation:**
- MemOS

**Permanent Preservation:**
- myNeutron (blockchain)

---

## Future Trends

Based on this landscape:

1. **MCP adoption** - Growing standard for AI interoperability
2. **Speed competition** - Performance benchmarks becoming key differentiator
3. **Privacy/security** - Increasing focus on user control and permissions
4. **Hybrid architectures** - Combining graph, vector, and key-value stores
5. **Blockchain integration** - Emerging pattern for permanent storage
6. **Self-hosting options** - Privacy-conscious users driving local deployment

---

**Last Updated:** October 24, 2025
