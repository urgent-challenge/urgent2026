---
layout: page
permalink: /baseline/
title: Baseline
description:  
nav: false
nav_order: 5

bibliography: baseline.bib
---


> 🚧 This website is currently under construction. All content is subject to change and may not reflect the final details of the competition. Please refer to official announcements once the contest begins for the most accurate and up-to-date information.


<br>

## Baseline code and checkpoint

Please refer to the official [GitHub repository](https://github.com/urgent-challenge/urgent2026_challenge_track1) for more details.


<br>

## Distortion model


<img alt="framework" src="/urgent2026/assets/img/framework.png" style="max-width: 100%;"/>

As depicted in the figure above, we design a distortion model (simulation stage) <d-math>\mathcal{F}(\cdot)</d-math> to unify the data format for different distortion types, such that different speech enhancement (SE) sub-tasks can share a consistent input/output processing. In particular, we ensure that the sampling frequency (SF) at the output of the distortion model (degraded speech) is always equal to that of its input.

During training and inference, the processing of different SFs is supported for both <u>conventional SE models</u> (lower-right) that usually only operate at one SF and <u>adaptive STFT-based sampling-frequency-independent (SFI) SE models</u> (upper-right) that can directly handle different SFs.

* For conventional SE models (e.g., Conv-TasNet<d-cite key="Conv_TasNet-Luo2019"/>), we always **upsample** its input (degraded speech) to the highest SF (48 kHz) so that the model only needs to operate at 48 kHz. The model output (48 kHz) is then **downsampled** to the same SF as the degraded speech.
* For adaptive STFT-based SFI<d-cite key="Sampling-Paulus2022,Toward-Zhang2023,Improving-Zhang2024"/> SE models (e.g., BSRNN<d-cite key="Music-Luo2023,Efficient-Yu2023,High-Yu2023"/>, TF-GridNet<d-cite key="TF_GridNet-Wang2023,TF_GridNet2-Wang2023"/>), we directly feed the degraded speech of different SFs into the model, which can adaptively adjust their STFT/iSTFT configuration according to the SF and generate the enhanced signal with the same SF.
<br>


## Discriminative Baseline

We provide an adaptive STFT-based SFI<d-cite key="Sampling-Paulus2022,Toward-Zhang2023,Improving-Zhang2024"/>  BSRNN <d-cite key="Music-Luo2023,Efficient-Yu2023,High-Yu2023"/> as the discriminative baseline. The model is available at [here](https://github.com/urgent-challenge/urgent2026_challenge_track1). The details of the baseline training can be found in our [recent ASRU paper](https://arxiv.org/abs/2506.23859) <d-cite key="liLessMoreData2025"/>.

## Generative Baseline

We follow a recent work named FlowSE<d-cite key="leeFlowSEFlowMatchingbased2025"/> to build generative SE models. It extends the flow matching method<d-cite key="lipmanFlowMatchingGenerative2023"/> to a conditional flow matching model that generates clean speech conditioned by the noisy speech. We reimplement an [improved BSRNN](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/baseline_code/models/bsrnn_flowse.py) to estimate the conditional vector field. The model is available at [online](https://github.com/urgent-challenge/urgent2026_challenge_track1), and the training details of the generative baseline model can be found in the [paper](https://arxiv.org/abs/2506.23859) <d-cite key="liLessMoreData2025"/>.

