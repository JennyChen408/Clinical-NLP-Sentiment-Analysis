# Clinical-NLP-Sentiment-Analysis
Clinical NLP pipeline for preprocessing patient–provider messages and evaluating sentiment using VADER and RoBERTa.
This repository contains an end-to-end pipeline for processing de-identified patient–provider messages and running baseline sentiment analysis using **VADER** and **RoBERTa**. The project explores how different sentiment models behave on clinical communication and builds the foundation for future fine-tuning with domain-specific models.


# Clinical Message Sentiment Analysis: VADER, RoBERTa, and Model Comparison

This repository contains an end-to-end pipeline for processing de-identified patient–provider messages and running baseline sentiment analysis using **VADER** and **RoBERTa**. The project explores how different sentiment models behave on clinical communication and builds the foundation for future fine-tuning with domain-specific models.

## Repository Structure

### **1. `01_preprocessing.ipynb`**
Text preprocessing pipeline:
- Clean `<Redacted>` tokens → replace with `[NAME]`
- Fix mojibake / corrupted apostrophes 
- Normalize whitespace and remove stray non-ASCII characters
- Export cleaned AE (patient) and AF (provider) messages to `/processed`
This step ensures consistent, model-ready text inputs.

### **2. `02_vader.ipynb`**
Apply **VADER** sentiment analysis:
- Compute compound scores for AE/AF
- Export aligned results (AE-only, AF-only, combined tables)
- Generate summary statistics (mean, median, positivity ratios)
- Quick visualization of sentiment distribution

### **3. `03_roberta.ipynb`**
Apply **RoBERTa** (`cardiffnlp/twitter-roberta-base-sentiment-latest`):
- Batch tokenization and inference
- Convert logits to a continuous sentiment score:
  **score = P(positive) − P(negative)**
- Export aligned AE/AF sentiment tables
- Example visualization: provider sentiment distribution (AI vs non-AI replies)

### **4. `model_comparison.ipynb`**
Compare VADER and RoBERTa outputs:
- Convert continuous scores into **neg / neu / pos** labels
- Side-by-side bar plots:  **VADER vs RoBERTa** for AE and AF messages
- AE vs AF polarity comparison within each model
- Exploratory analysis of agreement / disagreement between models

This notebook provides a concise overview of how the two sentiment models differ on clinical messages.


## Future Work
I am currently preparing a fine-tuning pipeline for **BioClinicalBERT** to better adapt sentiment classification to clinical communication.  
**Updated models, evaluation metrics, and additional analysis notebooks will be added to this repository.**

## Status
⭐ *This project is actively in progress.*  
More updates will be published as the analysis expands.

