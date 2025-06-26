# Offline AI Tutor for Indian Students

## Overview
This project enables you to build an **offline AI tutor app** for Indian students (class 6 to postgraduate, all streams) using TinyLLaMA and llama.cpp. It covers dataset generation, prompt engineering, SQLite/JSON storage, (optional) LoRA fine-tuning, and mobile integration.

---

## 1. Generate Indian Curriculum Q&A Dataset

- **Edit or expand `prompts.txt`** with 500+ questions from Physics, Polity, History, Chemistry, Biology, Commerce, etc.
- Run:

```bash
python generate_qa_dataset.py
```
- Outputs:
  - `qa_dataset.json` (all Q&A pairs)
  - `qa_dataset.db` (SQLite for mobile)

---

## 2. Convert to Alpaca Format (for LoRA/QLoRA Fine-Tuning)

```bash
python generate_alpaca_dataset.py
```
- Output: `alpaca_indian_qa.json`

---

## 3. Export to SQLite (if needed)

```bash
python save_sqllite.py
```
- Output: `qa_dataset.db`

---

## 4. (Optional) Fine-Tune with LoRA/QLoRA

- Use HuggingFace `transformers`, `peft`, and your `alpaca_indian_qa.json`.
- See HuggingFace QLoRA/PEFT docs for full script. After training, export back to GGUF using llama.cpp tools.

---

## 5. Mobile Integration

- Use `qa_dataset.db` or `qa_dataset.json` in your React Native/Capacitor app.
- For full offline LLM inference, use [llama.cpp WASM build](https://github.com/ggerganov/llama.cpp/tree/master/examples/wasm) and [react-native-wasm](https://github.com/kripod/react-native-wasm).

---

## 6. Ethical Use & Constraints

- Entire system works offline. No cloud APIs.
- Data is for learning, not cheating.
- Use `AsyncStorage` or `SQLite` for mobile storage.

---

## File Descriptions
- `generate_qa_dataset.py`: Main script to generate Q&A pairs using TinyLLaMA.
- `generate_alpaca_dataset.py`: Converts Q&A to Alpaca format for fine-tuning.
- `save_sqllite.py`: Exports Q&A pairs to SQLite.
- `prompts.txt`: (Create this file) List of questions/prompts, one per line.
- `model.py`: Reserved for future inference/mobile code.

---

## Example Prompt (in prompts.txt)
```
Explain Bhakti Movement in simple Hindi.
Solve this JEE Physics problem: A ball is thrown vertically upwards with a speed of 20 m/s. Find the maximum height.
What is the difference between Lok Sabha and Rajya Sabha?
```

---

## Contact
For help, open an issue or contact the maintainer. # replit
