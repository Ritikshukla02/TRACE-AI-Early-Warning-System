# BERTweet Model & My Contribution

## My Role in TRACE

My main responsibility in the TRACE project was to build the **comment-level risk classification component using BERTweet**.

The goal was to take an input comment and estimate how strongly it relates to different types of potentially harmful content. The model output was then saved in a structured format so that other components of TRACE could use it for further behavioral analysis.

---

## What the Model Predicts

The BERTweet model was fine-tuned to analyze comments across **eight risk categories**:

* Bullying
* Coercion
* Grooming
* Hate
* Sextortion
* Sexual
* Threat
* Toxicity

Instead of returning only one category, the output contains a score for each category. This preserves more information about the comment when it is passed to the next stage of the system.

---

## Training Setup

The model was trained for **5 epochs**, with the best checkpoint selected using **Macro F1** on the evaluation data.

| Training Parameter    |       Value |
| --------------------- | ----------: |
| Learning Rate         |      `2e-5` |
| Training Batch Size   |        `16` |
| Evaluation Batch Size |        `16` |
| Number of Epochs      |         `5` |
| Weight Decay          |      `0.01` |
| Evaluation            | Every epoch |
| Checkpoint Saving     | Every epoch |
| Best Model Metric     |    Macro F1 |

Using Macro F1 for model selection was useful because performance across all risk categories mattered, rather than focusing only on the most common category.

---

## From Model Prediction to JSONL

After inference, the prediction for each input was stored in **JSONL (JSON Lines)** format.

Each record contains:

* `sender_id` : identifier associated with the prediction
* Probability scores for all eight risk categories
* `risk-score` : overall risk value used in the TRACE pipeline

Example:

```json
{
  "bert_analysis": {
    "sender_id": "pred_005",
    "bullying": 0.0342,
    "coercion": 0.0029,
    "grooming": 0.0022,
    "hate": 0.0074,
    "sextortion": 0.0040,
    "sexual": 0.0021,
    "threat": 0.7453,
    "toxicity": 0.2019,
    "risk-score": 0.7637
  }
}
```

In this example, **threat** receives the highest category score.

---

## Passing the Output to the Team

My part of the pipeline can be summarized as:

**Input Comment → BERTweet → 8 Risk Scores → Structured JSONL Output**

After generating the predictions, I saved them in a JSONL file and shared the structured output with another team member for integration into the broader TRACE pipeline.

This separation allowed the BERTweet classifier to work as an independent comment-analysis component while the remaining system handled behavioral context, reasoning, and visualization.

