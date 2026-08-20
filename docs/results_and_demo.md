# Results & Demo

## What We Built

During the hackathon, our team developed a working end-to-end prototype of TRACE that connected:

**BERTweet Classification → Behavioral Analysis → Evidence & Recommendations → Human Review**

The BERTweet component successfully generated structured risk predictions across eight categories, which could then be passed to the remaining parts of the system for further analysis.

---

## Example Classification Output

For every analyzed input, the BERTweet component generated category-level probability scores along with an overall risk score.

[PASTE BERT OUTPUT IMAGE HERE]

This structured output made it possible to pass the model predictions between different components of the system without coupling them directly together.

---

## Final Prototype

The final prototype brings the analysis together through a Streamlit dashboard, allowing the available risk signals, behavioral context, and supporting evidence to be reviewed in one place.

[PASTE FINAL DASHBOARD IMAGE HERE]

---

## 🎥 See TRACE in Action

The complete prototype and workflow can be seen in the project demonstration:

**[▶️ Watch the TRACE Demo on YouTube](YOUR_YOUTUBE_LINK_HERE)**

The demo shows how TRACE moves from analyzing online interactions to presenting the available evidence for human review.

---

## Hackathon Result

TRACE reached the **final round of the USAII Global AI Hackathon 2026** in the Graduate & Doctoral Track.

More importantly, the prototype demonstrated how NLP classification and behavioral context can be combined instead of relying only on isolated comment moderation.

