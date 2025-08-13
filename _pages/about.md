---
# layout: default
layout: default
title: About
permalink: /
subtitle: Universality, Robustness, and Generalizability for EnhancemeNT

profile:
  align: right
  image: 
  image_circular: false # crops the image to make it circular
  address: >

news: false  # includes a list of news items
selected_papers: false # includes a list of papers marked as "selected={true}"
social: false  # includes social icons at the bottom of the page

bibliography: about.bib
# bibliography: papers.bib
---


## ICASSP 2026 URGENT Challenge

> 🚧 This website is currently under construction. All content is subject to change and may not reflect the final details of the competition. Please refer to official announcements once the contest begins for the most accurate and up-to-date information.


<div style="text-align: center;">
    <img alt="introduction" src="/urgent2026/assets/img/urgent2026.jpeg" style="max-width: 95%;" />
</div>

The ICASSP 2026 URGENT challenge (**U**niversal, **R**obust and **G**eneralizable speech **E**nhanceme**NT**) is a speech enhancement challenge held at [**ICASSP 2026 SP Grand Challenge**](https://2026.ieeeicassp.org/call-for-sp-grand-challenge-proposals/). We aim to build universal speech enhancement models for unifying speech processing in a wide variety of conditions.


<!-- ## Contents

- [ICASSP 2026 URGENT Challenge](#icassp-2026-urgent-challenge)
- [Contents](#contents)
- [Goal](#goal)
- [Task Introduction](#task-introduction)
  - [Track 1: Speech Enhancement](#track-1-speech-enhancement)
  - [Track 2: Speech Quality Assessment](#track-2-speech-quality-assessment)
- [Registration](#registration)
- [Paper submission](#paper-submission)
- [Slack channel](#slack-channel)
- [Links](#links)
  - [Data](#data)
  - [Baseline and Pre-training Models](#baseline-and-pre-training-models)
  - [Leaderboard and registration](#leaderboard-and-registration)
  - [Contact](#contact)
- [Motivation](#motivation) -->



## Goal

The ICASSP 2026 URGENT Challenge aims to further promote the research on **U**niversal, **R**obust and **G**eneralizable speech **E**nhanceme**NT**. 
This year's challenge focuses on the following aspects:

1. **Data Curation in Large-scale Datasets**. Some recent studies reveal diminishing returns from scaling datasets for speech enhancement (SE)<d-cite key="zhangPerformancePlateausComprehensive2024,gonzalezEffectTrainingDataset2024a,koheiurgent2025"/>, and data curation is crucial for training SE models with large-scale data<d-cite key="liLessMoreData2025"/>. The challenge aims to draw people's attention to this phenomenon, so as to make better use of large-scale data for speech enhancement.

2. **More Diverse Speech Sources**. While prior URGENT challenges addressed speech diversity through acoustics and language, the third challenge expands to critical understudied dimensions like age, accents, whispered/singing voices, and emotional speech.

3. **Speech Quality Assessment (SQA) Track Based on Human Ratings**. The ICASSP 2026 URGENT Challenge introduces a new track for perceptual quality prediction models using human ratings, featuring large-scale, distortion-diverse data tailored for SE—unlike existing SQA challenges.

<br>

## Task Introduction

### Track 1: Speech Enhancement
The task of this challenge is to build **a single speech enhancement system** to adaptively handle input speech with different distortions (corresponding to different SE subtasks), different domains (e.g., language, age, accents, emotion), different input formats (e.g., sampling frequencies) in different acoustic environments (e.g., noise and reverberation).

The training data will consist of several public corpora of speech, noise, and RIRs. **Only the specified set of data can be used during the challenge**. 
We encourage participants to apply data augmentation techniques such as dynamic mixing to achieve the best generalizability. 
The data preparation scripts are released in our GitHub repository<d-footnote><a href="https://github.com/urgent-challenge/urgent2025_challenge/" target="_blank">https://github.com/urgent-challenge/urgent2026_challenge_track1/</a></d-footnote>. Check the [`Data`](/urgent2026/data) tab for more information.


We will evaluate enhanced audios with a variety of metrics to comprehensively understand the capacity of existing generative and discriminative methods. They include four different categories of metrics<d-footnote>. An additional category (subjective SE metrics) will be added for the final blind test phase for evaluating the MOS score.</d-footnote>:

<!-- 2. DNSMOS Pro<d-cite key="cumlinDNSMOSProReducedSize2024"/>, Distill-MOS<d-cite key="stahlDistillationPruningScalable2025"/>, SIGMOS<d-cite key="risteaICASSP2024Speech2025"/>, Torchaudio-Squim<d-cite key="kumarTorchaudioSquimReferenceLessSpeech2023"/>. -->
1. Non-intrusive SE metrics such as  DNSMOS<d-cite key="reddyDnsmosNonIntrusivePerceptual2021"/>, NISQA<d-cite key="mittagNISQADeepCNNSelfAttention2021"/>, UTMOS<d-cite key="saekiUTMOSUTokyoSaruLabSystem2022"/>, SCOREQ <d-cite key="NEURIPS2024_bece7e02"/>.
2. Intrusive SE metrics such as POLQA<d-cite key="POLQA-Beerends2013"/>, PESQ<d-cite key="rixPerceptualEvaluationSpeech2001"/>, ESTOI<d-cite key="jensenAlgorithmPredictingIntelligibility2016"/>, SDR<d-cite key="vincentPerformanceMeasurementBlind2006"/>, MCD<d-cite key="kubichekMelcepstralDistanceMeasure1993"/>, LSD<d-cite key="grayDistanceMeasuresSpeech1976"/>.
3. Downstream-task-independent metrics (e.g., Levenshtein phone similarity) for language-independent, speaker-independent, and task-independent evaluation.
4. Downstream-task-dependent metrics (e.g., speaker similarity, emotional similarity, language identification accuracy, word accuracy or WAcc) for evaluation of compatibility with different downstream tasks.

More details about the evaluation plan can be found in the [`Rules`](/urgent2026/rules) tab.

### Track 2: Speech Quality Assessment

The task of this track is to build a robust, generalizable speech quality assessment (SQA) model that predicts mean opinion scores (MOS) for enhanced speech. Systems will be evaluated using correlation and error metrics — MSE (Mean Square Error), LCC (linear correlation coefficient), SRCC (Spearman’s rank correlation coefficient), and KTAU (Kendall’s tau) — between the predicted MOS and the provided MOS labels. Data preparation scripts and baseline codes are available at https://github.com/urgent-challenge/urgent2026_challenge_track2. We allow the use of any public data and publicly available models. See the [`Rules`](/urgent2026/rules/) page for full details.

<br>

## Registration
Registration for the leaderboard and Google Form submission are required.
Refer to the [`Leaderboard`](/urgent2026/leaderboard) tab for more details.

<br>

## Paper submission

Participants can submit a paper describing the submitted SE system to the [Interspeech 2025](https://www.interspeech2025.org/home). **The submitted papers will go through the same review process** as the regular papers and will be indexed and included in the ISCA archive.

Please note that participants need to choose "**14.09 ICASSP 2026 URGENT Challenge Challenge [Challenge]**" as the subject area when submitting the paper. The registration platform is already available.


<br>

## Slack channel
We have a [Slack channel](https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g) for real-time communication.

<br>

## Links

### Data

- Please check our official [GitHub](https://github.com/urgent-challenge/urgent2026_challenge_track1) for more details.



### Baseline and Pre-training Models

- Please check our official [GitHub](https://github.com/urgent-challenge/urgent2026_challenge_track1) for more details.


### Leaderboard and registration

- Leaderboard: [https://urgent-challenge.com](https://urgent-challenge.com) [TODO]

### Contact

- Slack channel: [https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g](https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g)

<br>

## Motivation


Building on the success of the URGENT Challenge series, we propose the third URGENT Challenge at ICASSP 2026 to advance research in **U**niversality, **R**obustness, and **G**eneralizability for Speech Enhanceme**NT**.
The proposal for the third URGENT Challenge continues the momentum established by its predecessors. The first URGENT Challenge at NeurIPS 2024<d-cite key="zhangURGENTChallengeUniversality2024,zhang2025lessons"/> pioneered large-scale evaluation under diverse conditions, addressing variable sampling rates, multiple distortions, and comprehensive metrics; The second URGENT Challenge at Interspeech 2025<d-cite key="koheiurgent2025"/> significantly expanded the scope, incorporating more complex distortion types, multilingual speech data, and large-scale training resources (up to 60k hours). For the upcoming ICASSP 2026 URGENT Challenge, we introduce the following significant advances in speech enhancement (SE):

 1. **Data Curation in Large-scale Datasets**. Deep learning has become the predominant paradigm in SE<d-cite key="wangSupervisedSpeechSeparation2018a"/>, and its data-driven foundation relies on an implicit scaling hypothesis: expanding dataset volume should consistently improve performance. However, recent studies<d-cite key="zhangPerformancePlateausComprehensive2024,gonzalezEffectTrainingDataset2024a,koheiurgent2025"/>, including the [Interspeech 2025 URGENT Challenge](https://urgent-challenge.github.io/urgent2025/)<d-cite key="koheiurgent2025"/>, reveal a diminishing return that simply expanding the data scale cannot effectively improve the capabilities of SE models. Through a detailed analysis of the URGENT 2025 datasets, our recent work<d-cite key="liLessMoreData2025"/> has found that data curation is crucial for training SE models with large-scale data. Models trained on a strategy-curated subset of 700 hours are found to outperform models trained on the 2,500-hour full dataset thanks to higher data quality. Building on this insight, we hope that it will encourage participants in the third URGENT Challenge to explore more effective data curation strategies for larger datasets, ultimately allowing training of more powerful SE models in larger-scale datasets.

2. **More Diverse Speech Sources**. Conventional speech enhancement algorithms focus predominantly on several SE benchmark datasets, overlooking the rich diversity of speech sources encountered in real-world scenarios. 
Prior URGENT challenges addressed diversity through variable sampling rates, distortions, and recording environments (NeurIPS 2024), and further expanded to multilingual speech (Interspeech 2025).
The third URGENT Challenge will significantly broaden speech source diversity by incorporating critical yet understudied dimensions, including age diversity, accents, non-native pronunciations, whispered speech, singing voices, emotional speech, etc.

3. **Speech Quality Assessment (SQA) Track Based on Human Ratings**. In addition to promoting better SE systems, the ICASSP 2026 URGENT Challenge  introduces a new challenge track focused on building and evaluating perceptual quality prediction models. This track is motivated by the growing demand for automatic mean opinion score (MOS) prediction methods in the absence of ground-truth references, leveraging the extensive set of human ratings collected in prior challenges. Compared to existing SQA challenges such as VoiceMOS Challenge series and CHiME-7 UDASE Challenge, it features large-scale data with diverse distortions tailored for speech enhancement.


By incorporating these advancements, the ICASSP 2026 URGENT Challenge continues to **bridge the gap between academic research and practical applications**, ensuring that SE models not only perform well in controlled settings but also deliver robust and generalizable performance in the complex and dynamic conditions encountered in everyday use.


<!-- Similar issues can also be observed in other speech tasks such as automatic speech recognition (ASR), speech translation (ST), speaker verification (SV), and spoken language understanding (SLU).
Among them, speech enhancement is particularly vulnerable to mismatches since it is heavily reliant on paired clean/noisy speech data to achieve strong performance. Unsupervised speech enhancement that does not require groundtruth clean speech has been proposed to address this issue, but often merely brings benefit in a final finetuning stage<d-cite key="Employing-Xu2024"/>. Therefore, we focus on speech enhancement in this challenge to address the aforementioned problems. -->

<!-- Be sure to list "URGENT Challenge: Universality, Robustness, and Generalizability for EnhancemeNT" as your paper subject area when making a submission. -->

