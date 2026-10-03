---
{"dg-publish":true,"permalink":"/prompt-engineering/","dg-note-properties":{}}
---

**Prompt engineering** is the practice of designing, refining, and structuring inputs (prompts) to guide Large Language Models (LLMs) and generative AI systems to produce accurate, context-aware, and high-quality outputs.

Instead of relying on luck or trial and error, prompt engineering applies structured techniques to steer how an AI model interprets, reasons through, and formats its answers.

### Key Components of an Effective Prompt

A complete prompt usually contains four primary elements:

|**Component**|**Description**|**Example**|
|---|---|---|
|**Instruction / Task**|The explicit action or goal for the AI to execute.|_"Summarize the attached article in 3 main points."_|
|**Persona / Role**|The identity, expertise, or perspective the model should adopt.|_"Act as a Senior Cybersecurity Auditor..."_|
|**Context & Constraints**|Background details, target audience, tone, or boundaries.|_"Target audience: non-technical founders. Do not use jargon."_|
|**Output Format**|Desired layout, structural constraints, or style.|_"Return the result as a valid JSON object with keys: `summary`, `action_items`."_|

### Core Prompting Techniques

#### 1. Zero-Shot Prompting

Asking the model to perform a task directly without providing any prior examples.

- **Example:** _"Classify this email as Urgent, Normal, or Low Priority: [Email Text]"_
    

#### 2. Few-Shot Prompting (In-Context Learning)

Providing 1 to 5 input-output examples inside the prompt to guide formatting, tone, or reasoning.

- **Example:**
    
    Plaintext
    
    ```
    Text: "The system crashed during checkout." -> Tag: Bug Report
    Text: "How do I upgrade my plan?" -> Tag: Billing Inquiry
    Text: "The new feature saved me 2 hours!" -> Tag: Positive Feedback
    Text: "Can I extract my data as a CSV?" -> Tag:
    ```
    

#### 3. Chain-of-Thought (CoT) Prompting

Forcing the model to generate step-by-step reasoning tokens before arriving at a final answer. This significantly reduces mathematical, logic, and multi-step errors.

- **Example:** _"Solve this math word problem step-by-step. Show your calculations first, then state the final answer."_
    

#### 4. Tree-of-Thoughts (ToT) / Multi-Path Reasoning

Guiding the model to explore multiple alternative paths, evaluate pros/cons for each, and then select the optimal solution. Useful for architecture decisions, strategy, or creative brainstorming.

#### 5. Generated Knowledge / Priming

Asking the model to generate key facts or context about a subject _before_ drafting the actual output to ensure accuracy.

### Modern Frameworks & Practical Techniques

#### The **R.O.C.E.** Prompt Framework

When writing complex prompts, structure them clearly:

- **Role:** Who is the AI? (e.g., _"Senior Frontend Developer"_)
    
- **Objective:** What is the primary task?
    
- **Context:** What background information is required?
    
- **Expectations:** What constraints, rules, or visual formats must be met?
    

#### System Prompts vs. User Prompts

- **System Prompt:** Sets foundational behavior, security boundaries, brand voice, and guidelines that persist across conversations.
    
- **User Prompt:** The dynamic, specific query or data provided at runtime.
    

#### Agentic Prompting

Designing prompts that enable an AI agent to use external tools (APIs, search engines, databases, custom functions), check its own work, and execute multi-step workflows autonomously.

### Best Practices for Quality Results

1. **Be Specific & Explicit:** State exact counts, length bounds, tone descriptions, and structural requirements.
    
2. **Tell the Model What to Do (Not Just What _Not_ to Do):** Direct instructions yield higher success rates than pure negative constraints.
    
3. **Use Delimiters:** Wrap input data using backticks (```), XML tags (`<context>...</context>`), or quotes to clearly mark raw inputs.
    
4. **Iterate & Refine:** Prompt engineering is an iterative process. Test with diverse test cases to check for edge-case failure modes.