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


## How to Participate

1. Fill in the [google form](https://forms.gle/1GZHQprsB8CgdXc88). 
    * If you are new to URGENT challenges, You will receive credentials for [leaderboard](https://urgent-challenge.com).
    * Otherwise, you will get notifications when approved for leaderboard submission.
2. Check [Track 1 (Universal Speech Enhancement)](/urgent2026/track1) and [Track 2 (Speech Quality Assessment)](/urgent2026/track2) for rules, data and baseline.
3. Log in and submit results to [Track 1](https://urgent-challenge.com/competitions/15) and [Track 2](https://urgent-challenge.com/competitions/17)

<br>


## Motivation

[CALL FOR PARTICIPANTS](/urgent2026/assets/pdf/call_for_participants.pdf)


The ICASSP 2026 URGENT challenge (**U**niversal, **R**obust and **G**eneralizable speech **E**nhanceme**NT**) is a speech enhancement challenge held at [**ICASSP 2026 SP Grand Challenge**](https://2026.ieeeicassp.org/call-for-sp-grand-challenge-proposals/). We aim to build universal speech enhancement models for unifying speech processing in a wide variety of conditions.

The ICASSP 2026 URGENT Challenge aims to further promote the research on **U**niversal, **R**obust and **G**eneralizable speech **E**nhanceme**NT**. 
This year's challenge focuses on the following aspects:

1. **Data Curation in Large-scale Datasets**. Some recent studies reveal diminishing returns from scaling datasets for speech enhancement (SE)<d-cite key="zhangPerformancePlateausComprehensive2024,gonzalezEffectTrainingDataset2024a,koheiurgent2025"/>, and data curation is crucial for training SE models with large-scale data<d-cite key="liLessMoreData2025"/>. The challenge aims to draw people's attention to this phenomenon, so as to make better use of large-scale data for speech enhancement.

2. **More Diverse Speech Sources**. While prior URGENT challenges addressed speech diversity through acoustics and language, the third challenge expands to critical understudied dimensions like age, accents, whispered/singing voices, and emotional speech.

3. **Speech Quality Assessment (SQA) Track Based on Human Ratings**. The ICASSP 2026 URGENT Challenge introduces a new track for perceptual quality prediction models using human ratings, featuring large-scale, distortion-diverse data tailored for SE—unlike existing SQA challenges.

<br>



## Task Introduction

### Track 1: Speech Enhancement


<div style="text-align: center;">
    <img alt="introduction" src="/urgent2026/assets/img/track1.png" style="max-width: 95%;" />
</div>

The task of this challenge is to build **a single speech enhancement system** to adaptively handle input speech with different distortions (corresponding to different SE subtasks), different domains (e.g., language, age, accents, emotion), different input formats (e.g., sampling frequencies) in different acoustic environments (e.g., noise and reverberation).

The large-scale training data will consist of several public corpora of speech, noise, and RIRs. 
We provide a 700-hour curated training set as a baseline. 
And we encourage participants to explore advanced data curation techniques to utilize a large-scale noisy training dataset.
Please check the [Track1](/urgent2026/track1) page for more details.

<br>


### Track 2: Speech Quality Assessment

<div style="text-align: center;">
    <img alt="introduction" src="/urgent2026/assets/img/track2.png" style="max-width: 95%;" />
</div>

The task of this track is to build a robust, generalizable speech quality assessment (SQA) model that predicts mean opinion scores (MOS) for enhanced speech. Systems will be evaluated using correlation and error metrics — MSE (Mean Squared Error), LCC (linear correlation coefficient), SRCC (Spearman’s rank correlation coefficient), and KTAU (Kendall’s tau) — between the predicted MOS and the provided MOS labels. Data preparation scripts and baseline codes are available at https://github.com/urgent-challenge/urgent2026_challenge_track2. We allow the use of any public data and publicly available models. See the [`Track2`](/urgent2026/track2/) page for full details.

<br>



### Contact

- We have a [Slack channel](https://join.slack.com/t/urgentchallenge/shared_invite/zt-2jy2stg7q-79AGeAY0CpKHRl7r4X0e6g) for real-time communication.

- For any further questions, drop an email at urgent.challenge@gmail.com.

<!-- 
## Motivation


Building on the success of the URGENT Challenge series, we propose the third URGENT Challenge at ICASSP 2026 to advance research in **U**niversality, **R**obustness, and **G**eneralizability for Speech Enhanceme**NT**.
The proposal for the third URGENT Challenge continues the momentum established by its predecessors. The first URGENT Challenge at NeurIPS 2024<d-cite key="zhangURGENTChallengeUniversality2024,zhang2025lessons"/> pioneered large-scale evaluation under diverse conditions, addressing variable sampling rates, multiple distortions, and comprehensive metrics; The second URGENT Challenge at Interspeech 2025<d-cite key="koheiurgent2025"/> significantly expanded the scope, incorporating more complex distortion types, multilingual speech data, and large-scale training resources (up to 60k hours). For the upcoming ICASSP 2026 URGENT Challenge, we introduce the following significant advances in speech enhancement (SE):

 1. **Data Curation in Large-scale Datasets**. Deep learning has become the predominant paradigm in SE<d-cite key="wangSupervisedSpeechSeparation2018a"/>, and its data-driven foundation relies on an implicit scaling hypothesis: expanding dataset volume should consistently improve performance. However, recent studies<d-cite key="zhangPerformancePlateausComprehensive2024,gonzalezEffectTrainingDataset2024a,koheiurgent2025"/>, including the [Interspeech 2025 URGENT Challenge](https://urgent-challenge.github.io/urgent2025/)<d-cite key="koheiurgent2025"/>, reveal a diminishing return that simply expanding the data scale cannot effectively improve the capabilities of SE models. Through a detailed analysis of the URGENT 2025 datasets, our recent work<d-cite key="liLessMoreData2025"/> has found that data curation is crucial for training SE models with large-scale data. Models trained on a strategy-curated subset of 700 hours are found to outperform models trained on the 2,500-hour full dataset thanks to higher data quality. Building on this insight, we hope that it will encourage participants in the third URGENT Challenge to explore more effective data curation strategies for larger datasets, ultimately allowing training of more powerful SE models in larger-scale datasets.

2. **More Diverse Speech Sources**. Conventional speech enhancement algorithms focus predominantly on several SE benchmark datasets, overlooking the rich diversity of speech sources encountered in real-world scenarios. 
Prior URGENT challenges addressed diversity through variable sampling rates, distortions, and recording environments (NeurIPS 2024), and further expanded to multilingual speech (Interspeech 2025).
The third URGENT Challenge will significantly broaden speech source diversity by incorporating critical yet understudied dimensions, including age diversity, accents, non-native pronunciations, whispered speech, singing voices, emotional speech, etc.

3. **Speech Quality Assessment (SQA) Track Based on Human Ratings**. In addition to promoting better SE systems, the ICASSP 2026 URGENT Challenge  introduces a new challenge track focused on building and evaluating perceptual quality prediction models. This track is motivated by the growing demand for automatic mean opinion score (MOS) prediction methods in the absence of ground-truth references, leveraging the extensive set of human ratings collected in prior challenges. Compared to existing SQA challenges such as VoiceMOS Challenge series and CHiME-7 UDASE Challenge, it features large-scale data with diverse distortions tailored for speech enhancement.


By incorporating these advancements, the ICASSP 2026 URGENT Challenge continues to **bridge the gap between academic research and practical applications**, ensuring that SE models not only perform well in controlled settings but also deliver robust and generalizable performance in the complex and dynamic conditions encountered in everyday use.

-->

<!-- Similar issues can also be observed in other speech tasks such as automatic speech recognition (ASR), speech translation (ST), speaker verification (SV), and spoken language understanding (SLU).
Among them, speech enhancement is particularly vulnerable to mismatches since it is heavily reliant on paired clean/noisy speech data to achieve strong performance. Unsupervised speech enhancement that does not require groundtruth clean speech has been proposed to address this issue, but often merely brings benefit in a final finetuning stage<d-cite key="Employing-Xu2024"/>. Therefore, we focus on speech enhancement in this challenge to address the aforementioned problems. -->

<!-- Be sure to list "URGENT Challenge: Universality, Robustness, and Generalizability for EnhancemeNT" as your paper subject area when making a submission. -->

