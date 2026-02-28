# FʀᴜɢᴀʟPʀᴏᴍᴘᴛ: Reducing Contextual Overhead in Large Language Models via Token Attribution
This repository contains the code and data of the paper titled **"FʀᴜɢᴀʟPʀᴏᴍᴘᴛ: Reducing Contextual Overhead in Large Language Models via Token Attribution."**

[![arXiv](https://img.shields.io/badge/arXiv-2510.16439-b31b1b.svg?logo=arxiv)](https://arxiv.org/abs/2510.16439)
[![GoogleScholar](https://img.shields.io/badge/Google%20Scholar-4285F4?style=flat&logo=Google+Scholar&logoColor=white&color=gray&labelColor=4285F4)](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=4L_7vaoAAAAJ&citation_for_view=4L_7vaoAAAAJ:WF5omc3nYNoC)

[![PDF](https://img.shields.io/badge/Paper%20PDF-EF3939?style=flat&logo=adobeacrobatreader&logoColor=white&color=gray&labelColor=ec1c24)](https://www.arxiv.org/pdf/2510.16439)

**License:** Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International

[![license](https://arxiv.org/icons/licenses/by-nc-sa-4.0.png)](http://creativecommons.org/licenses/by-nc-sa/4.0/)

## Overview

FrugalPrompt is a novel prompt compression framework that retains only the most semantically significant tokens in an input prompt before sending it to a Large Language Model (LLM). By leveraging token attribution methods — **GlobEnc** and **DecompX** — FrugalPrompt assigns saliency scores to every token in the input, ranks them, and retains only the top-*k*% most salient tokens to form a sparse, *frugalized* prompt. This reduces monetary costs, carbon footprint, and inference-time latency while maintaining competitive task performance.

The framework is evaluated across four NLP tasks:
- **Text Classification (CLS)** — Sentiment Analysis
- **Text Summarization (SUM)** — News Article Summarization
- **Question Answering (QA)** — Commonsense QA
- **Text Reasoning (RSN)** — Mathematical Reasoning

## Pipeline

The FrugalPrompt pipeline works as follows:

1. **Token Attribution:** The input prompt tokens ⟨t₁, t₂, …, tₙ⟩ are passed through a task-specific token attribution module (GlobEnc or DecompX built on a 110M BERT encoder) to generate saliency scores ⟨s₁, s₂, …, sₙ⟩ for each token.
2. **Token Ranking & Filtering:** Tokens are ranked by their saliency scores. The top *p = k% × n* tokens are selected while **preserving the original token order** to form the reduced (frugalized) prompt.
3. **LLM Inference:** The frugalized prompt is passed to a frozen LLM for task inference.

## Citation
If you find this work useful, please cite our paper:
```bib
@article{raiyan2025frugalprompt,
  title={FrugalPrompt: Reducing Contextual Overhead in Large Language Models via Token Attribution},
  author={Raiyan, Syed Rifat and Ishmam, Md Farhan and Imran, Abdullah Al and Moni, Mohammad Ali},
  journal={arXiv preprint arXiv:2510.16439},
  year={2025}
}
```
