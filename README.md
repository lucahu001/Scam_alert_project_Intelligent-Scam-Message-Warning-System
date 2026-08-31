# AI Scam Alert — Intelligent Scam Message Warning System

Upload a screenshot of a suspicious conversation; the system classifies it as
fraudulent or legitimate.

## Background

Social-commerce platforms dominate online shopping in Taiwan, and fraud has
followed. Criminal Investigation Bureau data for October 2024 lists
online-shopping scams as the second most common fraud type at 14.41% of all
reported cases, behind only investment scams.

## Approach

We built and compared two architectures on a dataset of 210 labelled
screenshots (104 for training, 106 for testing):

**Pipeline A — OCR + fine-tuned model**
Tesseract OCR (`chi_tra`) extracts Traditional Chinese text from the
screenshot → text is structured into a labelled dataset → `gpt-3.5-turbo-1106`
is fine-tuned on it via the OpenAI fine-tuning API.

**Pipeline B — multimodal**
The image is base64-encoded and sent directly to `gpt-4o`. No text extraction
step.

## Results

| Model | Training set (104) | Test set (106) |
|---|---|---|
| gpt-4o (multimodal) | 89.42% | 77.36% |
| gpt-3.5-turbo (OCR + fine-tuned) | 70.19% | 37.74% |

OCR was the bottleneck. We tried upscaling images and applying grayscale
filters to reduce noise, but Traditional Chinese extraction remained
unreliable enough that errors upstream propagated through everything
downstream. Removing the OCR step entirely — Pipeline B — was what closed the
gap.

## An unresolved observation

Re-running the fine-tuned gpt-3.5-turbo on the same 104-sample training set
weeks later returned 94.17%, up from 70.19%, with no change to the training
data. We could not determine whether this reflected a change in the
underlying model or overfitting on our side. We are reporting it as
unresolved rather than quoting the higher figure.

## Running it

Requirements:
- `openai`, `pytesseract`, `pandas`, `natsort`, `Pillow`
- Tesseract OCR engine with the Traditional Chinese pack
  (`tesseract-ocr`, `tesseract-ocr-chi-tra`)
- An OpenAI API key in the environment:

```bash
export OPENAI_API_KEY="your-key-here"
```

The notebook is written for Google Colab and mounts Google Drive for the
image dataset. Dataset images follow the naming convention
`詐騙對話-XX.jpg` (scam) and `正常對話-XX.jpg` (normal); ground-truth labels
are parsed from the filename.

Note: the fine-tuned model ID in the notebook
(`ft:gpt-3.5-turbo-1106:ici::BdSO0syF`) belongs to the original project
account and is not accessible to others. Pipeline B (gpt-4o) runs with any
valid API key.

## Team

| | |
|---|---|
| 黃天慧 Alani | Project manager |
| 胡楚逸 Luca | Development |
| 黃芊婷 Patricia | Development |
| 黃晟恩 Andy | Poster design |

Supervised by Professor Pien Chung-pei, National Chengchi University.
