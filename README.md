# Colab-Free-PDF-Translator
A robust, crash-proof automated pipeline for translating complex PDFs (like WSJ) on Google Colab Free Tier using BabelDOC &amp; Ollama. (稳健、防崩溃的自动化 PDF 翻译流水线，专为 Colab 免费版优化)
# 🚀 Colab Free PDF Translator (Optimized for WSJ/Financial Docs)

> **The Problem:** Translating complex, layout-heavy PDFs (like *The Wall Street Journal*) on Google Colab's Free Tier (T4 GPU) is painful. Users constantly face OOM (Out of Memory) errors, "Infinite Loop" crashes on dirty data, and session timeouts.
>
> **The Solution:** This project provides a "bulletproof" wrapper around [BabelDOC](https://github.com/funstory-ai/BabelDOC) and [Ollama](https://ollama.com/). It introduces a "Relay Tactics" approach to translate large documents in batches, ensuring the T4 GPU never crashes.

## ✨ Key Features

* **🛡️ Crash-Proof Patch**: Automatically injects a `Timeout/Retry` mechanism into BabelDOC's source code. If a complex table stalls the LLM, it skips instead of freezing the entire session.
* **🧹 Auto-Memory Cleaning**: Implements a "Relay" strategy. It kills and restarts the Ollama server every 5 pages to release GPU VRAM (The "5-Page Rule").
* **💎 Custom 32k Context Model**: Automatically configures a Google `TranslateGemma-4B` model with a 32k context window and safety parameters (`repeat_penalty`) to handle long financial texts without hallucinations.
* **📂 Auto-Renaming**: Saves output files as `Part_1-5.pdf`, `Part_6-10.pdf`, etc., preventing overwrite accidents.

## 🛠️ Usage

1.  Open the Notebook in Google Colab (Select **T4 GPU** runtime).
2.  Run **Step 1** to install dependencies and apply the source code patch.
3.  Restart the Session (`Runtime` -> `Restart Session`).
4.  Run **Step 2** to warm up the Ollama engine.
5.  Run **Step 3**, upload your PDF, and wait for the results.

## ⚠️ Notes for Free Tier Users
* **Do not** try to translate 20+ pages in one go. The script is configured to process batches of 5 pages to stay within the 16GB VRAM limit.
* **Download immediately**: Colab files are temporary. Download your `Part_X.pdf` files as soon as they appear.

## Credits
Built upon the amazing work of [BabelDOC](https://github.com/funstory-ai/BabelDOC).
