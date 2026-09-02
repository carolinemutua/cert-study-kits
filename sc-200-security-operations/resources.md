---
title: Resources
layout: default
parent: SC-200 Security Operations Analyst
nav_order: 4
---

# Resources

Every link on this page was checked and returned a successful response at the time of writing. Microsoft reorganises documentation regularly, so if a link fails, search the title from the [Microsoft Learn](https://learn.microsoft.com) home page rather than assuming the content is gone.

## Official, and authoritative

Start here. The study guide is the only document that defines what is scored.

| Resource | Why it matters |
| --- | --- |
| [SC-200 exam page and study guide](https://learn.microsoft.com/en-us/credentials/certifications/exams/sc-200/) | The skills measured list. Check the revision date against the one this kit was written from, which is 16 April 2026. |
| [Official practice assessment](https://learn.microsoft.com/en-us/credentials/certifications/exams/sc-200/practice/assessment?assessment-type=practice&assessmentId=59) | Free, and the closest available match to real question style. The readiness bar in the plan is based on this, not on third-party banks. |
| [Exam sandbox](https://aka.ms/examdemo) | Familiarisation with the exam interface, so no time is lost to the mechanics on the day. |
| [SC-200 training paths on Microsoft Learn](https://learn.microsoft.com/en-us/training/browse/?terms=SC-200) | The structured modules that map to the objectives, used as the reading step in the daily rhythm. |
| [Exam Readiness Zone](https://learn.microsoft.com/en-us/shows/exam-readiness-zone/) | Short videos walking through what each skill area actually tests. |

## Product documentation

Reference material for the labs. These are the pages to open alongside a portal, not to read cover to cover.

| Resource | Covers |
| --- | --- |
| [Microsoft Sentinel documentation](https://learn.microsoft.com/en-us/azure/sentinel/) | Connectors, analytics rules, automation, workbooks, hunting, and the data lake |
| [Microsoft Defender XDR documentation](https://learn.microsoft.com/en-us/defender-xdr/) | Incidents, advanced hunting, custom detection rules, and attack disruption |
| [Microsoft Defender for Cloud documentation](https://learn.microsoft.com/en-us/azure/defender-for-cloud/) | Workload protection alerts, which Domain 2 tests by product ownership |
| [Kusto Query Language quick reference](https://learn.microsoft.com/en-us/kusto/query/kql-quick-reference) | The single most useful page in this list, given how far Kusto reaches across all three domains |

## Community and practice

Useful, but secondary. Community content ages quickly against a revised objectives list, so check the publication date before trusting any of it, and prefer material from the last twelve months.

| Resource | Notes |
| --- | --- |
| [Azure Sentinel hunting query library on GitHub](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries) | Community-maintained and Microsoft-hosted. Excellent for reading real queries and learning idiomatic Kusto. |
| [John Savill's Technical Training](https://www.youtube.com/@NTFAQGuy) | Deep Azure and security explanations. Strong on the underlying platform concepts rather than exam cramming. |
| [A Guide To Cloud](https://www.youtube.com/@AGuideToCloud) | Security certification walkthroughs and lab demonstrations. |
| [Inside Cloud and Security](https://www.youtube.com/@insidecloudandsecurity) | Exam-focused security content, including objective walkthroughs. |
| [r/AzureCertification](https://www.reddit.com/r/AzureCertification/) | Recent sitting reports, which are useful for calibrating difficulty and spotting objective drift. |

## A note on practice exam providers

Paid question banks vary widely in quality, and some sites host material harvested from live exams. Using harvested content breaches the exam agreement and can invalidate a certification, so it is worth being deliberate here: use the official practice assessment as the scoring benchmark, and treat any third-party bank only as extra drilling on format, never as a source of truth on content.

## Building the lab

The labs in this kit assume a tenant that is safe to modify, with security licensing that includes Sentinel and the Defender products. Options that do not require a production environment:

1. A Microsoft 365 developer or trial tenant, paired with an Azure subscription for the Sentinel workspace.
2. An Azure free account, which covers the Sentinel side, with the Defender portals explored in whatever tenant is already available.

Ingest a small volume deliberately. Sentinel bills on data ingested, so a data collection rule that collects all security events from a noisy source can become expensive faster than expected. Scope the rule, watch the first day of ingestion, and adjust.
