---
title: Practice and flashcards
layout: default
parent: SC-200 Security Operations Analyst
nav_order: 3
---

# Practice and flashcards

A self-test bank for spaced recall. Answer from memory first, then check. Questions written by a candidate for a candidate are not exam questions, and no material here is drawn from the exam itself. For scored, representative questions use the [official practice assessment](https://learn.microsoft.com/en-us/credentials/certifications/exams/sc-200/practice/assessment?assessment-type=practice&assessmentId=59).

## How to use this page

Cover the answer column. Work one domain at a time, immediately after finishing the matching deep-dive. Anything missed goes on the weak-area list that drives Days 20 and 21 of the plan. Revisit a missed item after one day, then after three, then after a week.

---

## Domain 1: Manage a security operations environment

| Question | Answer |
| --- | --- |
| Which connector collects Windows security events, and what object controls what is collected? | The Windows Security Events connector through the Azure Monitor Agent. A data collection rule controls which events are gathered. |
| When would Windows Event Forwarding be chosen over the agent for Windows security events? | When agents cannot be deployed to every source host, so events are forwarded to a collector that is instrumented instead. |
| Which mechanism deploys Azure activity collection consistently across many subscriptions? | Azure Policy, which deploys the diagnostic settings automatically rather than requiring per-resource configuration. |
| What distinguishes a near real time analytics rule from a scheduled one? | A near real time rule runs continuously with a very short interval and is designed for low latency, and it carries tighter constraints on query complexity and lookback than a scheduled rule. |
| Which rule type is used to match ingested threat indicators against telemetry? | A threat intelligence analytics rule. |
| Where is a custom detection rule created in Defender XDR? | From a saved advanced hunting query, promoted to a custom detection rule. |
| What is the purpose of the MITRE ATT&CK view in Sentinel? | It maps active detections to attacker techniques, so coverage gaps become visible and can be prioritised. |
| Name the three retention tiers referenced by the objectives. | The analytics tier, the data lake tier, and the XDR tier. |
| What problem does SOC optimisation address? | It recommends changes to improve coverage or reduce cost, for example unused data being ingested or detections that have no data to run against. |
| What is the difference between an automation rule and a playbook in Sentinel? | An automation rule is the trigger and condition layer that decides when to act on an incident. A playbook is the Logic Apps workflow that performs the action. |
| Why set an automation level on a device group? | It controls how far automated investigation and remediation may go without analyst approval, which can be stricter for sensitive devices. |
| What does attack surface reduction configuration control? | Rules that block common attack behaviours on endpoints, such as scripts launching executables, independent of any specific detection. |

## Domain 2: Respond to security incidents

| Question | Answer |
| --- | --- |
| An alert concerns a risky OAuth application granted broad access to Microsoft 365 data. Which product owns it? | Defender for Cloud Apps. |
| An alert concerns a compromised on-premises identity showing suspicious directory activity. Which product owns it? | Defender for Identity. |
| An alert concerns a misconfigured or attacked cloud workload such as a virtual machine or container. Which product owns it? | Defender for Cloud, through its workload protections. |
| An alert concerns a malicious attachment delivered by email. Which product owns it? | Defender for Office 365. |
| What does automatic attack disruption do that ordinary automated investigation does not? | It intervenes mid-attack with high-confidence containment, for example disabling an account or isolating a device, to break the attack before the investigation completes. |
| What is the first thing to read on an incident, and why? | The incident graph, because it shows the correlated entities, the evidence, and the attack story in one view rather than as disconnected alerts. |
| Why link incidents rather than working them separately? | Multi-stage attacks surface as several incidents. Linking preserves the single attack narrative and prevents each part being closed as unrelated noise. |
| Which live response capability collects a forensic snapshot from a device? | Collecting an investigation package. |
| Where are pending and completed remediation actions reviewed? | The Action center. |
| Which Purview tool searches mailbox and site content for a keyword? | Content Search. |
| Which Purview tool answers who did what and when across Microsoft 365? | Audit. |
| What does the Microsoft Graph activity log add that the audit log does not? | A record of the API calls made against Microsoft Graph, which exposes programmatic access that user-level audit events do not describe. |
| When an assistant such as Security Copilot summarises an incident, what remains the analyst's job? | Validating the summary against the underlying evidence. The analyst stays accountable for the conclusion. |

## Domain 3: Perform threat hunting

| Question | Answer |
| --- | --- |
| Which table holds process execution and command line data? | `DeviceProcessEvents`. |
| Which table holds outbound and inbound network connections per device? | `DeviceNetworkEvents`. |
| Which table holds sign-in activity including logon type? | `IdentityLogonEvents`. |
| Which Sentinel table holds the classic Windows security event log? | `SecurityEvent`. |
| Which operator counts distinct values, and where would it be used in a lateral movement hunt? | `dcount`, used to count how many distinct devices a single account reached. |
| What is the difference between `has` and `contains` in a Kusto query? | `has` matches whole terms and is indexed, so it is much faster. `contains` matches any substring and is slower. Prefer `has` where the match is a whole term. |
| Which operator makes a string comparison case-insensitive? | `=~` for equality, and `!~` for inequality. |
| What does a bookmark in Sentinel hunting do? | It preserves an interesting result so it can be revisited and promoted into an investigation or incident. |
| Why run a Kusto job against the data lake tier rather than querying directly? | Long-range hunts span more data than an interactive query is intended to handle. The job tier is built for that volume and retention. |
| What is a summary rule table for? | It pre-aggregates high-volume data on a schedule, so hunts and detections query a smaller, cheaper table instead of raw events. |
| What does a hunting graph blast radius show? | What else an entity touched, and therefore how far a compromise could have spread from it. |
| A hunt finds activity no detection caught. What is the correct final step? | Promote the query to a detection rule, so the gap is closed permanently rather than depending on the hunt being repeated. |

---

## Rapid-recall flashcards

Numbers and one-line facts that are cheap to memorise and expensive to guess.

| Prompt | Recall |
| --- | --- |
| Passing score | 700 out of 1000 |
| Question count | Approximately 40 to 60 |
| Duration | Approximately 120 minutes |
| Domain 1 weight | 40 to 45 percent |
| Domain 2 weight | 35 to 40 percent |
| Domain 3 weight | 20 to 25 percent |
| Event ID for a failed Windows logon | 4625 |
| Event ID for Windows process creation | 4688 |
| Agent used for Syslog, CEF, and Windows events | The Azure Monitor Agent |
| Object defining what the agent collects | A data collection rule |
| Framework used for detection coverage analysis | MITRE ATT&CK |
| Sentinel component that runs the response workflow | A playbook, built on Logic Apps |
| Sentinel component that decides when to run it | An automation rule |

## Kusto drills

Write each of these from a blank editor. If an example has to be copied, the drill has not been passed yet.

1. List the ten devices with the most process executions in the last day.
2. Show failed sign-ins in the last seven days, grouped by account, sorted by count, showing only accounts with more than twenty failures.
3. Find every network connection to a specific IP address, and show which process initiated it.
4. Show accounts that signed in interactively to more than three distinct devices in the last day.
5. Count Graph API calls by response status code over the last day, to surface a spike in failures.
6. Take any one of the above and describe, without writing it, what the equivalent detection rule schedule and lookback should be.
