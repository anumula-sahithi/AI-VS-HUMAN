# AI vs Human Content Detector

A multi-modal system that detects whether **text, audio, images, or video** content is AI-generated or human-generated.  

It provides:  
- **Probability Score** (0.0–1.0) indicating likelihood of AI generation  
- **Confidence Level** (Low / Medium / High)  
- **Short, human-readable explanation** of the decision  
- **Performance Requirement**: Average processing time under 60 seconds  

---

## Features
- **Text Detection** → Hugging Face AI detector + GPT-2 perplexity  
- **Audio Detection** → CNN + RNN classifier on mel spectrogram slices  
- **Image Detection** → Pretrained Hugging Face classifier with explanation  
- **Video Detection** → Frame sampling + aggregated image classification  

---
### Deployment Link: 
```
https://huggingface.co/spaces/satyahaha/B2B
```
## Installation & Setup

### 1. Clone the repository
```bash
git clone https://github.com/OSDG-IIITH/build2break-25-breakittt.git
```

### 2.Set up API Keys

This project requires two API keys:

- **Hugging Face Token (`HF_TOKEN`)** → [Get your token here](https://huggingface.co/settings/tokens)  
- **Groq API Key (`GROQ_API_KEY`)** → [Get your key here](https://console.groq.com/)  
### On Google Colab
"Add New Secret" in Secrets Tab and add this in your code:
```
from google.colab import userdata
import os

os.environ["HF_TOKEN"] = userdata.get("HF_TOKEN")
os.environ["GROQ_API_KEY"] = userdata.get("GROQ_API_KEY")
```

#### On Linux / macOS / WSL
```bash
export HF_TOKEN="your_hf_token_here"
export GROQ_API_KEY="your_groq_api_key_here"
```

### On Windows (PowerShell)
```
setx HF_TOKEN "your_hf_token_here"
setx GROQ_API_KEY "your_groq_api_key_here"
```

---

## Running Locally (Non-Deployment Mode)

This project provides **4 Jupyter/Colab notebooks** — one for each type of detection:  

- `Text.ipynb` → Detects AI vs Human text  
- `Audio.ipynb` → Detects AI vs Human audio  
- `Image.ipynb` → Detects AI vs Human images  
- `Video.ipynb` → Detects AI vs Human videos  

### Instructions
1. Open the desired notebook (e.g., `Audio.ipynb`) in **Google Colab** or **Jupyter Notebook**. Just in case, if the git file does not open, kindly download the .ipynb file to run it  
2. Run the cells step by step.  
3. When prompted, the notebook will **ask you to choose a file from your local storage**.  
4. The notebook will process the file and return:  
   -  AI vs Human probability score  
   -  Confidence level (Low / Medium / High)  
   -  Short reasoning/explanation  

---

## Confidence Levels & Reasoning

Each notebook returns a **Confidence Level** to help you interpret results:

- **Low Confidence** — The result is **not reliable**. The tool is unsure, so the answer may be wrong.  
- **Medium Confidence** — The result is **probably correct**, but there is a chance it could be the opposite (AI could look human, and human could look AI).  
- **High Confidence** — The result is **very likely correct**, but it is still not 100% certain.  

### Reasoning
The tool checks **patterns in the content** (depending on the modality):  
- **Text** → writing patterns, perplexity, linguistic features  
- **Audio** → pitch, tone, spectrogram patterns  
- **Image** → textures, lighting, artifacts  
- **Video** → motion, lighting consistency, temporal coherence  

These can sometimes be affected by:  
- Editing / post-processing  
- Quality loss (compression, noise, blur)  
- AI tricks / adversarial generation  

Therefore, the result should always be treated as a **probability, not a guarantee**.  

---


# Deployment

This project can be run in:

Google Colab (Recommended) → Run interactively with no setup.
### Deployment Link:
```
https://huggingface.co/spaces/satyahaha/B2B
