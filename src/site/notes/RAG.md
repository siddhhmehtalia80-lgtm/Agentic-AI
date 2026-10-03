---
{"dg-publish":true,"permalink":"/rag/","dg-note-properties":{}}
---

**RAG** stands for **Retrieval-Augmented Generation**.

It is an architecture and technique in artificial intelligence that enhances Large Language Models (LLMs) by connecting them to external, verified data sources—such as databases, internal company documents, or web search APIs—before generating a response.

### Why RAG is Needed

Standard LLMs are trained on fixed datasets up to a specific point in time. This creates two main limitations:

1. **Knowledge Cutoffs:** The model doesn't know about current events or private internal files (e.g., your company's internal wiki or recent news).
    
2. **Hallucinations:** When an LLM doesn't know the answer, it may generate convincing but incorrect information.
    

RAG solves these problems by allowing the model to look up relevant facts from an authoritative database **first**, and then write a response grounded strictly in those facts.

### How RAG Works (Step-by-Step)

```
[ User Query ] ──► 1. Retrieval ──► [ Relevant Documents ] 
                          │
                          ▼
                   2. Augmentation 
                          │
                          ▼
[ Prompt + Context ] ──► 3. Generation ──► [ Fact-Grounded Output ]
```

1. **Retrieval:** When a user asks a question, a retrieval system searches an external database (often a **Vector Database**) to find the most relevant information or documents related to the query.
    
2. **Augmentation:** The retrieved documents are dynamically injected into the LLM's prompt alongside the original user question as contextual background.
    
3. **Generation:** The LLM reads the context and generates an answer that is directly backed by the retrieved data, usually citing the exact source.
    

### Key Benefits of RAG

- **Reduces Hallucinations:** Answers are grounded in real, verifiable documents rather than pure memory.
    
- **Up-to-Date & Private Information:** Connects models to live search feeds or secure company data without needing to re-train or fine-tune the LLM.
    
- **Source Attribution:** Allows the model to cite exact sources, links, or documents for users to double-check accuracy.