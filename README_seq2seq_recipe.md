
# Neural Recipe Generation with Seq2Seq Models

This repository presents a deep learning project that generates recipe instructions from a list of ingredients using Sequence-to-Sequence (Seq2Seq) models. Several model variants are explored, incorporating mechanisms such as attention, copy, coverage, and checklist to enhance generation quality and reduce issues like repetition and out-of-vocabulary (OOV) errors.

## Overview

The objective is to train models that convert a list of ingredients into coherent cooking instructions. All models are based on RNN encoder-decoder architectures and implemented using PyTorch. Various model extensions were introduced to improve output performance and robustness.

## Model Variants

Six models are implemented and compared:

### Baselines
- **Baseline 1**: Basic Seq2Seq model without attention
- **Baseline 2**: Seq2Seq model with attention

### Mild Extensions
- **Mild Extension 1**:
  - Uses pretrained GloVe embeddings (100 dimensions)
  - Smaller hidden and embedding sizes
  - Increased maximum output length
- **Mild Extension 2**:
  - Shared embedding between encoder and decoder
  - Two-layer encoder and decoder
  - Larger hidden and embedding sizes

### Spicy Extensions
- **Spicy Extension 1**:
  - Incorporates a coverage mechanism to reduce repetition
- **Spicy Extension 2**:
  - Combines coverage, checklist, and copy mechanisms
  - Uses a smaller batch size to handle complexity

## Key Techniques

### Attention  
Enables the decoder to focus on relevant parts of the input at each step of generation.

### Copy Mechanism  
Based on See et al. (2017), allows the model to copy words directly from the input, which helps with rare or unknown tokens.

### Coverage Mechanism  
Based on Tu et al. (2016), tracks attention history to avoid repeated phrases.

### Checklist Mechanism  
Based on Kiddon et al. (2016), ensures that each input ingredient is addressed at least once in the generated output.

## Evaluation Metrics

Models are evaluated using:
- BLEU-4
- METEOR
- BERTScore (F1)

## References

- Kiddon et al., 2016: [Globally Coherent Text Generation with Neural Checklist Models](https://aclanthology.org/D16-1032/)
- See et al., 2017: [Get to the Point: Summarization with Pointer-Generator Networks](https://aclanthology.org/P17-1099/)
- Tu et al., 2016: [Modeling Coverage for Neural Machine Translation](https://aclanthology.org/P16-1008/)
- Vinyals et al., 2016: [Order Matters: Sequence to Sequence for Sets](https://arxiv.org/pdf/1511.06391)

## Notes

- All models are implemented in PyTorch.
- The test set is used for evaluation only and is not involved in training or preprocessing.
- Coverage, copy, attention, and checklist mechanisms are implemented manually.
