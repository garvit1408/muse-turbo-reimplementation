# 🧠 MuSE: Multimodal Sarcasm Explanation - TURBO Model Reimplementation

This repository provides a reimplementation of the **TURBO** model for the **MuSE (Multimodal Sarcasm Explanation)** task using the **MORE+** dataset.

---

## 📌 Project Overview

This project aims to generate textual explanations for sarcastic social media posts that include both an image and a caption.

- Uses **Vision Transformer (ViT)** for image encoding.
- Uses **BART-base** for text generation.
- Implements a **Shared Fusion Mechanism** to combine image and text features (excluding Knowledge Graphs and GCNs).

---

## 🗂 Dataset

- **Dataset**: MORE+  
- **Required Files**:
  - `Images/` directory — contains the post images.
  - `train_df.tsv`, `val_df.tsv` — tab-separated files with:
    - `pid` (post ID)
    - `caption` (text of the post)
    - `explanation` (target explanation)
    - `sarcasm_target` (ground truth label)
  - `O_train.pkl`, `O_val.pkl` — detected objects.
  - `D_train.pkl`, `D_val.pkl` — image descriptions.

> ⚠️ Ensure these files are placed in the appropriate directories before training.

---

## ⚙️ Code Flow

1. **Data Loading**  
   Loads captions, object annotations, and image descriptions using `pandas` and `pickle`.

2. **Model Setup**  
   Initializes ViT and BART tokenizer using HuggingFace Transformers.

3. **Custom Dataset Class**  
   Prepares inputs by combining image features, object info, and captions.

4. **Model Definition**  
   Wraps ViT and BART into a unified model with a shared fusion mechanism.

5. **Training**  
   Fine-tunes the model using the HuggingFace `Trainer` API.

6. **Evaluation**  
   Generates sarcasm explanations and evaluates using:
   - **BLEU**
   - **ROUGE**
   - **METEOR**
   - **BERTScore**

7. **Checkpointing**  
   Saves model checkpoints after each epoch.

---

## 📊 Evaluation Metrics

- **BLEU**: BLEU-1, BLEU-2, BLEU-3, BLEU-4  
- **ROUGE**: ROUGE-1, ROUGE-2, ROUGE-L  
- **METEOR**  
- **BERTScore**

---

## 🏁 How to Run

1. Clone this repository and set up your environment.
2. Place the dataset files in the correct paths.
3. Run either of the following to start training:
   - `code.ipynb` (Jupyter Notebook)
   - `code.py` (Python script)
4. The output directory will include:
   - Trained model checkpoints
   - Generated explanations for validation/test sets

---

## 📎 Dependencies

Install the following Python packages before running:

```bash
pip install transformers torch scikit-learn pandas Pillow evaluate
```
## ✍️ Author

Reimplemented by Garvit Singh
