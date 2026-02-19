# Roku Support Bot Evaluation  
Conversation-Level Performance Analysis (30 Case Study Review)

---

## Overview

This project evaluates the performance of the Roku Support Bot through structured analysis of 30 real support conversations across multiple categories:

- Connectivity & Setup
- Playback & App Issues
- Account & Billing
- Remote & Hardware
- Ambiguous Queries
- Advanced / Edge Cases

The objective was to assess containment quality, escalation behavior, intent accuracy, and customer satisfaction (CSAT), and to identify patterns driving negative user experiences.

---

# 📈 Metrics Summary

| Metric | Result |
|--------|--------|
| **Containment Rate** | 80% |
| **Intent Accuracy** | 93.3% |
| **Recontact Rate** * | 6.7% |
| **Positive CSAT** | 76.7% |
| **Negative CSAT** | 20% |

---

## Metric Definitions

**Containment Rate**  
Percentage of conversations resolved without human escalation.

**Intent Accuracy**  
Percentage of conversations where the bot correctly interpreted user intent.

**Recontact Rate (Proxy)**  
Estimated based on conversations where intent was not accurate (assumption: unresolved intent increases likelihood of repeat contact).

**CSAT Score Distribution**
- 1 = Positive
- 0 = Neutral
- -1 = Negative

---

## Dataset Structure

Each conversation was evaluated using the following framework:

| Column | Description |
|--------|------------|
| Question Category | High-level issue classification |
| User Question | Original user query |
| Response | Full bot response flow |
| Escalated? | Whether case was escalated to human |
| Intent? | Accurate / Not Accurate / Mixed |
| CSAT Score | -1 (Negative), 0 (Neutral), 1 (Positive) |
| CSAT Label | Sentiment classification |
| Open Codes | Behavioral observations |
| Axial Codes | Thematic grouping |

---

## Qualitative Coding Methodology

### Open → Axial Coding Framework

Each conversation was first labeled using open coding (granular behavioral observations).  
These open codes were then grouped into higher-level axial themes.

### LLM-Assisted Thematic Clustering

An LLM was used to assist in clustering open codes into axial categories.  
The model helped identify pattern similarity and semantic grouping, while final category definitions were manually reviewed and validated.

| Open Code | Axial Code |
|-----------|------------|
| Resolved by providing steps and link to documentation | Self-Service Resolution via Procedural Guidance |
| Resolved by providing steps | Self-Service Resolution via Procedural Guidance |
| Resolved but continued providing steps after user signaled satisfaction | Over-Communication / Redundant Assistance |
| Resolved by providing steps; asked good questions despite ambiguity | Clarification-Driven Successful Resolution |
| Unresolved due to user ambiguity and escalated to human | Escalation Due to User Ambiguity |
| Unresolved due to issue complexity and escalated to human | Escalation Due to Technical Complexity |
| Unresolved due to issue severity and escalated to human | Escalation Due to Severity / Risk |
| Resolved, escalated based on explicit user request | User-Initiated Escalation |

This hybrid approach (manual + LLM-assisted clustering) improved consistency while preserving human judgment.

---

## Key Findings

<img width="893" height="614" alt="image" src="https://github.com/user-attachments/assets/b57431b9-c292-4317-a7c4-da6ef82f9772" />


### 📌 Escalation Patterns

- 20% of cases escalated
- 83% of escalations occurred within ≤ 2 turns
- Majority of escalations driven by:
  - User ambiguity
  - Technical complexity
- Escalated cases disproportionately received negative CSAT

---

### 📌 CSAT Correlation Insights

Negative CSAT was strongly associated with:

- Early escalation
- Low containment
- Unresolved ambiguity
- High-risk technical flows (factory reset / recovery mode)
- Repetitive troubleshooting loops

---

### 📌 Over-Communication Pattern

<img width="361" height="333" alt="Screenshot 2026-02-19 155643" src="https://github.com/user-attachments/assets/6eba7bd2-56a4-489d-a183-cae1d7f6e61e" />


In one connectivity case:

User:
> "no im good"

Bot:
> Continued suggesting additional troubleshooting steps

CSAT Outcome: Neutral (0) (+1 for accurate resolution -1 for looping)

Open Code:
- Continued guidance after user signaled satisfaction

Axial Code:
- Over-Communication / Redundant Assistance

This suggests the absence of a resolution-state detection mechanism.

---

### 📌 Successful Resolution Pattern

High CSAT conversations typically included:

- Clarification before action
- Structured procedural steps
- Clear, confident tone
- Links to relevant documentation
- Escalation only when explicitly requested

Axial Code:
- Clarification-Driven Successful Resolution

---

## Failure Mode Themes

### 1️⃣ Escalation Due to User Ambiguity
- Vague or emotional queries
- Limited probing before escalation
- Negative CSAT impact

### 2️⃣ Escalation Due to Technical Complexity
- High-risk recovery/reset scenarios
- User hesitation due to data loss risk
- Escalation following trust friction

### 3️⃣ Over-Communication
- Continued troubleshooting after user satisfaction signal
- Redundant assistance loops
- Neutral or negative CSAT

---

## Recommendations

### 1️⃣ Increase Escalation Threshold
Test raising minimum turn threshold (2 → 3 turns) before escalation to improve containment and context collection.

### 2️⃣ Add Resolution-State Detection
Stop troubleshooting loops when user signals completion or satisfaction.

### 3️⃣ Improve Ambiguity Handling
Introduce structured clarification prompts before escalation.

### 4️⃣ Improve Confidence Framing in Complex Cases
Provide transparent risk communication and guided reassurance before suggesting deep resets.

---


## Tools Used

- Manual conversation review
- Thematic coding (Open → Axial)
- Spreadsheet-based metric tracking
- CSAT correlation analysis

---

# Methodological Assumptions & Limitations

*Since this was a personal evaluation project, several assumptions were made:

### 1️⃣ CSAT Scoring

- CSAT labels were inferred manually based on conversation tone and resolution quality.
- Scores may reflect evaluator bias.
- No access to actual post-interaction user survey data.

### 2️⃣ Recontact Rate

- Estimated using non-accurate intent cases as a proxy.
- Assumes unresolved intent increases likelihood of repeat contact.
- True recontact data was not available.

### 3️⃣ Containment & Escalation Context

- Escalation classification was based solely on visible transcript behavior.
- No backend system signals were available.

### 4️⃣ Sample Size

- 30 conversations.
- Findings directional, not statistically significant.

---

## Why This Still Holds Value

Despite limitations, the analysis provides:

- Structured evaluation framework
- Repeatable scoring methodology
- Clear behavioral pattern identification
- Hypothesis generation for product experimentation
- Escalation timing insights tied to CSAT outcomes

The goal was not statistical certainty, but systematic pattern detection and actionable product recommendations.

---

## Future Improvements

- Incorporate real CSAT survey data
- Expand sample size to 100+ conversations
- Validate recontact with CRM data
- Introduce inter-rater reliability scoring
- Run quantitative significance testing

