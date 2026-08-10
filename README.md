## Hello! I'm Xinran Zhang 👋

I am a Master's student in **Mechanical Engineering at Tsinghua University**, working on **physical-signal foundation models for industrial and robotic systems**.

My research explores how non-text physical signals — such as **vibration, tactile, and acoustic signals** — can be represented, aligned, and reasoned over by **large language models and multimodal foundation models**, with applications in **industrial diagnosis, robotic perception, and intelligent operation & maintenance**.

---

## 📰 Recent News

- **2026.07:** VSLLaVA was published in *Advanced Engineering Informatics*.
- **2026.05:** FaultOvis was submitted to *IEEE Transactions on Industrial Informatics*.
- **2026.03:** I am preparing Ph.D. applications and developing my research portfolio on physical-signal foundation models.
- **2024.05:** I was featured in a [Hunan University official media student profile](https://mp.weixin.qq.com/s/nxoHBo9KyyRW0MGVfkmg9Q) for my undergraduate academic journey. *(in Chinese)*

---

## 🎓 Education

<table>
  <tr>
    <td width="70">
      <img src="assets/img/education/thu.png" width="100">
    </td>
    <td>
      <strong>Tsinghua University</strong><br>
      M.S. in Mechanical Engineering<br>
      Sept. 2024 – Jun. 2027 expected<br>
      GPA: <strong>4.0 / 4.0</strong>, Rank: <strong>1 / 74</strong>
    </td>
  </tr>
</table>

<br>

<table>
  <tr>
    <td width="70">
      <img src="assets/img/education/hnu.png" width="100">
    </td>
    <td>
      <strong>Hunan University</strong><br>
      B.S. in Vehicle Engineering<br>
      Sept. 2020 – Jun. 2024<br>
      GPA: <strong>3.91 / 4.0</strong>, Rank: <strong>1 / 123 for three consecutive academic years</strong>
    </td>
  </tr>
</table>

---

## 🔬 Research Vision

Modern industrial and robotic systems continuously generate rich physical signals, including vibration, tactile, acoustic, force, and other sensor measurements. However, most existing foundation models are primarily designed for text, images, or videos, while physical signals remain underrepresented in the current multimodal AI landscape.

My long-term research goal is to develop **foundation-model-based physical signal intelligence**:  
building unified representations, cross-modal alignment methods, and reliable reasoning frameworks that connect physical signals with **language, vision, and action spaces**.

I am particularly interested in three directions:

- **Physical-signal foundation models** for vibration, tactile, and acoustic signal understanding
- **Robot tactile perception and embodied physical-signal modeling**
- **Industrial AI agents**, intelligent maintenance, and digital-twin systems powered by LLMs

---

## 🔎 Research Interests

- Physical Signal Foundation Models
- Multimodal Large Language Models for Industrial and Robotic Systems
- Signal-Language / Signal-Vision / Signal-Action Alignment
- Vibration, Tactile, and Acoustic Signal Understanding
- Domain Generalization and Representation Learning
- Prognostics and Health Management (PHM)
- Industrial AI Agents and Intelligent Operation & Maintenance

---

## 🚀 Selected Research Projects

### VibAlign: Raw Physical Signal Tokens for LLMs

[![VibAlign](assets/img/vibalign_overview.png)](projects/vibalign.md)

**VibAlign** learns language-aligned signal tokens from raw one-dimensional vibration and tactile signals, enabling LLM-based structured recognition and signal-conditioned reasoning for industrial diagnosis and robotic tactile perception.

**Highlights:** raw physical-signal tokenization · signal-language alignment · robotic tactile sensing · BiMamba encoder · verbalizer-guided LLM adaptation

**Status:** Manuscript in preparation / under review

[Project Page](projects/vibalign.md) · Paper coming soon · Code coming soon

---

### FaultOvis: Domain-Generalized VLM for Industrial Fault Diagnosis

[![FaultOvis](assets/img/faultovis/architecture.png)](projects/faultovis/)

**FaultOvis** adapts a vision-language model to cross-domain bearing fault diagnosis by combining STFT-based signal images, diagnostic instruction tuning, auxiliary visual classification, and contrastive representation learning.

**Highlights:** domain generalization · VLM adaptation · STFT signal images · visual-side discriminative supervision

[Project Page](projects/faultovis.md) · Paper coming soon · Code coming soon

---

### VSLLaVA: Multimodal Instruction Tuning for Industrial Vibration Signal Analysis

[![VSLLaVA](assets/img/vsllava/architecture.png)](projects/vsllava/)

**VSLLaVA** adapts large multimodal foundation models to industrial vibration signal analysis by formulating signal understanding as an expert-guided multimodal question-answering task.

**Highlights:** signal question answering · multimodal instruction tuning · VLM adaptation · GRPO refinement

**Status:** Published in *Advanced Engineering Informatics* · Code publicly available

[Project Page](projects/vsllava/) · [Published Paper](https://www.sciencedirect.com/science/article/pii/S1474034626007159) · [Preprint](https://arxiv.org/abs/2409.07482) · [Code](https://github.com/ZXR-Rachel/VSLLaVA)

---

## 🧩 Earlier Research Experience

### Vision-based Local Map Construction for Autonomous Driving

**This undergraduate thesis explored end-to-end local HD map construction for autonomous driving by transforming multi-view camera images into bird's-eye-view map representations.**

I reproduced and implemented a deep-learning-based BEV map construction framework using NuScenes surround-view camera images. The pipeline includes image feature extraction, BEV view transformation, map-element decoding, and vectorized reconstruction of lane dividers, pedestrian crossings, and road boundaries with piecewise Bezier curves.

**Highlights:** autonomous driving · BEV perception · local HD map construction · Transformer · Swin Transformer · BiFPN · Mask2Former · piecewise Bezier curve

**Results:** trained and evaluated on NuScenes; achieved **42.6 mAP@HARD** and **61.4 mAP@EASY** over three static map-element categories; showed higher average AP than IPM, LSS, VPN, and HDMapNet baselines under the same 30-epoch evaluation setting.

**Status:** Undergraduate thesis · Awarded Excellent Undergraduate Thesis at Hunan University

---

## 🖼️ Project Pages & Visual Portfolio

I am organizing my research projects into visual project pages. Each page includes the motivation, method overview, architecture figures, key results, and links to papers or code when publicly available.

| Project | Topic | Page |
|---|---|---|
| VibAlign | Raw physical-signal tokenization for industrial and robotic systems | [View Project](projects/vibalign.md) |
| FaultOvis | Domain-generalized VLM adaptation for bearing fault diagnosis | [View Project](projects/faultovis.md) |
| VSLLaVA | Multimodal instruction tuning for industrial vibration signal analysis | [View Project](projects/vsllava.md) |

---

## 📚 Publications & Manuscripts

1. **Xinran Zhang**, et al.  
   **VibAlign: Learning Language-Aligned Signal Tokens for Vibration Signal Analysis with Large Language Models.**  
   *Submitted to Mechanical Systems and Signal Processing.*

2. **Xinran Zhang**, Jinfeng Huang, et al.  
   **FaultOvis: A Domain-Generalized Vision-Language Model for Rolling Bearing Fault Diagnosis.**  
   *Submitted to IEEE Transactions on Industrial Informatics.*

3. Qi Li†, **Xinran Zhang†**, et al.  
   **VSLLaVA: A Pipeline of Large Multimodal Foundation Model for Industrial Vibration Signal Analysis.**  
   *Advanced Engineering Informatics*, 2026, 76: 105023.  
   [Published Paper](https://www.sciencedirect.com/science/article/pii/S1474034626007159) · [arXiv](https://arxiv.org/abs/2409.07482) · [Code](https://github.com/ZXR-Rachel/VSLLaVA)

† Equal contribution.

---

## 🏆 Awards & Social Activities

### Selected Awards

- University First-Class Scholarship, Tsinghua University, 2025
- National Scholarship, 2021, 2022, 2023
- Honorable Mention, Mathematical Contest in Modeling, 2023
- National First Prize, National English Competition for College Students, 2023
- National Third Prize, Chinese Mathematics Competition for College Students, 2023
- Second Prize, Hunan Provincial Mechanics Competition, 2022

### Teaching & Leadership

- Teaching Assistant, **Fundamentals of Engineering Drawing**, Tsinghua University
- Leader, Peer Learning Support Group, Hunan University

---

## 💻 Tech Stack

### Programming & Research Tools

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![VSCode](https://img.shields.io/badge/VSCode-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)
![LaTeX](https://img.shields.io/badge/LaTeX-008080?style=for-the-badge&logo=latex&logoColor=white)

### Research Skills

- LLM/VLM adaptation
- LoRA / PEFT
- Multimodal instruction tuning
- GRPO / RL-based refinement
- Contrastive learning
- Representation learning
- Vibration and tactile signal preprocessing
- STFT and envelope spectrum analysis
- Signal visualization and experimental evaluation

---

## 📫 Get in Touch

- Email: [xinran-z24@mails.tsinghua.edu.cn](mailto:xinran-z24@mails.tsinghua.edu.cn)
- GitHub: [ZXR-Rachel](https://github.com/ZXR-Rachel)
- CV: [Download My CV](assets/cv/cv-xinran-zhang.pdf)
- Google Scholar: [Coming Soon](#)
- LinkedIn: [Coming Soon](#)

## ✒️ Last updated: 2026.07.21
