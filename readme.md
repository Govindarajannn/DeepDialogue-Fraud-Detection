# DeepDialogue Fraud Detection

An AI-powered phone call fraud detection system that runs entirely locally to protect user privacy while achieving near-perfect classification accuracy.

## Problem Statement

With the rapid development of AI tools, fraudsters are becoming increasingly sophisticated, often leveraging machine learning techniques to evade detection. While apps like Truecaller provide caller identification and scam alerts, there's a critical gap in real-time conversation analysis during active calls.

This system serves as a second line of defense, helping users identify fraudulent calls during the conversation itself. Unlike cloud-based solutions, our approach runs entirely locally, addressing privacy and data security concerns that have prevented widespread adoption of similar systems.

## Motivation

Despite phone scams being a critical problem affecting millions globally, there is surprisingly little research in this domain. The lack of accessible, privacy-preserving detection tools motivated this project.

## Approach

### Dataset Generation
- Generated a synthetic dataset using Groq's Llama 3.1-8B model
- Carefully crafted prompts to create realistic dialogue scenarios
- Covered various scam tactics and legitimate call patterns
- Total dataset: 1,800 samples

### Model Fine-Tuning
- Base model: Qwen2.5-0.5B-Instruct
- Technique: LoRA (Low-Rank Adaptation)
- Training samples: 1,800 dialogues
- Demonstrates that small models can achieve production-grade performance on specialized tasks with quality fine-tuning

## Results

### 1. Accuracy Improvement
- **Base model:** 56.67% (barely better than random guessing)
- **Fine-tuned model:** 95.56% (near-perfect classification)
- **Impact:** Correctly classifies 39 more samples out of 180

### 2. Precision: Massive Reduction in False Alarms
- **Base model:** 54.11% (almost half of scam predictions are wrong)
- **Fine-tuned model:** 98.81% (almost all scam predictions are correct)
- **Impact:** False positives dropped from 67 → 1 (98.5% reduction)
- **Real-world benefit:** Users won't be unnecessarily alarmed by legitimate calls

### 3. Recall: Maintained High Scam Detection
- **Base model:** 87.78% (catches most scams but at a cost)
- **Fine-tuned model:** 92.22% (catches even more scams)
- **Impact:** False negatives reduced from 11 → 7 (36% reduction)
- **Real-world benefit:** Better protection against actual scams

### 4. F1 Score: Balanced Excellence
- **Base model:** 66.95% (poor balance between precision and recall)
- **Fine-tuned model:** 95.40% (excellent balance)
- **Meaning:** The fine-tuned model excels at both identifying scams AND avoiding false alarms

### 5. Response Quality
- **Base model:** 31 invalid responses (17.2%)
- **Fine-tuned model:** 12 invalid responses (6.7%)
- **Impact:** 61% reduction in invalid responses

## Key Features

- **Privacy-First:** Runs entirely locally, ensuring user data remains secure
- **High Accuracy:** 95.56% classification accuracy
- **Low False Positives:** 98.81% precision means fewer false alarms
- **Lightweight:** Based on a 0.5B parameter model, suitable for edge devices
- **Real-Time:** Designed for live call analysis

## Installation

```bash
# Clone the repository
git clone https://github.com/Govindarajannn/DeepDialogue-Fraud-Detection.git
cd DeepDialogue-Fraud-Detection

# Install dependencies
pip install -r requirements.txt
```

## Requirements

See `requirements.txt` for full dependencies. Key packages include:
- transformers
- datasets
- peft
- torch
- groq

## Technical Details

This project demonstrates that specialized small language models can outperform larger general-purpose models on domain-specific tasks when properly fine-tuned with high-quality data.

## License

[Add your license here]

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

**Note:** This is a research project demonstrating the feasibility of local, privacy-preserving fraud detection. Always exercise caution with suspicious calls and report fraud to relevant authorities.