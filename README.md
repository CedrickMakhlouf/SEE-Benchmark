(MSc AI Thesis)
# SEE-Benchmark

**Screen Explanation Evaluation (SEE)** is the first open-source benchmark designed to evaluate how well Vision-Language Models (VLMs) can generate screen descriptions for visually impaired users. It enables systematic, reproducible comparisons of model and prompt combinations using annotated Dutch desktop screenshots and LLM-based evaluation.

## 📌 Purpose

Sighted users understand screen layouts through top-down visual cues. Visually impaired users rely on screen readers, which present interfaces linearly and depend on developer metadata. SEE-Benchmark closes this gap by enabling intelligent, top-down screen summaries using VLMs.

## 🧠 Features

- **100 annotated Dutch desktop screenshots** from real-world government, work, and daily-use applications.
- Each sample includes:
  - `reference_description`: Human-written 5–7 sentence description.
  - `must_include`: List of essential screen elements for usability.
- **LLM-as-a-Judge scoring** using G-Eval (GPT-4o) assessing:
  - Reference Coverage (semantic alignment with the reference)
  - Must-Include Coverage (inclusion of essential elements)

## 🔐 API Key Setup

Create a `.env` file in the project root with your credentials:

```

TOGETHER\_API\_KEY=your-together-key
OPENAI\_API\_KEY=your-openai-key

```

These keys are used for Together API (model inference) and OpenAI API (evaluation via GPT-4o).

## 📓 Notebooks

### 1. `generate_descriptions.ipynb`  
Runs a selected Vision-Language Model (e.g. LLaMA 4) on all 100 annotated screenshots using a chosen prompt to generate Dutch screen descriptions.

**Workflow:**
- Loads the model via the Together API
- Encodes each screenshot and sends it along with the selected prompt
- Stores all generated outputs in a `.xlsx` file in the `results/` directory  
  Example:  
  `results/meta-llama_Llama-4-Maverick__feedback__20250629_1215.xlsx`

**You control:**
- `MODEL_NAME`
- `PROMPT_VERSION`
- `PROMPT_TEXT`

### 2. `evaluate_descriptions.ipynb`  
Evaluates the screen descriptions using GPT-4o and the GEval method (via DeepEval). Each output is compared against the annotated reference and must-include list.

**Workflow:**
- Loads the `.xlsx` output from the `results/` directory
- Automatically extracts the model and prompt from the filename
- Computes:
  - Reference Coverage
  - Must-Include Coverage
- Prints per-image results and an overall summary
- Saves the evaluation output as a `__eval.csv` file in the same `results/` folder  
  Example:  
  `results/meta-llama_Llama-4-Maverick__feedback__20250629_1215__eval.csv`

## 📁 Output Structure

```

/results/             ← Generated `.xlsx` description files
/outputs/             ← Optional: JSON versions of model outputs (not required)
/screen\_annotations/  ← 100 annotated screenshot descriptions + metadata

````
