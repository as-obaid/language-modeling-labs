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
| Natural language inference | Replacing every SNLI premise with an uninformative sentence costs a from-scratch transformer only **0.0062** accuracy (**0.5708** → **0.5646**), exposing hypothesis-only bias; a BiLSTM loses **0.0441** |
| Fine-tuning pre-trained transformers | SciBERT detects adverse drug effects at **0.9266** F1 against **0.9111** for DistilBERT and **0.8273** for TF-IDF; dynamic padding feeds the model **38.4%** fewer tokens and lifts DistilBERT throughput from **1067.7** to **1716.4** sentences/s |
| Prompting and evaluating LLMs | With its full prompt (role, chain-of-thought, three examples), flan-t5-base is **100.0%** format-compliant on ICD-10 coding, yet **90.0%** of its codes are hallucinated, copied from the in-context examples; macro F1 never exceeds **0.0667** |

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
| 09 | [Self-Attention for NLI](Lab_9.ipynb) | • Scaled dot-product and multi-head attention from scratch, checked against PyTorch<br>• Transformer encoder vs. BiLSTM<br>• Attention heatmaps and entropy<br>• Hypothesis-only bias probes and contrast pairs | SNLI | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_9.ipynb) |
| 10 | [Fine-Tuning BERT for ADE Detection](Lab_10.ipynb) | • DistilBERT vs. SciBERT fine-tuning against a TF-IDF baseline<br>• Domain shift: subword fragmentation and fill-mask probes<br>• Batch-inference profiling: throughput, latency, GPU memory<br>• Dynamic vs. fixed padding and a latency-SLA check | ADE Corpus v2 | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_10.ipynb) |
| 11 | [Prompting and Evaluating LLMs](Lab_11.ipynb) | • Scaling laws and Chinchilla compute budgeting<br>• Failure modes across pretraining, instruction tuning and RLHF<br>• Zero-shot to few-shot, chain-of-thought and role prompt ablation<br>• Ordering sensitivity, format compliance and hallucination checks | Clinical notes<br>ICD-10-CM | [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/as-obaid/language-modeling-labs/blob/main/Lab_11.ipynb) |

> **Coming next:** End-to-End NLP Application

## Tech stack

| Library | Role | Labs |
| --- | --- | :-: |
| ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) | Language | 01–11 |
| ![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white) | Arrays and vector math | 01–11 |
| ![pandas](https://img.shields.io/badge/pandas-150458?style=for-the-badge&logo=pandas&logoColor=white) | Tabular text data | 01–02 |
| ![NLTK](https://img.shields.io/badge/NLTK-1F6F8B?style=for-the-badge) | Brown corpus, tokenization, stemming and lemmatization | 01–04 |
| ![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white) | TF-IDF, logistic regression, Naive Bayes, LinearSVC, PCA | 03, 05, 06, 10 |
| ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white) | Word2Vec, feedforward networks, RNN / LSTM / GRU, seq2seq with attention, transformer encoder, batch-inference profiling, flan-t5 inference | 05–11 |
| ![gensim](https://img.shields.io/badge/gensim-4C8CF5?style=for-the-badge) | Pretrained GloVe vectors | 05 |
| ![Hugging Face](https://img.shields.io/badge/Hugging_Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black) | WordPiece (`tokenizers`), BERT fine-tuning, fill-mask and flan-t5 prompting (`transformers`), CoNLL-2003, SNLI and ADE (`datasets`) | 03, 07, 09–11 |
| ![SacreBLEU](https://img.shields.io/badge/SacreBLEU-5B5EA6?style=for-the-badge) | Reference BLEU scores | 08 |
| ![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white) | Notebooks, runnable on Google Colab | 01–11 |

## Getting started

**Colab:** click a badge in the [Labs](#labs) table, then choose **Runtime → Run all**.
The first cell installs any missing packages and datasets download on first use.
Lab 10 fine-tunes two transformers, so give it a GPU runtime
(**Runtime → Change runtime type → T4 GPU**); the other labs run on CPU.

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
