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

