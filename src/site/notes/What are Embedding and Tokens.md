---
{"dg-publish":true,"permalink":"/what-are-embedding-and-tokens/","dg-note-properties":{}}
---

What are Embeddings? 

In AI, the term you are likely referring to is **embeddings**.

Embeddings are numerical representations of data—like words, sentences, or images—converted into vectors (long lists of numbers). They map text into a mathematical space where items with **similar meanings sit closer together**
## What are Tokens?

**Tokens** are the fundamental units of text that Large Language Models (LLMs) read and generate.

----------------------------------------------------------------

## Math as a "Language" (Tokens & Patterns)

To a Large Language Model (LLM), mathematical symbols, formulas, and numbers are just specialized forms of text.

- **Tokenization:** Equations are broken down into tokens (e.g., $x^2 + 3x = 10$ becomes `["x", "^2", " +", " 3", "x", " =", " 10"]`).
    
- **Pattern Recognition:** Models are trained on millions of math textbooks, research papers, and code repositories. They learn which symbols typically follow others in specific contexts (e.g., seeing $a^2 + b^2 =$ strongly predicts $c^2$).
  see:[[What is AI\|What is AI]]
  
  **Tokens** and **embeddings** are the two foundational steps an AI model uses to process human language into mathematical data it can understand.

**1. Tokens (How AI Reads)**

### Tokens are the basic building blocks of text for an AI. Instead of reading full words or single letters, an LLM breaks text down into smaller chunks called tokens.

- **What a token is:** A token can be a whole word, a sub-word, a single character, or punctuation. On average, 1 token is about 4 characters or 0.75 words in English.
    
- **How it works:** The sentence _"Unbelievable tech!"_ might be split into tokens like: `["Un", "believ", "able", " tech", "!"]`.
    
- **Numerical ID:** Each unique token is assigned a specific number ID. The AI converts your text input into a sequence of numbers (e.g., `[1542, 8931, 412, 98, 12]`).
    

**2. Embeddings (How AI Understands Meaning)**

While tokens turn text into numbers, **embeddings** turn those numbers into _meaning_ and _context_.

- **What an embedding is:** An embedding is a long list of numbers (a vector) that places a token or piece of text into a high-dimensional mathematical space.
    
- **How it works:** Words with similar meanings or contexts are placed close together in this mathematical space.
    
    - For example, the embeddings for **"king"** and **"queen"** will sit very close to each other, while **"king"** and **"banana"** will be far apart.
        
    - This allows the AI to perform "semantic math." A classic example:
        
        $$\text{Embedding("King")} - \text{Embedding("Man")} + \text{Embedding("Woman")} \approx \text{Embedding("Queen")}$$