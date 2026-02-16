# LLMwidGoogleCollab

---

# Ollama-Colab API Bridge 🚀

A lightweight solution to bypass LLM token limits and subscription costs by hosting a local API server on Google Colab's free tier.

## 📖 Overview

In the era of **Vibe Coding**, hitting token limits on commercial LLM providers can stall productivity. This project provides a "Zero-Cost" alternative using **Ollama** and **Google Colab**.

By leveraging the **Tesla T4 GPU** (15GB VRAM) provided in the Colab free tier, we can host Small Language Models (SLMs) and expose them via a local REST API endpoint for development, testing RAG pipelines, or automation scripts.

## ✨ Key Features

* **Zero Cost:** No per-token billing or monthly subscriptions.
* **Privacy-First:** Your prompts and data remain within your temporary Colab instance.
* **Low Latency:** High-speed `localhost` API interaction within the same virtual environment.
* **Open Source:** Powered by Ollama and the latest open-source models (Llama 3.2, Phi-4, etc.).

## 🛠️ Technical Stack

* **Infrastructure:** Google Colab (Free Tier - Tesla T4 GPU).
* **Engine:** [Ollama](https://ollama.com/) (Linux binary).
* **Models:** Optimized for <4B parameters (e.g., `llama3.2:1b`, `phi4-mini`).
* **Interface:** Python `requests` library (OpenAI-compatible API structure).

## 🚀 Quick Start

1. **Open the Notebook:** Upload the `.ipynb` file to your Google Drive or open it directly in Colab.
2. **Change Runtime:** Navigate to `Runtime` > `Change runtime type` and select **T4 GPU**.
3. **Install & Run:** Execute the cells in order to:
* Install system dependencies (`zstd`).
* Initialize the Ollama background daemon.
* Pull your desired model.
* Start making local API calls.



## 📝 Example API Usage

Once the server is running, you can interact with the LLM using standard Python:

```python
import requests

payload = {
    "model": "llama3.2:1b",
    "prompt": "What is the benefit of using SLMs for networking automation?",
    "stream": False
}

response = requests.post("http://localhost:11434/api/generate", json=payload)
print(response.json()['response'])

```

## ⚠️ Important Considerations

* **Ephemeral Storage:** Colab instances are temporary. You will need to re-run the installation and model pull each time you connect to a new runtime.
* **VRAM Limits:** Stick to models under 4B parameters to avoid "Out of Memory" (OOM) errors on the 15GB T4 GPU.


