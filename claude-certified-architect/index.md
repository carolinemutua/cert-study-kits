---
title: Claude Certified Architect
layout: default
nav_order: 4
has_children: true
---

# Claude Certified Architect: Foundations

A practice-first study kit for the Claude Certified Architect (Foundations) exam. The credential confirms that a specialist can make sound trade-off decisions when building production Claude solutions across four core technologies: the Claude API, the Claude Agent SDK, the Model Context Protocol (MCP), and Claude Code.

The kit is built for someone who already authors skills, builds MCP servers, and writes evaluation logic, and who needs to convert that hands-on experience into a passing score. The sequencing follows the skills gap rather than the domain numbers, so the heaviest and least familiar domain leads.

## Exam facts at a glance

| Attribute | Detail |
| --- | --- |
| Credential | Claude Certified Architect: Foundations |
| Maintained by | Anthropic |
| Technologies assessed | Claude API, Claude Agent SDK, Model Context Protocol (MCP), Claude Code |
| Question type | Multiple choice, one correct answer of four |
| Scoring | 100 to 1000 scale |
| Passing score | 720 (a score of 720 or greater passes) |
| Guessing penalty | None, so every question should be answered |
| Scenario structure | Four of eight possible scenarios, randomly selected |
| Question style | Realistic industry scenarios (customer support agents, multi-agent research, CI/CD integration, structured extraction) |
| Recommended experience | Around six months hands-on with the Agent SDK, Claude Code, MCP, and prompt engineering |

## The four technologies in one line

The API is the raw conversation. The Agent SDK wraps it in a tool-calling loop that can delegate. MCP plugs in the backend. Claude Code is the ready-made agent configured with files.

```mermaid
mindmap
  root((Building with<br/>Claude))
    Claude API
      Messages loop
      tool_use
      stop_reason
      JSON output
    Agent SDK
      agent loop
      subagents
      Task tool
      hooks and sessions
    MCP
      servers
      tools and resources
      structured errors
    Claude Code
      CLAUDE.md
      rules and skills
      planning mode
      CLI and CI/CD
```

## The API loop (learn this before anything else)

Every agent behaviour on the exam is built on one loop. The API is stateless, so the whole message history is resent each call. The model replies, the code inspects `stop_reason`, and either finishes or runs a tool and appends the result.

```mermaid
flowchart LR
    A["Send full history + tools"] --> B["Model replies"]
    B --> C{"stop_reason?"}
    C -->|end_turn| D["Done"]
    C -->|tool_use| E["Run the tool"]
    E --> F["Append result as a user message"]
    F --> A
```

## What the exam measures

Five domains. The percentages are the published share of scored questions, which drives how the sprint plan allocates time.

```mermaid
pie showData
    title Claude Architect scored weight by domain
    "D1 Agent architecture and orchestration (27%)" : 27
    "D3 Claude Code configuration (20%)" : 20
    "D4 Prompt and structured output (20%)" : 20
    "D2 Tool design and MCP (18%)" : 18
    "D5 Context and reliability (15%)" : 15
```

## Pages in this kit

| Page | Purpose |
| --- | --- |
| [Two-week sprint plan]({{ site.baseurl }}/claude-certified-architect/plan/) | Gap-ordered sprint, heaviest and least familiar domain first |
| [Domain deep-dives]({{ site.baseurl }}/claude-certified-architect/domains/) | Each of the five domains with a diagram, the key concepts, and the exam traps |
| [Practice and flashcards]({{ site.baseurl }}/claude-certified-architect/practice/) | A self-test bank organised by domain, plus rapid-recall flashcards |
| [Resources]({{ site.baseurl }}/claude-certified-architect/resources/) | Official Anthropic courses and documentation for each technology |
