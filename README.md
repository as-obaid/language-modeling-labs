<div align="center">

# Language Modeling Labs

Hands-on NLP labs, from corpus statistics and n-gram models to transformers and large language models.

[Highlights](#highlights) · [Labs](#labs) · [Tech stack](#tech-stack) · [Getting started](#getting-started)

</div>

Core methods are implemented from scratch and checked against reference
implementations where they exist. Every notebook is saved fully executed, so
results can be read on GitHub without running anything.

## Highlights

| Area | Result |
| --- | --- |
| N-gram language models | Kneser-Ney smoothing cuts bigram perplexity from **3,169** (Laplace) to **315** on identical Brown test tokens |
| Word embeddings | GloVe-100 tracks human similarity judgments (Spearman ρ = **0.875**, 15 pairs); WEAT finds a strong career/family gender association (d = **1.77**) |
| Vanishing gradients | In an 8-layer sigmoid network the first layer gets **4.4 × 10⁻⁷** of the last layer's gradient norm; with ReLU it gets **0.60** |
| Sequence tagging | A BiLSTM reaches **0.72** span F1 on CoNLL-2003 NER; BIO-constrained decoding removes all **191** invalid tag transitions |
| Neural machine translation | Bahdanau attention lifts Multi30k English→German BLEU from **0.0979** to **0.2836**; the from-scratch BLEU matches SacreBLEU to within **10⁻¹⁶** |

## Labs

| # | Lab | What it covers | Data | |
| :-: | --- | --- | --- | :-: |
| 01 | [NLP Toolkit](Lab_1.ipynb) | • NumPy feature arrays<br>• pandas text wrangling<br>• NLTK frequency distributions | Product reviews<br>Brown | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_1.ipynb) |
| 02 | [Corpus Analysis](Lab_2.ipynb) | • Linguistic ambiguity<br>• Zipf's law fit<br>• Vocabulary coverage and type–token ratio<br>• Tokenization edge cases | Brown | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_2.ipynb) |
| 03 | [Preprocessing and Vectors](Lab_3.ipynb) | • Configurable preprocessing pipeline<br>• BPE from scratch and WordPiece<br>• Stemming vs. lemmatization<br>• BoW and TF-IDF from scratch | Built-in corpus | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_3.ipynb) |
| 04 | [N-gram Language Models](Lab_4.ipynb) | • MLE n-grams and perplexity<br>• Coverage vs. sparsity<br>• Laplace and Kneser-Ney smoothing<br>• Out-of-domain evaluation | Brown | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_4.ipynb) |
| 05 | [Word Embeddings](Lab_5.ipynb) | • Co-occurrence and PPMI<br>• Word2Vec CBOW and skip-gram<br>• GloVe similarity and analogies<br>• PCA projection<br>• WEAT bias test | Toy corpus<br>GloVe 100d | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_5.ipynb) |
| 06 | [Neural Text Classification](Lab_6.ipynb) | • Feedforward net vs. Naive Bayes and LinearSVC<br>• Backpropagation by hand<br>• Vanishing and exploding gradients | 20 Newsgroups | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_6.ipynb) |
| 07 | [Sequence Models](Lab_7.ipynb) | • BiLSTM NER tagger with span-level F1<br>• RNN vs. LSTM vs. GRU<br>• Teacher forcing in seq2seq<br>• BIO error analysis | CoNLL-2003 | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_7.ipynb) |
| 08 | [Seq2Seq with Attention](Lab_8.ipynb) | • LSTM encoder–decoder vs. Bahdanau attention<br>• Loss by source length<br>• BLEU from scratch, checked against SacreBLEU<br>• Attention heatmap analysis | Multi30k En→De | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_8.ipynb) |

> **Coming next:** Self-Attention · Fine-Tuning BERT · Prompting and Evaluating LLMs · End-to-End NLP Application

## Tech stack

| Library | Role | Labs |
| --- | --- | :-: |
| ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) | Language | 01–08 |
| ![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white) | Arrays and vector math | 01–08 |
| ![pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white) | Tabular text data | 01–02 |
| ![NLTK](https://img.shields.io/badge/NLTK-1F6F8B?style=for-the-badge) | Brown corpus, tokenization, stemming and lemmatization | 01–04 |
| ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white) | TF-IDF, Naive Bayes, LinearSVC, PCA | 03, 05, 06 |
| ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white) | Word2Vec, feedforward networks, RNN / LSTM / GRU, seq2seq with attention | 05–08 |
| ![gensim](https://img.shields.io/badge/gensim-4C8CF5?style=for-the-badge) | Pretrained GloVe vectors | 05 |
| ![Hugging Face](https://img.shields.io/badge/Hugging_Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black) | WordPiece (`tokenizers`), CoNLL-2003 (`datasets`) | 03, 07 |
| ![SacreBLEU](https://img.shields.io/badge/SacreBLEU-5B5EA6?style=for-the-badge) | Reference BLEU scores | 08 |
| ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white) | Notebooks, runnable on Google Colab | 01–08 |

## Getting started

**Colab:** click a badge in the [Labs](#labs) table, then choose **Runtime → Run all**.
The first cell installs any missing packages, datasets download on first use,
and no GPU is needed.

**Locally:**

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install jupyter
jupyter lab
```

## About

Coursework for AAI 6620 *Applied Natural Language Processing* at Northeastern
University, Fall 2026. Readings follow Jurafsky and Martin,
[*Speech and Language Processing*](https://web.stanford.edu/~jurafsky/slp3/)
(3rd ed. draft). Assignment prompts and starter code come from the course.

**Muhammad Obaidullah** · [github.com/as-obaid](https://github.com/as-obaid)
