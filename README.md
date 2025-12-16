# clip-semantic-risk-analysis


This project performs **zero-shot harmful content analysis** on images using
OpenAI's CLIP model.

Instead of using explicit class labels (e.g. weapon, violence),
the system infers **potential harm** via **relative semantic similarity**
between risk-related and safety-related concepts.

## 🔍 Method
- Vision–Language Model: CLIP (ViT-B/32)
- No training
- No hard labels
- Context-aware risk estimation

## 🧠 Decision Logic
Images are evaluated by comparing:
- Risk-related semantic similarity
- Safety-related semantic similarity

The final decision is based on the **relative margin**, allowing:
- SAFE
- POTENTIALLY HARMFUL
- AMBIGUOUS / CONTEXT-DEPENDENT

## ▶️ Run
```bash
pip install -r requirements.txt
python main.py
