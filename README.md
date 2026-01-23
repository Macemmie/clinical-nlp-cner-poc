[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/macemmie/clinical-nlp-cner-poc/blob/main/Clinical_NLP_Mini_Project.ipynb)

### clinical-nlp-cner-poc

A compact Clinical Natural Language Processing (NLP) proof-of-concept for converting unstructured clinical text into structured data using Clinical Named Entity Recognition (CNER).

This project focuses on clarity, reproducibility, and responsible handling of clinical text, rather than model training or large-scale evaluation.

---

#### Overview

Clinical records are often stored as free-text narratives, limiting their direct use in analytics and AI systems.  
This project demonstrates an end-to-end workflow that extracts clinically relevant entities from unstructured notes and organises them into structured tabular formats.

---

#### Pipeline Summary

1. Load a public, de-identified clinical text dataset.
2. Filter for paediatric-related records.
3. Apply minimal preprocessing to preserve clinical meaning.
4. Perform Clinical Named Entity Recognition using a pre-trained transformer model.
5. Post-process entities and standardise labels into:
   - **PROBLEM**
   - **TEST**
   - **TREATMENT**
6. Convert extracted entities into structured tabular outputs.
7. Illustrate a lightweight human-in-the-loop (HITL) review step.
8. Reflect on ethical considerations and limitations.

---

#### Dataset

This project uses the **MTSamples medical transcription dataset**, publicly available on Kaggle.

The dataset is **not redistributed** in this repository.  
Please obtain it directly from the source:

https://www.kaggle.com/datasets/louiscia/transcription-samples-mtsamples

All processing is performed on **de-identified clinical text**.

---

#### Model

- **Model:** `nlpie/clinical-distilbert-i2b2-2010`
- **Type:** Pre-trained transformer-based Clinical NER model
- **Training source:** i2b2 clinical concept extraction tasks

The model is used **without fine-tuning** to demonstrate out-of-the-box clinical entity extraction.

---

#### Outputs

The pipeline produces the following artefacts:

- **entities_long.csv**  
  Long-format table with one row per extracted entity, including offsets and confidence scores.

- **entities_wide.csv**  
  Wide-format table grouping entities by clinical note and category.

- **hitl_review_log.csv**  
  Human-in-the-loop review template intended for completion by a clinician or qualified domain expert.

---

#### Human-in-the-Loop (HITL)

Automated entity extraction should not be treated as clinically authoritative.  
The HITL review log illustrates how expert validation can be integrated to support accuracy, trust, and downstream clinical use.

---

#### Ethics and Limitations

- Only public, de-identified clinical text is used.
- No attempt is made to re-identify individuals or infer sensitive attributes.
- Model outputs may contain spurious or ambiguous entities.
- The pipeline is illustrative and **not intended for direct clinical deployment**.

---

#### How to Run

1. Open the notebook: `Clinical_NLP_Mini_Project.ipynb`
2. Download the MTSamples dataset from Kaggle and upload it to the Colab session.
3. Run the notebook in **Google Colab**.
4. Execute cells sequentially to reproduce all outputs.

---

#### Repository Contents

- `Clinical_NLP_Mini_Project.ipynb` — end-to-end pipeline notebook  
- `entities_long.csv` — structured entity output (long format)  
- `entities_wide.csv` — structured entity output (wide format)  
- `hitl_review_log.csv` — HITL annotation template

---

#### License

This repository contains original code and derived outputs.  
Please refer to the original dataset source for dataset licensing terms.
