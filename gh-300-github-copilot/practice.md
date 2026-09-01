---
title: Practice and flashcards
layout: default
parent: GH-300 GitHub Copilot
nav_order: 3
---

# Practice questions and flashcards

A self-test bank organised by skill area, followed by rapid-recall flashcards. Answers sit inside collapsible blocks, so each question can be attempted before the answer is revealed. Use this bank on the review days and after the Day 10 mock to drill weak areas.

How to use it: read the question, answer out loud or in writing, then expand the answer. Track every miss by area and feed those into the remediation days.

---

## Area 1: Use GitHub Copilot responsibly

**Q1.** A Copilot suggestion compiles and looks correct. Why is that not enough to accept it?

<details markdown="1"><summary>Answer</summary>

Because AI output must always be validated. Copilot can produce code that is plausible but wrong, insecure, biased, or based on outdated patterns. The developer stays accountable for reading, testing, and reasoning about the suggestion before accepting it.
</details>

**Q2.** Name three risks or limitations of generative AI coding tools that the exam expects you to describe.

<details markdown="1"><summary>Answer</summary>

Any three of: hallucination or plausible-but-incorrect output, insecure or vulnerable code, biased output, reproduction of copyrighted or public code, and a lack of live or project-specific knowledge. The mitigation in every case is human validation and appropriate safeguards.
</details>

**Q3.** Who is responsible for code that Copilot generates and a developer accepts into a repository?

<details markdown="1"><summary>Answer</summary>

The developer. Copilot assists, but ownership and accountability for accepted output remain with the person who commits it.
</details>

---

## Area 2: Use GitHub Copilot features

**Q4.** Distinguish inline suggestions, Copilot Chat, and agent mode.

<details markdown="1"><summary>Answer</summary>

Inline suggestions autocomplete code as you type. Chat answers questions and generates code from a conversation in the editor. Agent mode carries out a multi-step task, editing files and running tools with less step-by-step direction. All three are triggered from the IDE.
</details>

**Q5.** What is the GitHub Copilot CLI, and name two things it does?

<details markdown="1"><summary>Answer</summary>

It brings Copilot to the command line. It can explain or suggest shell commands, run interactively and in sessions, generate scripts, and help manage files, all from the terminal.
</details>

**Q6.** What is an instructions file used for?

<details markdown="1"><summary>Answer</summary>

It supplies persistent, repository- or workspace-level context and standards to Copilot, so responses stay consistent with the project's conventions without repeating the same guidance in every prompt. Prompt files serve a similar purpose for reusable prompts.
</details>

**Q7.** Which organisation-level controls does an administrator use to govern Copilot?

<details markdown="1"><summary>Answer</summary>

Organisation-wide policy management (including feature availability across IDEs and github.com), Copilot Code Review policies, audit log events for monitoring, and subscription management through the REST API.
</details>

**Q8.** What do Agent Sessions and Sub-Agents help with?

<details markdown="1"><summary>Answer</summary>

They manage and optimise context. Agent sessions organise an agent's work, and delegating to sub-agents keeps each context focused so a large task does not overwhelm a single context window.
</details>

---

## Area 3: Understand GitHub Copilot data and architecture

**Q9.** Trace what happens to a prompt from the editor to the returned suggestion.

<details markdown="1"><summary>Answer</summary>

Input and surrounding context are assembled into a prompt (prompt building), passed through proxy filtering before the model, processed by the large language model, then post-processed with safety and public-code filters before the suggestion is returned to the editor.
</details>

**Q10.** What does the proxy do in the Copilot architecture?

<details markdown="1"><summary>Answer</summary>

It sits between the editor and the model, filtering and handling the request (for example applying content exclusions and safety filtering) on the way in, and contributing to post-processing on the way out.
</details>

**Q11.** State two limitations of the large language model behind Copilot.

<details markdown="1"><summary>Answer</summary>

It has no live or real-time knowledge of your running system, and its training has a cut-off so it may not know the newest libraries or APIs. It also has no true understanding, so it can be confidently wrong.
</details>

---

## Area 4: Apply prompt engineering and context crafting

**Q12.** What is the difference between zero-shot and few-shot prompting?

<details markdown="1"><summary>Answer</summary>

Zero-shot describes the task with no examples. Few-shot includes one or more input-output examples in the prompt to steer the model toward the desired pattern.
</details>

**Q13.** Besides the text you type, what else forms the context of a Copilot prompt in the IDE?

<details markdown="1"><summary>Answer</summary>

Open files and nearby code, comments, the current file's contents, and, in chat, the conversation history. Copilot determines context from these signals, which is why keeping relevant files open improves suggestions.
</details>

**Q14.** Give two best practices for crafting an effective Copilot prompt.

<details markdown="1"><summary>Answer</summary>

Any two of: be specific about the goal, provide relevant context (open the right files, add examples), break large tasks into smaller ones, and iterate by refining the prompt after reading the result.
</details>

---

## Area 5: Improve developer productivity with GitHub Copilot

**Q15.** Name three productivity use cases Copilot supports beyond writing new code.

<details markdown="1"><summary>Answer</summary>

Any three of: refactoring existing code, generating documentation, explaining unfamiliar code, generating sample or test data, modernising legacy code, and writing tests.
</details>

**Q16.** How does Copilot help with testing?

<details markdown="1"><summary>Answer</summary>

It generates unit and integration tests, helps identify edge cases, and writes assertions, which speeds up building coverage.
</details>

**Q17.** Copilot suggests a fix that improves performance. What must the developer still do?

<details markdown="1"><summary>Answer</summary>

Validate it: confirm the change is correct, benchmark or test it where it matters, and make sure it does not introduce a regression or security issue. Suggestions are a starting point, not a guarantee.
</details>

---

## Area 6: Configure privacy, content exclusions, and safeguards

**Q18.** What does a content exclusion do?

<details markdown="1"><summary>Answer</summary>

It stops Copilot from using specified files or repositories as context and from offering suggestions in them, so sensitive code is not sent to the service or completed by it.
</details>

**Q19.** What does the "suggestions matching public code" filter do when enabled?

<details markdown="1"><summary>Answer</summary>

It blocks suggestions that match publicly available code, reducing the risk of reproducing licensed or public code verbatim.
</details>

**Q20.** A developer reports Copilot gives no suggestions in one repository. What is a likely cause tied to this area?

<details markdown="1"><summary>Answer</summary>

A content exclusion is configured for that file or repository, so Copilot is intentionally silent there. Checking the exclusion settings is the first troubleshooting step.
</details>

**Q21.** Who owns the output Copilot generates, and what is the limitation to keep in mind?

<details markdown="1"><summary>Answer</summary>

The developer owns and is responsible for accepted output. The limitation is that Copilot does not guarantee the suggestion is correct, secure, or free of resemblance to existing code, so validation and the public-code filter matter.
</details>

---

## Rapid-recall flashcards

Cover the right column, recall it from the left, then check.

| Prompt | Recall |
| --- | --- |
| Passing score | 700 or greater |
| Exam length | Approximately 90 minutes, proctored |
| Level | Intermediate |
| Heaviest area | Use GitHub Copilot features (25-30%) |
| Second heaviest | Use GitHub Copilot responsibly (15-20%) |
| Golden rule of responsible use | Always validate AI output |
| Who owns accepted output | The developer |
| Three IDE trigger modes | Inline suggestions, chat, agent mode |
| Copilot on the command line | GitHub Copilot CLI |
| Persistent project context for consistent responses | Instructions file (prompt files for reusable prompts) |
| Org controls | Policy management, Code Review policy, audit logs, REST API subscriptions |
| Suggestion lifecycle | Input, prompt building, proxy filter, model, post-processing, suggestion |
| No examples vs examples in the prompt | Zero-shot vs few-shot |
| Stops Copilot using a file as context | Content exclusion |
| Blocks output matching public code | Public-code matching filter |
| Two limitations of the LLM | No live knowledge, training cut-off |
| Account type for scheduling | Personal Microsoft account (MSA) |

## Scoring the mock

On the Day 10 full mock, tag every miss with its skill area, then re-study the two lowest-scoring areas first. A miss on a flashcard is a signal to re-read that area's deep-dive, not to move on.
