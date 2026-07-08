# VibAlign: Learning Language-Aligned Signal Tokens for Physical Signal Understanding

[← Back to Homepage](../README.md)

## Overview

VibAlign is a raw physical-signal-to-LLM framework for industrial diagnosis and robotic tactile perception.

It learns language-aligned signal tokens from one-dimensional vibration and tactile signals, enabling large language models to perform structured physical-signal recognition and signal-conditioned response generation.

This work represents my recent transition from signal-image-based multimodal adaptation toward direct physical-signal tokenization, with the goal of connecting raw vibration and tactile signals to language-based reasoning systems.

## Motivation

Modern industrial and robotic systems continuously generate rich physical signals, including vibration, tactile, acoustic, force, and other sensor measurements. However, most existing foundation models are primarily designed for text, images, and videos, while continuous physical signals remain underrepresented in the current multimodal AI landscape.

Existing LLM/MLLM-based signal analysis methods often rely on intermediate representations such as signal descriptions, statistical features, spectrograms, or time-frequency images. These approaches can be useful, but they do not directly address a fundamental question:

How can raw one-dimensional physical signals be converted into LLM-compatible semantic tokens?

VibAlign aims to bridge this gap by learning compact signal tokens from raw vibration and tactile signals and aligning them with textual label semantics. The framework is designed for structured physical-signal understanding in both industrial fault diagnosis and robotic tactile material recognition.

## Method

![VibAlign Architecture](../assets/img/vibalign/architecture.png)

VibAlign consists of three main components:

- A BiMamba-based temporal signal encoder for extracting representations from raw one-dimensional physical signals
- A learnable soft codebook connector that converts signal representations into LLM-compatible signal-token embeddings
- A LoRA-adapted LLM trained with verbalizer-guided supervision for structured response generation

The framework follows a three-stage training paradigm. First, the signal encoder is pretrained to learn discriminative and reconstructive signal representations. Second, the codebook connector is trained to align signal tokens with class-level textual semantics through contrastive learning. Third, the LLM is adapted with signal-conditioned instruction data and verbalizer-guided supervision.

During inference, VibAlign uses candidate scoring over the legal label set to improve label validity and response-format stability, followed by structured explanation generation.

## Key Contributions

- A raw physical-signal-to-LLM framework for vibration and tactile signal understanding
- A BiMamba-based signal encoder for modeling temporal dependencies in one-dimensional physical signals
- A soft codebook-based connector for constructing compact LLM-compatible signal tokens
- A three-stage signal-language alignment pipeline combining signal encoder pretraining, signal-text contrastive alignment, and verbalizer-guided LLM adaptation
- Candidate scoring-based inference for stable and label-consistent physical-signal recognition
- Evaluation on both industrial rolling bearing fault diagnosis and robotic tactile material recognition tasks
- Additional inference studies, signal-embedding sanity checks, ablations, cross-dataset analysis, and real-world THU dataset analysis

## Key Results

### Industrial Fault Diagnosis

![Fault Diagnosis Results](../assets/img/vibalign/fd_results.png)

VibAlign is evaluated on multiple rolling bearing fault diagnosis datasets, including public benchmark datasets and real-world THU vibration data.

The results show that VibAlign achieves strong within-dataset performance on public industrial vibration datasets and competitive performance compared with traditional discriminative classifiers and image-based MLLM diagnostic baselines under their respective original inference protocols.

These results suggest that raw physical-signal tokenization can serve as a promising alternative to signal-image-based MLLM adaptation for industrial fault diagnosis.

### MLLM-Based System-Level Comparison

![MLLM Comparison](../assets/img/vibalign/mllm_comparison.png)

VibAlign is compared with representative MLLM-based diagnostic systems that use image-based signal representations. Unlike these signal-image-based methods, VibAlign directly constructs signal tokens from raw one-dimensional signals.

The comparison is interpreted as a system-level comparison rather than a fully decoding-controlled representation comparison, because different MLLM methods may follow different original inference protocols.

## Robotic Tactile Perception

![Robotic Tactile Results](../assets/img/vibalign/tactile_results.png)

In addition to industrial vibration diagnosis, VibAlign is evaluated on robotic tactile material recognition.

This setting is important because tactile vibration signals are generated through physical contact between a robot and external materials. By applying VibAlign to robotic tactile data, this work extends physical-signal-to-language modeling from industrial machinery diagnosis toward robotic perception and embodied physical sensing.

The tactile recognition results show that raw tactile vibration signals can also be converted into LLM-compatible signal tokens for structured material recognition.

## Inference and Signal Embedding Analysis

VibAlign further studies different inference strategies and signal-embedding conditions.

The inference comparison shows that open-ended free generation is unstable for structured physical-signal prediction, while candidate scoring over legal labels substantially improves label validity and response-format stability.

The signal-embedding sanity study shows that replacing real signal embeddings with no signal, random noise, or shuffled mismatched embeddings leads to clear performance degradation. This indicates that VibAlign relies on the input physical signal rather than only memorizing textual priors or response templates.

## Ablation Study

Ablation studies analyze the effects of several key components, including LLM adaptation, signal-text alignment, positional embedding, reconstruction regularization, the codebook connector, and verbalizer-guided supervision.

The results support the importance of signal-conditioned LLM adaptation, signal-text contrastive alignment, verbalizer loss, and codebook-based signal token construction for stable physical-signal-to-language modeling.

## Real-World THU Analysis

The real-world THU vibration dataset presents stronger dataset shift and more challenging signal conditions than standard public benchmarks.

Additional analysis shows that raw-signal-to-language modeling remains sensitive to severe dataset-level shifts. The THU experiments also suggest that longer temporal contexts can be beneficial for real-world vibration modeling, especially when fault-related patterns require more extended temporal information.

## Paper and Code

- Paper: Coming soon
- Code: Coming soon
- Status: Manuscript coming soon

## Notes

VibAlign is positioned as a physical-signal-to-language modeling framework rather than a conventional task-specific classifier.

Its main contribution lies in exploring how raw vibration and tactile signals can be converted into compact signal tokens and aligned with language semantics, providing a step toward physical-signal foundation models for industrial and robotic systems.