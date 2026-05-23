# NeuroNLP

This repo contains the code for our NLP2 Project C report, **Rethinking Brain-Model Alignment: A Case for Text Embedders**.

The project compares sentence representations from two Qwen models on the Pereira et al. fMRI dataset:

- **Qwen3-8B**, an autoregressive LLM
- **Qwen3-Embedding-8B**, a text embedding model

The main question is whether a model trained specifically for text embeddings gives better brain-predictive sentence representations than a standard next-token prediction model.

## What this project does

We use Experiments 2 and 3 from the Pereira et al. dataset. The original stimuli are passages, but the analyses here are done at the sentence level:

- Experiment 2: 384 sentences
- Experiment 3: 243 sentences

For both models, we extract representations from all 37 layers. Each sentence representation is taken from the final non-padding token of each layer.

We then compare the models using:

- voxel-wise Ridge encoding models
- random embedding baselines
- paired statistical tests
- Representational Similarity Analysis (RSA)
- a residual analysis where broad topic information is reduced

## Files

```text
extract_embeddings.ipynb
