# Overview

Multimodal Emotion Recognition (MER) is critical for interpreting real-world interactions. While Multimodal Large Language Models (MLLM) have shown promise in MER, their internal decision-making mechanisms under modality conflict and missingness remain largely underexplored. In this paper, to systematically investigate these behaviors, we introduce EmoMM, a comprehensive benchmark featuring modality-aligned, conflict, and missing subsets. Through extensive evaluation, we uncover a Video Contribution Collapse (VCC) phenomenon, where MLLM marginalize video evidence due to high token redundancy and modality preferences. To address this, we propose Conflict-aware Head-level Attention Steering(CHASE), a lightweight mechanism that detects modality conflicts and performs inference-time attention steering, effectively mitigating decision bias without retraining the backbone. Experimental results demonstrate that CHASE consistently improves performance across various settings, significantly enhancing the reliability of MLLM in complex affective scenarios.

<div style="text-align: center; margin: 24px 0;">
  <img
    src="/figure1-overview.png"
    alt="Overview of the EmoMM benchmark"
    style="max-width: 100%; width: 850px;"
  />
  <p style="margin-top: 8px; font-size: 14px; color: #666;">
    <em>
      Figure 1. Overview of the EmoMM benchmark. Left: subset split of EmoMM into EmoMM-Align, EmoMM-Conflict, and EmoMM-Missing. Right: example instances illustrating the three subsets.
    </em>
  </p>
</div>
