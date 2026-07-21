# VSLLaVA: A Pipeline for Large Multimodal Foundation Models in Industrial Vibration Signal Analysis

[← Back to Homepage](../README.md)

## Overview

VSLLaVA is a vibration-signal-oriented large multimodal model adaptation pipeline for industrial signal analysis and Prognostics and Health Management (PHM).

It formulates vibration signal interpretation as a multimodal question-answering task, enabling large vision-language models to perform signal type identification, signal parameter analysis, and explanatory diagnostic response generation through a natural-language interface.

This work represents my early exploration of connecting physical vibration signals with large multimodal foundation models through signal visualization, expert-guided instruction tuning, and signal-oriented response refinement.

## Motivation

Large multimodal models provide a flexible natural-language interface for visual reasoning and interactive analysis. However, general-purpose LMMs usually lack domain-specific priors for industrial vibration signal analysis, while conventional PHM systems are often designed as task-specific pipelines with fixed labels, fixed outputs, and limited interactivity.

VSLLaVA aims to bridge this gap by converting vibration signal analysis into an expert-guided Signal-Question-Answer (SQA) format. Instead of replacing specialized diagnostic models, it provides a flexible human-in-the-loop interface that allows PHM engineers to query signal types, parameters, and diagnostic explanations through multimodal instructions.

## Method

![VSLLaVA Pipeline](../assets/img/vsllava/architecture.png)

VSLLaVA consists of four main components:

- Expert-guided Signal-Question-Answer dataset construction from simulated and real vibration signals
- LoRA-based supervised fine-tuning of multiple vision-language model backbones
- Dual-mode evaluation combining rule-based metrics and an LMM referee
- GRPO-based post-SFT refinement for more concise, stable, and label-consistent signal identification

The pipeline first converts vibration signals into visual representations and constructs multimodal SQA triplets. Different VLM backbones are then adapted through parameter-efficient supervised fine-tuning. Finally, a tailored GRPO stage is introduced to improve classification-oriented signal type identification.

## Key Contributions

- A vibration-signal-oriented LMM adaptation pipeline for industrial signal analysis
- An expert-guided Signal-Question-Answer dataset that converts vibration signal characteristics, physical principles, and diagnostic reasoning into multimodal instruction data
- LoRA-based SQA supervised fine-tuning across multiple VLM backbones
- A tailored GRPO refinement stage for signal type identification
- A dual-mode evaluation framework combining expert-designed quantitative metrics and LMM-referee evaluation
- Additional validation through text-only ablation, real-signal experiments, vision-encoder co-tuning analysis, and conventional deep learning baselines

## Key Results

### SQA-SFT Performance

![SQA-SFT Bar Results](../assets/img/vsllava/sft_bar.png)

SQA-based supervised fine-tuning consistently improves the signal-oriented question-answering ability of multiple VLM backbones. The adapted models show clear gains in signal type identification, parameter-oriented responses, and explanatory answer quality compared with their corresponding base models.

For example, Ovis2-8B improves from 64.29% to 80.81% in Word Recall and from 0.16 to 5.52 in CIDEr after SQA-SFT. Qwen2-VL-2B-Instruct improves from 62.66% to 73.83% in Word Recall and from 0.60 to 4.76 in CIDEr. These results show that expert-guided SQA fine-tuning helps general-purpose VLMs acquire vibration-signal-specific understanding.

The results also show that exact numerical parameter identification remains challenging. Some models achieve better semantic and textual metrics after SQA-SFT but still suffer from high Mean Relative Error, indicating that current VLMs can learn signal-related concepts more reliably than precise numerical parameter reading.

### Cross-Backbone Evaluation

![SQA-SFT Heatmap Results](../assets/img/vsllava/sft_heatmap.png)

The heatmap results further show that the proposed SQA-SFT strategy is not limited to a single model architecture. Multiple VLM backbones, including InternVL3, Ovis2, LLaVA-next, and Qwen2-VL, benefit from the same expert-guided signal-question-answer adaptation pipeline.

The degree of improvement differs across backbones and signal categories. Models with stronger pretrained visual-language alignment, such as Ovis2-8B and Qwen2-VL, generally achieve stronger post-SFT performance. Real-bearing signals remain more difficult than many simulated signal categories because of stronger noise, weaker visual regularity, and more complex physical patterns.

## GRPO Refinement

![GRPO Training Results](../assets/img/vsllava/grpo_curve.png)

After SQA-SFT, VSLLaVA introduces a GRPO-based refinement stage for signal type identification. This stage is designed to improve answer conciseness, format stability, and label consistency.

The GRPO reward function incorporates domain-specific synonym matching, fuzzy matching, and exact-match bonuses. Experimental results show that GRPO further improves classification-oriented signal identification performance by encouraging the model to generate concise and mappable signal type responses.

Across the evaluated VLM backbones, SQA-SFT+GRPO consistently improves signal-type classification metrics over SQA-SFT alone. For example, InternVL3-8B improves from 79.36% to 97.50% in accuracy and from 76.99% to 97.48% in macro F1. LLaVA-next-8B improves from 77.84% to 95.27% in accuracy and from 77.77% to 97.06% in macro F1.

GRPO is therefore used as a task-specific post-SFT refinement step. Its role is to improve concise and label-consistent signal type identification rather than to claim universal improvement on all open-ended signal reasoning tasks.

## Additional Studies

### Text-Only SQA Ablation

To examine whether the improvement brought by VSLLaVA mainly comes from textual exposure or multimodal signal-question-answer alignment, we conducted a text-only ablation using Qwen2.5 language models without signal images.

| Model | Stage | Word Recall (%) | CIDEr | Mean Relative Error |
|---|---|---:|---:|---:|
| Qwen2.5-0.5B-Instruct | Base | 42.46 | 0.00 | 8.19 |
| Qwen2.5-0.5B-Instruct | Text-only SFT | 58.00 | 2.17 | 2368.51 |
| Qwen2.5-7B-Instruct | Base | 50.86 | 0.00 | 36.89 |
| Qwen2.5-7B-Instruct | Text-only SFT | 56.19 | 2.62 | 72.66 |

Text-only SFT improves language-level matching metrics. For Qwen2.5-0.5B-Instruct, Word Recall increases from 42.46% to 58.00%, and CIDEr increases from 0.00 to 2.17. For Qwen2.5-7B-Instruct, Word Recall increases from 50.86% to 56.19%, and CIDEr increases from 0.00 to 2.62.

However, text-only models still remain limited in signal-grounded understanding because no signal image is provided. The large Mean Relative Error of Qwen2.5-0.5B-Instruct after text-only SFT also suggests that the model can learn answer templates and terminology but may still generate numerical values that are not grounded in the actual signal.

Overall, this ablation confirms that the proposed SQA dataset is not merely a collection of signal-related texts. Its main value lies in the structured multimodal pairing of signal visualizations, expert questions, and diagnostic answers.

### Conventional Deep Learning Baselines

VSLLaVA also compares with conventional task-specific deep learning baselines, including ViT and ResNet, to contextualize the proposed LMM-based pipeline against pre-LMM diagnostic models.

Since ViT and ResNet cannot generate open-ended natural-language responses, the original SQA benchmark is reformulated into two task-specific settings: 12-class signal type classification and parameter regression.

| Model | Setting | Word Recall (%) | Mean Relative Error | Num. Score |
|---|---|---:|---:|---:|
| ViT | Task-specific training | 91.07 | 127.62 | 0.55 |
| ResNet | Task-specific training | 90.93 | 297.79 | 0.50 |

The results show that conventional DL baselines perform strongly on the closed-set signal type classification sub-task. ViT and ResNet achieve Word Recall values of 91.07% and 90.93%, respectively, after task-specific training.

However, these baselines require decomposing the SQA benchmark into separate classification and regression tasks. Their outputs are further converted into fixed answer templates for evaluation, so text-generation metrics such as BLEU, ROUGE, and CIDEr should not be interpreted as open-ended generation quality.

Therefore, the conventional DL baselines are interpreted as strong task-specific references rather than direct replacements for VSLLaVA. In contrast, VSLLaVA operates through a unified multimodal question-answering interface.

### Vision-Encoder Co-Tuning

An additional ablation examines whether co-tuning the vision encoder together with language-side LoRA can further improve vibration-signal understanding.

In the main SQA-SFT setting, the vision encoder and visual-language alignment unit are frozen, and only language-side LoRA modules are trained. In this ablation, the vision encoder is also co-tuned during SQA-based fine-tuning.

| Model | Setting | Word Recall (%) | CIDEr | BLEU-4 |
|---|---|---:|---:|---:|
| Ovis2-8B | SQA-SFT + vision co-tuning | 78.56 | 4.98 | 0.64 |
| Qwen2-VL-7B-Instruct | SQA-SFT + vision co-tuning | 70.44 | 4.36 | 0.57 |

Compared with the frozen-vision SQA-SFT setting reported in the main evaluation, vision-encoder co-tuning does not consistently provide additional benefit. For example, Ovis2-8B with vision co-tuning achieves 78.56% Word Recall, 4.98 CIDEr, and 0.64 BLEU-4, which are lower than the corresponding frozen-vision SQA-SFT results.

These results suggest that directly adapting a natural-image-pretrained vision encoder with limited signal-oriented SQA data may introduce instability or overfitting rather than consistently improving signal-language alignment.

Therefore, VSLLaVA keeps the vision encoder and alignment unit frozen in the main experiments for controlled, efficient, and comparable adaptation across different VLM backbones. Signal-specific visual pretraining remains an important future direction.

### Real-Signal JNU Experiment

To further examine real-signal robustness, VSLLaVA includes an additional experiment on the JNU bearing dataset using both raw waveform images and envelope-spectrum representations.

The JNU experiment contains four real bearing conditions: healthy, inner race defect, outer race defect, and roller element defect. For each signal segment, two visual representations are generated from the same 1-second window: the raw time-domain waveform and the envelope spectrum obtained through Hilbert envelope analysis.

| Model | Setting | Macro Acc. (%) | Macro F1 (%) | Recognized / Unrecognized | Word Recall (%) |
|---|---|---:|---:|---:|---:|
| Ovis2-8B | Base | 76.25 | 12.50 | 43 / 57 | 41.49 |
| Ovis2-8B | SQA-SFT w/ raw waveform | 68.75 | 9.52 | 65 / 35 | 63.22 |
| Ovis2-8B | SQA-SFT w/ envelope spectrum | 60.63 | 19.52 | 99 / 1 | 55.17 |
| Qwen2-VL-2B-Instruct | SQA-SFT w/ raw waveform | 67.50 | 16.40 | 80 / 20 | 73.36 |
| Qwen2-VL-2B-Instruct | SQA-SFT w/ envelope spectrum | 70.63 | 17.31 | 81 / 19 | 85.18 |

The results show that SQA-SFT improves real-signal response quality for several VLM backbones, but the benefit of envelope-spectrum visualization is model-dependent. For example, Qwen2-VL-2B-Instruct achieves higher Word Recall with envelope-spectrum fine-tuning than with raw-waveform fine-tuning, improving from 73.36% to 85.18%.

Envelope-spectrum representations can also reduce invalid or unmappable predictions in some cases. For instance, Ovis2-8B produces 99 recognized predictions with envelope-spectrum fine-tuning, compared with 65 under raw-waveform fine-tuning and 43 under direct base-model inference.

However, robust closed-set real-bearing-fault classification remains challenging for general-purpose VLMs. Some settings achieve relatively high macro accuracy, but their macro F1 scores remain low, indicating class bias, unmappable outputs, or insufficient discrimination among fault types.

Overall, the JNU experiment shows that envelope analysis is a useful but not universally sufficient preprocessing strategy. Real bearing signals still require stronger signal-specific visual representations, more explicit frequency-domain grounding, and more reliable adaptation methods.

## Paper and Code

- Published paper: [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S1474034626007159)
- Preprint: [arXiv](https://arxiv.org/abs/2409.07482)
- Code: [GitHub](https://github.com/ZXR-Rachel/VSLLaVA)
- Citation: Li Q, Zhang X, Huang J, et al. VSLLaVA: A pipeline for Large Multimodal Foundation Models in industrial vibration signal analysis. *Advanced Engineering Informatics*, 2026, 76: 105023.
- Status: Published in *Advanced Engineering Informatics*

## Notes

VSLLaVA is positioned as a flexible human-in-the-loop interface for PHM engineers. It complements rather than replaces specialized task-specific diagnostic models.

Its main contribution lies in adapting large multimodal models to vibration-signal-oriented question answering, enabling natural-language interaction with industrial signal analysis tasks. The additional ablation, baseline, co-tuning, and real-signal studies further show both the potential and current limitations of using general-purpose VLMs for physical signal understanding.