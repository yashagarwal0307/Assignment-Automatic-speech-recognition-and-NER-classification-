## Tasks.
1) Convert audio to speech.
2) Do Named Entity Recognition on the converted speech.


This project demonstrates an **end-to-end pipeline** that combines **Automatic Speech Recognition (ASR)** with **Named Entity Recognition (NER)** to extract structured medical information from spoken audio.

---

## Project Overview.

Healthcare professionals often rely on dictations, voice notes, and patient-doctor conversations. However, unstructured audio is difficult to analyze.
This project aims to:

1. **Convert medical speech into text** using a pretrained ASR model.
2. **Identify key medical entities** such as diseases, symptoms, medications, tests, and anatomical terms using NER.
3. **Build a structured fact sheet** that organizes extracted information.
4. **Evaluate ASR quality** using error rate metrics.

---

## Features.

* **Speech-to-Text Conversion**: Convert audio recordings into accurate transcriptions.
* **Entity Recognition**: Extract medical concepts like diseases, symptoms, and drugs.
* **Fact Sheet Generation**: Summarize extracted information in structured form.
* **Performance Evaluation**: Measure transcription accuracy using **Word Error Rate (WER)**.

---

## Dataset.

We use the **jarvisx17/Medical-ASR-EN dataset** from Hugging Face.

* Contains English audio samples from the medical domain.
* Each sample includes **audio recordings** and corresponding **ground-truth transcriptions**.

---

## Methodology.

### 1. Automatic Speech Recognition (ASR)

*  **Whisper small a pretrained ASR model by OpenAi** was used to transcribe medical speech into text.
* Output: raw transcription of spoken audio.

### 2. Named Entity Recognition (NER)

* A **A pretrained d4data/biomedical-ner-all** was applied to identify relevant entities.
* Categories extracted:

  * **Disease/Disorder**
  * **Symptom/Sign**
  * **Medication/Drug**
  * **Diagnostic & Therapeutic Procedures**
  * **Anatomy/Body Structures**

### 3. Fact Sheet Creation

* The recognized entities were organized into a **fact sheet** for structured interpretation.
* Example format:

  ```
  Disease: [pneumonia]  
  Symptom: [fever, cough]  
  Medication: [antibiotics]  
  Test: [chest x-ray]  
  Anatomy: [lungs]  
  ```
### 4. Map the fact sheet with the actual NER labels in the medical domain  on which the d4data/biomedical-ner-all model was trained on.

### 5. Evaluation Metrics

* **Word Error Rate (WER)**: Measures transcription errors at the word level.
---

## Example Results.

* **Ground Truth**: "My shoulder hurts me so much"
* **Predicted Transcription**: "My shoulder hurts me so much.
* Named Entities:
 - shoulder (Biological_structure, score=0.99)
 - hurts (Sign_symptom, score=0.76)

* Extracted Medical Information/Fact Sheet:
{'Disease': [], 'Symptom': ['hurts'], 'Medication': [], 'Test': [], 'Anatomy': ['shoulder']}
* **Extracted Entities**:

 

## Conclusion.

This project successfully integrates **ASR + NER** for the medical domain, enabling:

* Accurate transcription of spoken medical audio.
* Automatic extraction of critical entities.
* Structured representation in the form of a fact sheet.
* Reliable evaluation using **WER**.

Future work can include fine-tuning domain-specific ASR/NER models or  use a more vast dataset to improve accuracy in real-world clinical settings.

---

This project demonstrates how multimodal AI can be applied in **healthcare speech analysis**, making unstructured medical audio more useful for decision-making.


