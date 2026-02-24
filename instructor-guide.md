# How Agents Work: Instructor Guide

**Module Time:** 120 minutes  

---

## What This Module Is About

This module connects **classical AI agent theory** with **modern LLM-based agent systems**.

Learners move from understanding the internal anatomy of an agent (Session 2) to understanding:

- where agent theory comes from  
- how the classical perceive–act loop works  
- how modern frameworks extend it  
- why LLM agents are architected the way they are  

This session is conceptual but critical. It prevents learners from seeing modern agent platforms as “magic tools” and instead positions them as structured implementations of decades of AI research.

The goal is to help learners think like **architects of autonomous systems**, not just builders using frameworks.

---

## Core Objectives

By the end of this module, learners should be able to:

- Explain the historical definition of an AI agent  
- Compare classical agent architectures  
- Describe the classical perceive–act interaction loop  
- Distinguish classical loops from modern ReAct-style loops  
- Explain the three roles of the LLM: reasoner, planner, orchestrator  
- Identify what responsibilities belong to the LLM vs the runtime  
- Connect theory to modern no-code and code-first platforms  

---

## Must-Hit Topics

- Russell & Norvig definition of an agent  
- Simple reflex vs model-based vs goal-based vs utility-based agents  
- Perceive–Act loop  
- Learning as separate from interaction  
- ReAct pattern (Observe–Think–Act)  
- LLM as planner, reasoner, orchestrator  
- Separation between LLM and runtime  
- Transparency and interpretability differences  

---

## 1. Classical Agent Architectures & Modern Platforms  
**Time:** ~10 minutes  

### Purpose

Ground modern LLM agents in classical AI theory.

This prevents conceptual confusion later when learners encounter orchestration frameworks and multi-agent systems.

---

### Key Talking Points

- The definition of an agent predates LLMs  
- An agent is defined by interaction with an environment  
- Complexity does not define agenthood — interaction does  

Four classical architectures:

1. **Simple Reflex**
   - If condition → action
   - No internal state

2. **Model-Based Reflex**
   - Maintains internal state
   - Handles partial observability

3. **Goal-Based**
   - Evaluates actions against goals
   - Plans ahead

4. **Utility-Based**
   - Optimizes trade-offs
   - Maximizes expected utility

Modern LLM agents resemble goal-based and utility-based systems — but reasoning is generated dynamically via natural language instead of fixed algorithms.

---

### Teaching Tips

- Ask learners:
  > “Is a decision tree chatbot an agent? Which type?”
- Reinforce that most “AI tools” are still reflex systems
- Clarify that LLMs replace rule tables with dynamic reasoning
- Avoid diving into algorithmic search details

---

## 2. The Perceive–Act Loop & Its Modern Extensions  
**Time:** ~20 minutes  

### Purpose

Clarify the foundational interaction loop and distinguish it from modern LLM-based patterns.

---

### Classical Perceive–Act Loop

Core loop:

```
PERCEIVE → ACT → PERCEIVE → ACT → ...
```
Key idea:

- Reasoning is embedded in architecture
- There is no explicit “thinking step”
- Decision-making depends on agent type

Important clarification:

> Reasoning is not a separate stage in classical agents — it is the internal mechanism of the architecture.

---

### Learning as Separate

In classical systems:
```
PERCEIVE → ACT (real-time loop)
↓
LEARN (separate improvement process
```

Learning updates the model or rule base — but does not change the loop structure.

---

### The Modern Extension: ReAct

Modern LLM agents externalize reasoning:
```
OBSERVE → THINK → ACT → OBSERVE → THINK → ACT
```

Key differences:

- Reasoning is explicit and readable  
- Tool calls are dynamically selected  
- Decision logic is generated at runtime  
- The reasoning trace increases interpretability  

---

### Side-by-Side Contrast

Emphasize these distinctions:

| Classical | Modern ReAct |
|------------|--------------|
| Opaque logic | Explicit reasoning |
| Fixed design-time logic | Dynamic generation |
| Hard-coded action selection | Tool-call orchestration |
| Learning separate | Memory + prompt adaptation |

---

### Teaching Tips

- Ask:
  > “Where does reasoning happen in each system?”
- Emphasize interpretability as a production advantage
- Reinforce that ReAct is an extension, not a replacement of the loop
- Connect this back to Session 2 data flow

---

## 3. The LLM as Planner, Reasoner, and Orchestrator  
**Time:** ~15 minutes  

### Purpose

Clarify the **functional roles of the LLM** within the loop.

Prevent learners from equating “LLM = full agent.”

---

### Role 1: Reasoner

- Interprets situation
- Generates inference
- Determines next requirement

Reinforce:
This is generation, not retrieval.

---

### Role 2: Planner

- Decomposes multi-step tasks
- Sequences subtasks
- Adjusts when failures occur

Planning is dynamic and conditional.

---

### Role 3: Tool-Call Orchestrator

- Selects tool
- Fills parameter schema
- Waits for result
- Determines next action

Important distinction:

> The LLM chooses the action.  
> The runtime executes the action.

---

### LLM vs Runtime Responsibilities

Critical table to reinforce:

| Capability | LLM | Runtime |
|------------|------|---------|
| Generate reasoning | ✅ | ❌ |
| Execute APIs | ❌ | ✅ |
| Persist memory | ❌ | ✅ |
| Validate tool output | ❌ | ✅ |
| Enforce permissions | ❌ | ✅ |

Production insight:

Failing to separate these responsibilities creates fragile systems.

---

### Teaching Tips

- Ask:
  > “What happens if the LLM could execute code directly?”
- Emphasize safety and governance implications
- Reinforce architecture boundaries from Session 2
- Keep focus on conceptual clarity

---

## 4. Break  
**Time:** ~10 minutes  

Encourage learners to reflect on:

- Classical vs modern loops  
- Where reasoning lives  
- What the LLM can and cannot do  

---

## 5. Lab Transition  
**Time:** ~60 minutes  

Frame the lab as:

> “You are now mapping theory to architecture.”

Encourage learners to:

- Identify the loop type  
- Define reasoning boundaries  
- Clarify planner vs orchestrator  
- Distinguish runtime vs LLM responsibility  

The objective is conceptual fluency.

---

## Wrap-Up & Course Connection  
**Time:** ~5 minutes  

### Key Takeaways

- Agent theory predates LLMs  
- The perceive–act loop remains foundational  
- Modern systems externalize reasoning  
- LLMs function as planner, reasoner, and orchestrator  
- Runtime responsibility is separate and critical  

Reinforce that future modules build on this theoretical grounding.

---

### Reflection Questions

- Which classical architecture most closely resembles modern LLM agents?
- Why is reasoning not a separate step in classical agents?
- What architectural risks appear if LLM and runtime boundaries blur?

---

### Next Steps

Next module: **Current Agentic AI Frameworks and Ecosystems**

Learners will apply this theoretical foundation to compare real-world platforms and architectural trade-offs.

---

## Resources

- Russell & Norvig — *Artificial Intelligence: A Modern Approach* (Ch. 2–3)
- Yao et al. — *ReAct: Synergizing Reasoning and Acting in Language Models* (2022)
- OpenAI Function Calling Guide
- LangChain Agent Documentation
- Lilian Weng — *LLM-powered Autonomous Agents*

