# How the TRACE System Works

## Putting the Components Together

TRACE was built as an end-to-end pipeline where each component handles a different part of the analysis.

The overall flow is:

**Comments → BERTweet → Risk Scores → Behavioral Analysis with Gemma → Streamlit Dashboard → Human Review**

![System Worflow](images/system_workflow.png)

---

## 1. Comment-Level Risk Analysis

The process starts with individual comments.

BERTweet analyzes each comment across eight risk categories and produces structured probability scores. These predictions are stored in JSONL format and passed to the next stage of the system.

The detailed BERTweet implementation is explained in [BERTweet Model & My Contribution](bertweet_model.md).

---

## 2. Looking Beyond a Single Comment

A single prediction does not always provide enough context to understand potentially concerning behavior.

The next stage therefore looks at broader information such as:

* Previous interactions from the sender
* Activity across different accounts
* Changes in behavior over time
* Repeated or escalating risk patterns

This allows TRACE to move from **comment-level classification** toward **behavioral-pattern analysis**.

---

## 3. Behavioral Analysis with Gemma

Gemma is used to analyze the broader behavioral context together with the available risk information.

Instead of treating each comment independently, this stage helps identify whether multiple interactions together indicate a potentially concerning pattern or escalation.

---

## 4. Presenting the Evidence

The results are presented through a **Streamlit dashboard**.

The dashboard brings the available information together so that an analyst can review:

* Detected risk signals
* Relevant behavioral context
* Supporting evidence
* System recommendations

[PASTE DASHBOARD IMAGE HERE]

---

## 5. Human Review

TRACE does not automatically make enforcement decisions.

The system acts as an **early-warning and decision-support tool**, while the final decision remains with the human analyst.

This keeps human judgment involved when dealing with sensitive and potentially high-impact cases.

---

## 🔄 Complete Flow

The complete TRACE pipeline can be summarized as:

**Comment Analysis → Risk Classification → Behavioral Context → Evidence Presentation → Human Decision**

The main strength of this design is that it does not rely on a single model or a single comment. Different components contribute different information before the case reaches the human reviewer.

