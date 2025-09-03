---
layout: page
permalink: /track2/
title: "Track2: Speech Quality Assessment"
description:  
nav: true
nav_title: Track2
nav_order: 4
# toc: true
bibliography: track2.bib
dropdown: true
children: 
    - title: Overview
      permalink: /track2
    - title: Data
      permalink: /track2#data
    - title: Rules
      permalink: /track2#rules    
    - title: Baseline
      permalink: /track2#baseline
    - title: Submission
      permalink: /track2#submission
    - title: Ranking
      permalink: /track2#ranking
---

This track focuses on predicting the Mean Opinion Score (MOS) of speech processed by **speech enhancement systems**<d-footnote>This contrasts with existing challenges, which primarily targeted MOS prediction for text-to-speech (TTS) and voice conversion (VC) systems.</d-footnote>.

## Contents:

- [Data](#data)
  - [Training and Development Data](#training--development-data)
  - [Validation Data](#validation-data)
  - [Non-Blind Test Data](#blind-test-data)
  - [Blind Test Data](#non-blind-test-data)
- [Rules](#rules)
- [Baseline](#baseline)
- [Submission](#submission)
- [Ranking](#ranking)
  - [Overall ranking method](#overall-ranking-method)


## Data

#### Training / Development Data

We provide scripts to prepare and train on the following datasets in our [official baseline repo](https://github.com/urgent-challenge/urgent2026_challenge_track2). For ease of access, datasets with redistributable licenses are mirrored on Hugging Face. As most existing MOS datasets are designed for TTS or VC, participants are encouraged to use additional public datasets and apply SE-specific data curation.

<style>
/* Basic */

table {
  border-spacing: 0px;
  border-collapse: collapse;     /* Share borders between adjacent cells */
  width: 100%;
  max-width: 100%;
  margin-bottom: 15px;
  background-color: transparent; /* Change the background-color of table here */
  text-align: left;              /* Change the text-alignment of table here */
}

table td, table th {
  padding: .2em .5em;
}

th {
  font-weight: bold;
  border: 1px solid #cccccc;  /* Change the border-color of heading here */
}

td {
border: 1px solid #cccccc;  /* Change the border-color of cells here */
}


tr {
background-color: white; 
}

tr:nth-of-type(2n) {
  background-color: #eee;
}

tr th {
  background-color: white;
}

td {
  transition: background-color 200ms ease-in-out 0s;
}

td:hover {
  background-color: #fff176;
}

tr {
  border-top: 1px solid #cccccc;
  border-bottom: 1px solid #cccccc;
}
</style>
<table>
<colgroup>
<col>
<col>
<col>
<col>
<col>
<col>
</colgroup>
<thead>
  <tr>
    <th></th>
    <th>Corpus</th>
    <th>#Samples</th>
    <th>#Systems</th>
    <th>Duration (hours)</th>
    <th>Links</th>
    <th>License</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="11">Training</td>
    <td>BC19<d-cite key="BC19"/></td>
    <td>136</td>
    <td>21</td>
    <td>0.32</td>
    <td><a href="https://zenodo.org/records/6572573/files/main.tar.gz">[Original]</a></td>
    <td><a href="https://www.cstr.ed.ac.uk/projects/blizzard/data.html">Custom</a></td>
  </tr>
  <tr>
    <td>BVCC<d-cite key="BVCC"/></td>
    <td>4973</td>
    <td>175</td>
    <td>5.56</td>
    <td><a href="https://zenodo.org/records/6572573/files/ood.tar.gz">[Original]</a></td>
    <td><a href="https://www.cstr.ed.ac.uk/projects/blizzard/data.html">Custom</a></td>
  </tr>
  <tr>
    <td>NISQA<d-cite key="NISQA"/></td>
    <td>11020</td>
    <td>N/A</td>
    <td>27.21</td>
    <td><a href="https://zenodo.org/records/4728081/files/NISQA_Corpus.zip">[Original]</a></td>
    <td><a href="https://github.com/gabrielmittag/NISQA/wiki/NISQA-Corpus">Mixed</a></td>
  </tr>
  <tr>
    <td>PSTN<d-cite key="PSTN"/></td>
    <td>58709</td>
    <td>N/A</td>
    <td>163.08</td>
    <td><a href="https://challenge.blob.core.windows.net/pstn/train.zip">[Original]</a></td>
    <td>Unknown</td>
  </tr>
  <tr>
    <td>SOMOS<d-cite key="SOMOS"/></td>
    <td>14100</td>
    <td>181</td>
    <td>18.32</td>
    <td>
      <a href="https://zenodo.org/records/7378801/files/somos.zip">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/somos.zip">[Huggingface]</a>
    </td>
    <td>CC BY-NC-SA 4.0</td>
  </tr>
  <tr>
    <td>TCD-VoIP<d-cite key="TCD-VoIP"/></td>
    <td>384</td>
    <td>24</td>
    <td>0.87</td>
    <td>
      <a href="https://drive.usercontent.google.com/download?id=1rHJN34vP-W8SJtjpNUnx5RIks3o5L5he&export=download&authuser=0">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/TCD-VOIP.zip">[Huggingface]</a>
    </td>
    <td>CC BY-NC-SA 4.0</td>
  </tr>
  <tr>
    <td>Tencent<d-cite key="Tencent"/></td>
    <td>11563</td>
    <td>N/A</td>
    <td>23.51</td>
    <td>
      <a href="https://share.weiyun.com/B4IS0l3z">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/TencentCorpus.zip">[Huggingface]</a>
    </td>
    <td>Apache</td>
  </tr>
  <tr>
    <td>TMHINT-QI<d-cite key="TMHINT-QI"/></td>
    <td>12937</td>
    <td>98</td>
    <td>11.35</td>
    <td>
      <a href="https://drive.google.com/file/d/1TMDiz6dnS76hxyeAcCQxeSqqEOH4UDN0/view?usp=sharing">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/TMHINTQI.zip">[Huggingface]</a>
    </td>
    <td>MIT</td>
  </tr>
  <tr>
    <td>TTSDS2<d-cite key="TTSDS2"/></td>
    <td>460</td>
    <td>80</td>
    <td>0.96</td>
    <td>
      <a href="https://huggingface.co/datasets/ttsds/listening_test">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/ttsds2.zip">[Huggingface]</a>
    </td>
    <td>MIT</td>
  </tr>
  <tr>
    <td>urgent2024-sqa<d-cite key="UniVERSAExt"/><d-cite key="P808-Sach2025"/><d-cite key="URGENT-Zhang2024"/></td>
    <td>238</td>
    <td>238000</td>
    <td>429.34</td>
    <td>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent2024-sqa">[Huggingface]</a>
    </td>
    <td>CC BY-NC-SA 4.0</td>
  </tr>
  <tr>
    <td>urgent2025-sqa<d-cite key="UniVERSAExt"/><d-cite key="P808-Sach2025"/><d-cite key="Interspeech2025-Saijo2025"/></td>
    <td>100000</td>
    <td>100</td>
    <td>261.31</td>
    <td>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent2025-sqa">[Huggingface]</a>
    </td>
    <td>CC BY-NC-SA 4.0</td>
  </tr>
  <tr>
    <td rowspan="2">Development</td>
    <td>CHiME-7 UDASE Eval<d-cite key="CHiME-7-UDASE-Eval"/></td>
    <td>640</td>
    <td>5</td>
    <td>0.84</td>
    <td>
      <a href="https://zenodo.org/records/10418311/files/CHiME-7-UDASE-evaluation-data.zip">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/CHiME-7-UDASE-evaluation-data.zip">[Huggingface]</a>
    </td>
    <td>CC BY-SA 4.0</td>
  </tr>
</tbody>
</table>
 

#### Validation Data

The validation data is available on Hugging Face, and the data preparation script can be found in the official [GitHub repository](https://github.com/urgent-challenge/urgent2026_challenge_track2).

<!-- Although MOS labels for the validation set are provided for offline evaluation, we **strongly recommend** submitting your results to the leaderboard. This allows you to verify your system’s relative performance under our ranking protocol and ensures there are no misunderstandings regarding the evaluation procedure. -->

#### Non-Blind Test Data

The non-blind test data will be availabel after the non-blind test phase opens, please stay tuned.

#### Blind Test Data

The blind test data will be availabel after the non-blind test phase opens, please stay tuned.

---

## Baseline

Please refer to the official [GitHub repository](https://github.com/urgent-challenge/urgent2026_challenge_track1) for more details, which is a implmentation of [Uni-VERSA-Ext](https://arxiv.org/abs/2506.12260)<d-cite key="UniVERSAExt"/>.

You can also try the pretrained models on [Colab](https://colab.research.google.com/drive/1Y2OkPE0hGSG4XRj_b7RsmWMVSg4KkhM7)

- Other Suggested MOS Predictors
  - [UTMOS2 (domain dependent)](https://github.com/sarulab-speech/UTMOSv2)
  - [SSL-MOS](https://github.com/nii-yamagishilab/mos-finetune-ssl)
  - [NISQA](https://github.com/gabrielmittag/NISQA)
  - [LDNet (listener dependent)](https://github.com/unilight/LDNet)
  - [Uni-VERSA](https://huggingface.co/collections/espnet/universa-6834e7c0a28225bffb6e2526)


---

## Rules

1. During the first month of the challenge, participants may propose additional public datasets for inclusion in the official dataset list. The organizers will review all requests and may update the list accordingly. Any updates will be announced in the [`Notice`](/urgent2026/notice) tab.

2. Participants may use any publicly available dataset to develop their prediction systems. All datasets used must be clearly reported in the system description. The use of proprietary datasets—including collecting your own MOS ratings—is not permitted unless those resources are publicly released.<d-footnote>These rules follow the precedent set by the <a href="https://sites.google.com/view/voicemos-challenge/audiomos-challenge-2025">AudioMOS Challenge 2025</a>.</d-footnote>

3. Participants may incorporate publicly available models into their systems for tasks such as generating additional data, producing pseudo-MOS labels, initializing model parameters, or serving as system components. All such pre-trained resources must be explicitly cited and described in the system description.

4. The test data should only be used for evaluation purposes. **Techniques such as test-time adaptation, unsupervised domain adaptation, and self-training on the test data are NOT allowed**.

5. Registration is required to submit results to the challenge (Check the Check [`How to Participate`](/urgent2026/#how-to-participate) for more information tab for more information). Note that the team information (including affiliation, team name, and team members) should be provided when submitting the results. For detailed submission requirements, please check the [`Submission`](#submission) part.
    * Only the team name will be shown in the leaderboard, while the affiliation and team members will be kept confidential.<br/><br/>

---


## Submission

* Each submission should be **a zip file** containing two parts:
    1. a mos.scp file containing the mapping from audio name (without extension) to predicted mos score
    ```
    fileid_0001 4.031136
    fileid_0002 3.545564 
    ```
    2. a YAML (README.yaml) file containing the basic information about the submission (as listed below). The template can be found [here](/urgent2026/template_track2).
        * team information (team name, affiliation, team mambers)
        * description of the training & validation data used for the submission
        * description of pre-trained models used for the submission (if applicable)

> Submissions that fail to conform to the above requirements may be rejected.
>
> Should you encounter any problem during the submission, please feel free to [contact the organizers](mailto:urgent.challenge@gmail.com).

## Ranking

Systems will be evaluated based on both correlation and error metrics between the predicted Mean Opinion Scores (MOS) and the ground-truth MOS labels. The following metrics will be used:

- **Mean Squared Error (MSE)** – Measures the average squared difference between predicted and true scores.

- **Linear Correlation Coefficient (LCC)** – Assesses the strength of the linear relationship between predicted and true scores.

- **Spearman’s Rank Correlation Coefficient (SRCC) and Kendall’s Tau (KTAU)** – Evaluate the rank correlation between predicted and true scores

    <style type="text/css">
    .tg  {border:none;border-collapse:collapse;border-color:#ccc;border-spacing:0;}
    .tg td{background-color:#fff;border-color:#ccc;border-style:solid;border-width:0px;color:#333;
    font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;word-break:normal;}
    .tg th{background-color:#f0f0f0;border-color:#ccc;border-style:solid;border-width:0px;color:#333;
    font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
    .tg .tg-r2ra{background-color:#f9f9f9;border-color:inherit;text-align:left;vertical-align:middle}
    .tg .tg-51oy{background-color:#ffffff;border-color:#000000;text-align:center;vertical-align:middle}
    .tg .tg-rt8k{background-color:#ffffff;border-color:#000000;text-align:left;vertical-align:middle}
    .tg .tg-uzvj{border-color:inherit;font-weight:bold;text-align:center;vertical-align:middle}
    .tg .tg-g7sd{border-color:inherit;font-weight:bold;text-align:left;vertical-align:middle}
    .tg .tg-r6l2{background-color:#ffffff;border-color:inherit;text-align:center;vertical-align:middle}
    .tg .tg-0a7q{border-color:#000000;text-align:left;vertical-align:middle}
    .tg .tg-xwyw{border-color:#000000;text-align:center;vertical-align:middle}
    .tg .tg-kyy7{background-color:#f9f9f9;border-color:inherit;text-align:center;vertical-align:middle}
    .tg .tg-d459{background-color:#f9f9f9;border-color:inherit;text-align:left;vertical-align:middle}
    .tg .tg-ligs{background-color:#f9f9f9;border-color:inherit;text-align:center;vertical-align:middle}
    .tg .tg-rq3n{background-color:#ffffff;border-color:inherit;text-align:center;vertical-align:middle}
    .tg .tg-mfxt{background-color:#ffffff;border-color:inherit;text-align:left;vertical-align:middle}
    .tg .tg-qmuc{background-color:#ffffff;border-color:inherit;text-align:left;vertical-align:middle}
    </style>
    <table class="tg">
    <thead>
    <tr>
        <th class="tg-uzvj">Category</th>
        <th class="tg-g7sd">Metric</th>
        <th class="tg-uzvj">Value Range</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td class="tg-r6l2" rowspan="2">Error</td>
        <td class="tg-rt8k">System level MSE ↓</td>
        <td class="tg-51oy">[0, ∞)</td>
    </tr>
    <tr>
        <td class="tg-rt8k">Utterance level MSE ↓</td>
        <td class="tg-51oy">[0, ∞)</td>
    </tr>
    <tr>
        <td class="tg-r6l2" rowspan="2">Linear Correlation</td>
        <td class="tg-rt8k"> System level LCC ↑</td>
        <td class="tg-51oy">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-0a7q">Utterance level LCC ↑</td>
        <td class="tg-51oy">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-r6l2" rowspan="4">Rank Correlation</td>
        <td class="tg-rt8k"> System level SRCC ↑</td>
        <td class="tg-51oy">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-0a7q">Utterance level SRCC ↑</td>
        <td class="tg-51oy">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-rt8k"> System level KTAU ↑</td>
        <td class="tg-51oy">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-0a7q">Utterance level KTAU ↑</td>
        <td class="tg-51oy">[-1, 1]</td>
    </tr>

    </tbody>
    </table><br/>

### Overall ranking method

The overall ranking will be determined via the following procedure:

1. Calculate the `average score` of each metric for each submission.
2. Calculate the `per-metric ranking` based on the average score.
 * We adopt the dense ranking ("1223" ranking)<d-footnote><a href="https://en.wikipedia.org/wiki/Ranking#Dense_ranking_(%221223%22_ranking)">https://en.wikipedia.org/wiki/Ranking#Dense_ranking_(&quot;1223&quot;_ranking)</a></d-footnote> strategy for handling ties.
3. Calculate the `per-category ranking` by averaging the rankings within each category.
4. Calculate the `overall ranking` by averaging the `per-category rankings`.<br/><br/>

```python
# Step 1: Calculate the average score of each metric
scores = {}
for submission in all_submissions:
  scores[submission] = {}
  for category in metric_categories:
    for metric in category:
      scores[submission][metric] = mean([metric(each_sample) for each_sample in submission])

# Step 2: Calculate the per-metric ranking based on the average score
rank_per_metric = {}
rank_per_category = {}
for category in metric_categories:
  for metric in category:
    rank_per_metric[metric] = get_ranking([scores[submission][metric] for submission in all_submissions])

  # Step 3: Calculate the `per-category ranking` by averaging the rankings within each category
  rank_per_category[category] = get_ranking([rank_per_metric[metric] for metric in category])

# Step 4: Calculate the overall ranking by averaging the `per-category rankings`
rank_overall = get_ranking([rank_per_category[category] for category in metric_categories])
```
