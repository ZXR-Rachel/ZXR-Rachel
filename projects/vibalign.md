
# VibAlign: Learning Language-Aligned Signal Tokens for Physical Signal Understanding

[← Back to Homepage](../README.md)

## Overview

VibAlign is a raw physical-signal-to-LLM framework that learns language-aligned signal tokens from one-dimensional vibration and tactile signals for industrial diagnosis and robotic tactile perception.

## Motivation

Most existing foundation models are primarily designed for text, images, and videos, while continuous physical signals such as vibration and tactile signals remain underrepresented. VibAlign explores how raw physical signals can be converted into LLM-compatible semantic tokens.

## Method

![VibAlign Architecture](../assets/img/vibalign/architecture.png)

VibAlign consists of a BiMamba-based temporal signal encoder, a soft codebook-based signal token connector, and an LLM adapted through verbalizer-guided supervision.

## Key Contributions

- Raw physical-signal-to-LLM framework for vibration and tactile signals
- BiMamba-based signal encoder for one-dimensional physical signals
- Soft codebook connector for LLM-compatible signal token construction
- Three-stage signal-language alignment pipeline
- Evaluation on industrial vibration and robotic tactile material recognition tasks

## Key Results

![VibAlign Results](../assets/img/vibalign/results_fd.png)

## Robotic Tactile Perception

![Tactile Results](../assets/img/vibalign/results_tactile.png)

## Paper and Code

- Paper: Coming soon
- Code: Coming soon
