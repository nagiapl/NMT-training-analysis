# NMT-training-analysis

Training and analyzing Transformer-based neural machine translation (NMT) models for **German → English**.

## Overview

This project trains an encoder-decoder Transformer (MarianMT architecture, randomly initialized) from scratch on a small subset of the [Europarl](https://opus.nlpl.eu/Europarl/corpus/version/Europarl) parallel corpus, containing only short sentences (< 10 tokens). The model is then compared against the pretrained [`Helsinki-NLP/opus-mt-de-en`](https://huggingface.co/Helsinki-NLP/opus-mt-de-en), which has the same architecture but was trained on far more data.

Both models are evaluated on an in-distribution validation split (short sentences) and an out-of-distribution split (sentences of length 10–20) to study length generalization.

## What's inside

- **Training**: training the model from scratch with Hugging Face `Seq2SeqTrainer` and tracking train, i.i.d. and o.o.d. losses.
- **Error analysis**: manually categorizing translation errors (omission, hallucination, repetition, fluency, named entities, etc.) for both models.
- **Evaluation metrics**: BLEU, GLEU, chrF, length ratio and a repetition rate, plus a discussion of how well they capture the errors observed.
- **Attention analysis**: visualizing attention with `bertviz` and estimating *attention coverage* to check whether it signals under-translation.
- **Model improvement**: testing decoding strategies such as beam size and length penalty to improve translation quality, especially on longer sentences.

## Files

| File | Description |
|------|-------------|
| `Train_and_analyze_NMT.ipynb` | Main notebook with all code (built for Google Colab with a T4 GPU) |
| `Analysis Report.pdf` | Written report with results and discussion |
