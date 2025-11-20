# Scientific Title Generation (T5-small & Mistral 7B)

This project generates scientific paper titles from abstracts using two methods:

1. **T5-small (fine-tuned)** — supervised sequence-to-sequence learning  
2. **Mistral 7B (10-shot)** — prompt-based generation with no training

Both models are evaluated with **BLEU**, **ROUGE-2**, and **ROUGE-L**.

---

## Data

Place these files in the project root:

- `QTL_text.json` — training data (Title + Abstract)
- `QTL_test_labeled.tsv` — test set with reference titles


---

## Methods

### T5-small
- Fine-tuned on `QTL_text.json`
- Generates titles for dev + test sets  
- Saves: `QTL_test_with_predicted_titles.tsv`

### Mistral 7B (10-shot)
- 4-bit quantized model (`mistralai/Mistral-7B-Instruct-v0.3`)
- Uses 10 example (Abstract, Title) pairs in the prompt  
- Saves:  
  - `mistral_dev_zero_shot_10shot.tsv`  
  - `mistral_test_zero_shot_10shot.tsv`

---

## Install

```bash
pip install torch transformers datasets evaluate pandas scikit-learn bitsandbytes
