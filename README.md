# NeuroNLP

This repository contains the code for the NLP2 Project C report **“Rethinking Brain-Model Alignment: A Case for Text Embedders.”** The project compares the brain predictivity of sentence representations extracted from **Qwen3-8B**, an autoregressive language model, and **Qwen3-Embedding-8B**, a dedicated text embedding model, using the Pereira et al. fMRI dataset.

## Project overview

Large language models are increasingly used to model neural responses to language. Most work focuses on autoregressive models trained with next-token prediction, but it remains unclear whether these models are always the best source of sentence-level representations for brain encoding.

This project asks whether a dedicated text embedding model can better predict sentence-level fMRI responses than an autoregressive LLM from the same model family. We compare the models across layers, experiments, and complementary analyses.

## Research questions

The project addresses two main questions:

1. Does Qwen3-Embedding-8B produce more brain-predictive sentence representations than Qwen3-8B?
2. Does the relative advantage of each model depend on the semantic structure of the stimulus set?

## Dataset

We use Experiments 2 and 3 from the Pereira et al. fMRI dataset.

- **Experiment 2:** 96 passages, 384 sentence stimuli.
- **Experiment 3:** 72 passages, 243 sentence stimuli.
- Analyses are conducted at the **sentence level**.
- fMRI responses are restricted to the left-hemisphere language network ROI.

The dataset is not included in this repository and must be obtained separately.

## Models

The project compares:

- **Qwen3-8B:** autoregressive LLM trained with next-token prediction.
- **Qwen3-Embedding-8B:** dedicated embedding model trained for semantic similarity and retrieval.

For both models, representations are extracted from all 37 hidden-state layers, including the initial embedding layer. Sentence representations are obtained using the final non-padding token from each layer.

## Analyses

The repository includes code for:

- extracting sentence-level representations from both models;
- fitting voxel-wise Ridge encoding models;
- evaluating encoding accuracy with cross-validation;
- computing random embedding baselines;
- comparing models with paired statistical tests;
- running Representational Similarity Analysis (RSA);
- applying a residual method to reduce broad topic-level information.

## Repository structure

```text
NeuroNLP/
│
├── extract_embeddings.ipynb
│   Extracts layer-wise sentence embeddings from Qwen3-8B and Qwen3-Embedding-8B.
│
├── further_analysis.ipynb
│   Runs additional analyses, including random baselines, RSA, and residual analyses.
│
├── results/
│   Stores generated embeddings, figures, and analysis outputs.
│
├── data/
│   Expected location for Pereira dataset files. The dataset itself is not included.
│
└── README.md
