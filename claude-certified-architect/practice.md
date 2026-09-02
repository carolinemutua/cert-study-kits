---
title: Practice and flashcards
layout: default
parent: Claude Certified Architect
nav_order: 3
---

# Practice questions and flashcards

A self-test bank organised by domain, followed by rapid-recall flashcards. Answers sit inside collapsible blocks, so each question can be attempted before the answer is revealed. These questions are written to drill the concepts and the exam traps, not to reproduce any official exam. Use the bank on the review days and after the Day 10 mock to drill weak areas.

How to use it: read the question, answer out loud or in writing, then expand the answer. Track every miss by domain and feed those into the remediation days. Do the questions even for the domains that feel easy, because the wrong answers on this exam are written to sound right.

---

## Domain 1: Agent architecture and orchestration

**Q1.** A coordinator agent is configured but cannot spawn any subagents. What is the most likely cause?

<details markdown="1"><summary>Answer</summary>

The `Task` tool is not in the coordinator's `allowedTools`. A coordinator delegates by calling the Task tool, so without it in the allow list it has no way to spawn a subagent.
</details>

**Q2.** A subagent is spawned to summarise a document, but it behaves as if it never saw the earlier conversation. Is this a bug?

<details markdown="1"><summary>Answer</summary>

No. A subagent starts with a blank context and sees only the prompt it is given. It does not inherit the coordinator's chat history. Everything the subagent needs must be passed in its prompt. Assuming inheritance is a classic trap.
</details>

**Q3.** You are asked to speed up a workflow that runs three independent research subagents. What is the correct approach, and what is the tempting wrong one?

<details markdown="1"><summary>Answer</summary>

Correct: issue all three Task calls in a single response so they run in parallel. Tempting wrong answer: a sequential loop that spawns one, waits, then spawns the next, which is what "run them one after another" produces and does not speed anything up.
</details>

**Q4.** A policy says refunds above 500 must never be issued by the agent. Where should that rule be enforced, and where should it not?

<details markdown="1"><summary>Answer</summary>

Enforce it in code with a hook (for example a PostToolUse or pre-action hook that blocks the action). Do not rely on the prompt to enforce policy, because a prompt is guidance the model can be argued out of, whereas a hook is deterministic.
</details>

**Q5.** What is the difference between `resume` and `fork_session`?

<details markdown="1"><summary>Answer</summary>

`resume` continues the same conversation from where it left off. `fork_session` branches it into a separate line, so the original is preserved and a variant can be explored independently.
</details>

---

## Domain 2: Tool design and MCP integration

**Q6.** Requests to "analyze the uploaded report" keep getting routed to a web-search tool instead of the document tool. Both tools say "analyzes content and extracts key information." What is the fix?

<details markdown="1"><summary>Answer</summary>

Rewrite the tool descriptions so they differentiate. Each description must state when to use that tool versus the similar one (for example "use for uploaded documents and files" versus "use for live web pages"). Vague, near-identical descriptions are the root cause of misrouting.
</details>

**Q7.** Why is returning `{"error": "500"}` from a tool worse than returning a structured error?

<details markdown="1"><summary>Answer</summary>

A bare error string gives the agent nothing to act on. A structured error carries `isError`, an error category, and whether it is retryable, so the agent can decide to retry, choose another tool, or escalate. Reasoning depends on structure, not a status code in a string.
</details>

**Q8.** When should `tool_choice` be set to force a specific tool rather than left on `auto`?

<details markdown="1"><summary>Answer</summary>

When the step must perform a specific action rather than decide whether to act. Leaving it on `auto` when the workflow requires the tool to run is a trap, because the model may choose to answer in prose instead of calling the tool.
</details>

**Q9.** How should MCP server secrets such as API tokens be supplied?

<details markdown="1"><summary>Answer</summary>

Through environment variables referenced in the configuration (for example `${GITHUB_TOKEN}`), never committed into the config file. The reference to the variable is committed; the token itself stays out of source control.
</details>

---

## Domain 3: Claude Code configuration and workflows

**Q10.** A project CLAUDE.md and a global CLAUDE.md give conflicting guidance. Which wins?

<details markdown="1"><summary>Answer</summary>

The more specific one. Project configuration overrides user configuration, which overrides global. The trap is getting the direction backwards and assuming the global setting wins.
</details>

**Q11.** A rule in `.claude/rules/` does not seem to apply to a file you are editing. What is the first thing to check?

<details markdown="1"><summary>Answer</summary>

Its glob scope. Path-scoped rules load only for files that match their glob. If the file does not match, the rule never loads. The trap is assuming every rule always applies everywhere.
</details>

**Q12.** What do `context: fork` and `allowed-tools` do in a SKILL.md?

<details markdown="1"><summary>Answer</summary>

`context: fork` runs the skill in an isolated context so it does not pollute the main conversation. `allowed-tools` restricts which tools the skill may use. Together they scope a skill's blast radius.
</details>

**Q13.** For a Claude-based check running in a CI pipeline, which invocation is correct?

<details markdown="1"><summary>Answer</summary>

Headless mode with `-p` for the prompt and `--output-format json` so the pipeline can parse the result. The tuning trap is optimising to catch every possible issue rather than to minimise false positives, which is what makes a CI check usable.
</details>

---

## Domain 4: Prompt engineering and structured output

**Q14.** What is the most reliable way to get schema-valid JSON out of the model?

<details markdown="1"><summary>Answer</summary>

Define a tool whose input schema is exactly the output shape wanted, and force that tool with `tool_choice`. The model then returns arguments that conform to the schema. Asking for JSON in prose is the trap, because the output is not guaranteed to be valid.
</details>

**Q15.** A structured-output call returns an invalid result. What should the retry contain?

<details markdown="1"><summary>Answer</summary>

The original text, the bad answer the model produced, and the exact validation error. Feeding all three back lets the model correct the specific fault. A blind re-ask usually repeats the same mistake.
</details>

**Q16.** A team wants to move both a blocking pre-merge check and an overnight tech-debt report to the Batch API to save fifty percent. Is that correct?

<details markdown="1"><summary>Answer</summary>

No. The Batch API is fifty percent cheaper but can take up to 24 hours with no latency guarantee. It suits the overnight report, which tolerates delay, but not the pre-merge check, which blocks a waiting developer and needs a synchronous call.
</details>

**Q17.** Name two properties of the Batch API that make it unsuitable for interactive agent tool loops.

<details markdown="1"><summary>Answer</summary>

It is asynchronous with up to a 24-hour window (no real-time response), and it is one-shot rather than a live tool-calling loop. Each request is identified by a `custom_id` for matching results later, which also signals its batch, not interactive, design.
</details>

---

## Domain 5: Context management and reliability

**Q18.** Two credible sources give contradictory figures for a key metric. What should the agent do?

<details markdown="1"><summary>Answer</summary>

Preserve both values with their source and date, and surface the conflict with attribution rather than silently choosing one. For example, note that a 2023 source says one figure and a 2024 source says another, which is more useful than a single unexplained number.
</details>

**Q19.** What is "lost in the middle," and how is it mitigated?

<details markdown="1"><summary>Answer</summary>

Models attend less reliably to information buried in the middle of a long input than to the start and end. Mitigate it by placing the key instructions and facts at the beginning and end of the prompt.
</details>

**Q20.** One subagent in a multi-agent run fails. What is the reliable behaviour?

<details markdown="1"><summary>Answer</summary>

The coordinator continues with the partial results from the subagents that succeeded, and attributes the gap, rather than aborting the entire run on a single failure.
</details>

**Q21.** Name the three conditions that should trigger escalation to a human.

<details markdown="1"><summary>Answer</summary>

A policy gap (the situation is not covered by the rules), an explicit user request for a human, or an inability to make progress. The trap is guessing an answer instead of escalating when one of these holds.
</details>

---

## Rapid-recall flashcards

Cover the right column, recall it from the left, then check.

| Prompt | Recall |
| --- | --- |
| Passing score | 720 or greater, on a 100 to 1000 scale |
| Guessing penalty | None, so answer every question |
| Scenario structure | Four of eight possible scenarios, randomly selected |
| Four core technologies | Claude API, Agent SDK, MCP, Claude Code |
| API is stateless, so each call | Resends the whole message history |
| Loop ends when stop_reason is | end_turn |
| Coordinator needs this tool to delegate | Task |
| A subagent starts with | A blank context, only its own prompt |
| Parallel subagents | Many Task calls in one response |
| Enforce policy in code, not the prompt, using | A hook |
| Fixes tool misrouting | Descriptions that differentiate the tools |
| A good tool error carries | isError, category, retryable |
| MCP secrets supplied via | Environment variables, not committed |
| CLAUDE.md conflict winner | The more specific (project over global) |
| Rules load only when | Their glob matches the file |
| Force schema-valid JSON via | A tool schema plus forced tool_choice |
| Retry a bad structured output with | The text, the bad answer, and the exact error |
| Batch API | Fifty percent cheaper, up to 24h, custom_id, one-shot |
| Batch API is wrong for | Blocking or interactive tool loops |
| Conflicting sources | Keep both with source and date |
| Long-prompt weak spot | Lost in the middle, so key info at the edges |
| Subagent fails | Continue with partial results |
| Escalate on | Policy gap, explicit request, or no progress |
| Heaviest domain | Domain 1, agent architecture (27%) |

## Scoring the mock

On the Day 10 full mock, tag every miss with its domain, then re-study the two lowest-scoring domains first. A miss on a flashcard is a signal to re-read that domain's deep-dive, not to move on.
