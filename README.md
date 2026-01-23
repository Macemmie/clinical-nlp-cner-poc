# clinical-nlp-cner-poc

A Clinical NLP pipeline for extracting structured information from free-text medical notes using Clinical Named Entity Recognition (CNER).

---

## Overview

Clinical records are often stored as unstructured narrative text, which limits their direct use in data-driven analysis and AI systems. This project demonstrates a focused, end-to-end pipeline for converting free-text clinical notes into structured, machine-readable data using a pre-trained transformer-based CNER model.

The project is intentionally scoped as a proof of concept and emphasises clarity, reproducibility, and responsible handling of clinical text.

---

## Pipeline Summary

The pipeline follows these steps:

1. **Data loading and filtering**  
   Load a public, de-identified clinical text dataset and select paediatric-related notes.

2. **Text preparation**  
   Retain original clinical language while removing incomplete or empty records.

3. **Clinical Named Entity Recognition (CNER)**  
   Apply a pre-trained transformer-based NER model to extract clinical entities.

4. **Entity post-processing**  
   Merge subword tokens and standardise entity labels into clinical categories:
   - PROBLEM  
   - TEST  
   - TREATMENT  

5. **Structured data creation**  
   Convert extracted entities into:
   - a long-format table (one entity per row), and  
   - a wide-format table (entities grouped by note and category).

6. **Human-in-the-loop (HITL) review**  
   Generate a brief review template to illustrate how clinician or domain-expert feedback can be incorporated.

7. **Ethics and limitations reflection**  
   Document ethical considerations, known limitations, and potential future extensions.

---

## Dataset

This project uses the **MTSamples medical transcription dataset**, available publicly via Kaggle.

The dataset is **not redistributed** in this repository.  
Please obtain it directly from the original source:

- https://www.kaggle.com/datasets/louiscia/transcription-samples-mtsamples

All processing is performed on de-identified clinical text.

---

## Model

- **Model:** `nlpie/clinical-distilbert-i2b2-2010`
- **Type:** Pre-trained transformer-based Clinical NER model
- **Training source:** i2b2 clinical concept extraction tasks

The model is used **without fine-tuning** to demonstrate out-of-the-box clinical entity extraction.

---

## Outputs

The pipeline produces the following artefacts:

- `entities_long.csv`  
  Long-format table containing one row per extracted entity with offsets and confidence scores.

- `entities_wide.csv`  
  Wide-format table grouping entities by clinical note and category.

- `hitl_review_log.csv`  
  Human-in-the-loop review template with fields intended to be completed by a clinician or qualified domain expert.

---

## Human-in-the-Loop (HITL)

Automated extraction outputs should not be treated as clinically authoritative.  
The HITL review log is intentionally provided as a **template** to illustrate how expert validation can be integrated into the pipeline.

Annotation fields are expected to be completed by a clinician or domain expert in real-world use.

---

## Ethics and Limitations

- The project uses only public, de-identified clinical text.
- No attempt is made to infer sensitive attributes or re-identify individuals.
- Model outputs may include spurious entities or label ambiguities.
- The pipeline is illustrative and not intended for direct clinical deployment.

---

## How to Run

1. Open the notebook:
   `Clinical_NLP_Mini_Project.ipynb`

2. Run the notebook in **Google Colab**.

3. Download the MTSamples dataset from Kaggle and upload it to the Colab session.

4. Execute cells sequentially to reproduce all outputs.

---

## Repository Contents

- `Clinical_NLP_Mini_Project.ipynb` — full step-by-step pipeline  
- `entities_long.csv` — structured entity output (long format)  
- `entities_wide.csv` — structured entity output (wide format)  
- `hitl_review_log.csv` — HITL annotation template  

---

## License

This repository contains original code and derived outputs.  
Please refer to the original dataset source for dataset licensing terms.
