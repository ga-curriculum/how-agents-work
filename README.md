# How Agents Work
**Session Time:** 120 minutes  
**Format:** Instructor-Led  

---

## Prerequisites

- Completion of Session 1: Introduction to the Agentic AI Era  
- Conceptual understanding of the difference between Generative AI and Agentic AI  
- Familiarity with the idea that agents perceive, reason, and act  

---

## Learning Objectives

By the end of this session, students will be able to:

1. **Compare** classical agent architectures and explain how modern no-code and low-code platforms relate to them.
2. **Identify** the classical agent interaction loop (Perceive–Act) and **distinguish** it from modern extensions that include reasoning, memory, and learning.
3. **Illustrate** how LLMs act as planners, reasoners, and tool-call orchestrators within autonomous agent loops.

> This session bridges classical AI theory with modern practice. Students leave with a mental model that explains *why* modern agent platforms are built the way they are — not just *how* to use them.

---

## Session Breakdown

| # | Segment | Duration |
|---|---------|----------|
| 1 | Classical Agent Architectures & Modern Platforms | 10 min |
| 2 | The Perceive–Act Loop & Its Modern Extensions | 20 min |
| 3 | The LLM as Planner, Reasoner, and Orchestrator | 15 min |
| 4 | Break | 10 min |
| 5 | Lab | 60 min |
| 6 | Wrap-Up & Reflection | 5 min |
|   | **Total** | **120 min** |

---

## 1. Classical Agent Architectures & Modern Platforms (10 min)

### Where Does "Agent" Come From?

The concept of an AI agent predates LLMs by decades. Classical AI research defined agents precisely and rigorously — and those definitions still explain why modern systems are architected the way they are.

**Russell & Norvig's definition:**
> An *agent* is anything that can perceive its environment through sensors and acts upon that environment through actuators.

This sounds simple, but it has enormous implications: an agent is defined by its relationship to an environment, not by its internal complexity.

### Four Classical Agent Architectures

<img width="686" height="385" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/18c45aa7-51fb-4cf8-bd44-e6276029c276" />


Modern LLM agents are closest to **Goal-Based** and **Utility-Based** — but instead of hand-coded rules or utility functions, the LLM does the reasoning dynamically from natural language instructions.

### How Modern Platforms Map to Classical Theory

No-code and low-code platforms (n8n, Flowise, Relevance AI, GPT Builder) are not magic — they are implementations of classical agent architecture using LLMs as the reasoning engine.

| Classical Component | Modern Platform Equivalent |
|---|---|
| Sensors / Perception | User input, API responses, database reads |
| Internal state / Memory | Conversation history, vector databases |
| Goal representation | System prompt and task description |
| Action selection | LLM output → tool call decision |
| Actuators / Actions | API calls, file writes, email sends |

**Key insight:** When you configure a no-code agent, you are designing each of these components — even if the platform abstracts the implementation details.

### Discussion Prompt (3 min)

> Think about the last time you used an AI tool at work or in your personal life. Which classical agent type was it closest to? Was it truly goal-based, or was it more like a reflex agent dressed up with an LLM?

---

## 2. The Perceive–Act Loop & Its Modern Extensions (20 min)

### The Classical Perceive–Act Loop

The foundational loop in classical AI is deceptively simple:

<img width="354" height="207" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/5239ed21-8725-4c9f-bd1c-50d091136540" />


The agent:
1. **Perceives** the environment through its sensors (what is happening?)
2. **Acts** based on its architecture (what should I do?)
3. Repeats

**Reasoning is not a separate step** — it is embedded in the architecture itself. A simple reflex agent reasons by table lookup. A goal-based agent reasons by search. The loop doesn't change; the architecture determines what "deciding" looks like.

This is a common misconception to clear up early: reasoning is not a phase between perceiving and acting — it is the mechanism of the agent's decision-making, baked into its architecture.

### Learning as a Separate Mechanism

Classical agents can improve over time, but **learning is not part of the core interaction loop** — it is a separate improvement mechanism that operates on the agent's architecture:

<img width="593" height="452" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/8eef0135-d504-4870-9cbe-e227e94d8c6f" />


In modern LLM agents, "learning" typically takes the form of:
- Fine-tuning the model on new data
- Updating the agent's memory or knowledge base
- Adjusting the system prompt based on observed failures

### The Modern Extension: ReAct and Beyond

Modern LLM agent frameworks extend the classical loop with explicit reasoning traces and tool calls:

<img width="413" height="170" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/cbb4d0f6-855f-4c9b-b668-fad22bfb6ab2" />


This is the **ReAct pattern** (Reasoning + Acting), where the agent:
1. **Observes** the current state (user input + memory + previous results)
2. **Thinks** — generates an explicit reasoning trace in natural language
3. **Acts** — selects and calls a tool, or produces a final response
4. **Observes** the result of the action, and repeats

<img width="591" height="464" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/717eb9c9-dbff-4dd4-b334-635a72b34eb5" />


### Classical Loop vs. Modern ReAct: Side-by-Side

| Dimension | Classical Perceive–Act | Modern ReAct |
|---|---|---|
| Reasoning location | Inside the architecture | Explicit, in natural language |
| Decision mechanism | Rules, search, or utility function | LLM generation |
| Transparency | Opaque (code-based logic) | Interpretable (reasoning trace) |
| Flexibility | Fixed at design time | Dynamic from prompt instructions |
| Tool use | Built-in or absent | Dynamic tool selection |
| Learning | External fine-tuning | Memory updates + prompt adjustment |

### Check for Understanding (2 min)

> In the ReAct loop, where does reasoning happen, and how is that different from a classical goal-based agent?

*(Expected answer: In ReAct, reasoning happens as a natural language generation step, explicit and readable. In classical agents, reasoning is the internal decision mechanism — a search algorithm, a rule table, or a utility calculation — not a visible step.)*

---

## 3. The LLM as Planner, Reasoner, and Orchestrator (15 min)

### Three Roles of the LLM in an Agent Loop

The LLM is not the agent — it is the **brain** of the agent. Depending on context, it plays three distinct roles simultaneously:

#### Role 1: Reasoner

The LLM generates a chain of thought — a reasoning trace — that interprets the current situation and determines what is needed next.

```
Situation:  User says "Book me a flight to São Paulo next Friday."
Reasoning:  "I need to know the departure city, the user's preferences,
             and available flights. I'll call the flight_search tool first."
```

This is not retrieval — the LLM is generating new inferences based on context, instructions, and its training.

#### Role 2: Planner

For complex, multi-step tasks, the LLM decomposes the goal into subtasks and sequences them:

<img width="362" height="273" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/6061426b-b716-44c2-8b5b-4c737bcb1a36" />

Planning in LLMs is dynamic — it adapts if a step fails or returns unexpected results.

#### Role 3: Tool-Call Orchestrator

The LLM decides which tools to call, with what parameters, and in what order. Tools are described to the LLM as structured schemas (names, parameters, descriptions), and the LLM generates structured calls:

```json
{
  "tool": "web_search",
  "parameters": {
    "query": "Competitor X Q3 2024 product announcements",
    "max_results": 5
  }
}
```

The LLM does not run the tool — it instructs the **agent runtime** to run it, waits for the result, and then decides the next step.

### What the LLM Cannot Do (and Why This Matters)

| Capability | LLM | Agent Runtime |
|---|---|---|
| Generate reasoning and text | ✅ | ❌ |
| Execute code or API calls | ❌ | ✅ |
| Access external databases | ❌ | ✅ |
| Persist memory between sessions | ❌ | ✅ |
| Validate action outcomes | ❌ | ✅ |

This distinction is critical for production design: the LLM is responsible for *what* to do; the runtime is responsible for *doing it* safely and reliably.

### The Full Modern Agent Loop (Annotated)

<img width="297" height="470" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/1e01616a-3673-4a3d-b7ac-360357b03b77" />


---

## 4. Break (10 min)

---

## 5. Lab (60 min)

https://pages.git.generalassemb.ly/Build-AI-Agents/How-Agents-Work/

---

## 6. Wrap-Up & Reflection (5 min)

### Key Takeaways
- Modern Agents Are Built on Classical Foundations
- Reasoning Is the Architecture
- The LLM Is Not the Agent

> Next session: **Current Agentic AI Frameworks and Ecosystems**

## Resources

- Russell & Norvig — *Artificial Intelligence: A Modern Approach*, Chapters 2 and 3
- Yao et al. — *ReAct: Synergizing Reasoning and Acting in Language Models* (2022) — [arxiv.org/abs/2210.03629](https://arxiv.org/abs/2210.03629)
- [LangChain Agent Documentation](https://docs.langchain.com/docs/components/agents)
- [OpenAI Function Calling Guide](https://platform.openai.com/docs/guides/function-calling)
- [Flowise Documentation](https://docs.flowiseai.com/)

---

*General Assembly · Build AI Agents · BAA 3.0 · © 2026*
