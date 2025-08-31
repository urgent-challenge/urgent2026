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
    - title: Data
      permalink: /track2#data
    - title: Rules
      permalink: /track2#rules    
    - title: Ranking
      permalink: /track2#ranking
    - title: Baseline
      permalink: /track2#baseline
---

This track focuses on predicting the Mean Opinion Score (MOS) of speech processed by **speech enhancement systems**<d-footnote>This contrasts with existing challenges, which primarily targeted MOS prediction for text-to-speech (TTS) and voice conversion (VC) systems.</d-footnote>.

## Contents:

- [Rules](#rules)
- [Data](#data)
  - [Training and Development Data](#training--development-data)
  - [Validation Data](#validation-data)
  - [Non-Blind Test Data](#blind-test-data)
  - [Blind Test Data](#non-blind-test-data)
- [Ranking](#ranking)
- [Baseline](#baseline)
- [Submission](#submission)

## Rules

- Participants are required submit a system description after the challenge ends.

- Any public dataset may be used to develop your prediction system, and the datasets used must be reported in the system description. Use of proprietary datasets, including collecting your own MOS ratings, is not permitted unless the resources are publicly available<d-footnote>We followed rules from <a href="https://sites.google.com/view/voicemos-challenge/audiomos-challenge-2025">AudioMos Challenge 2025</a></d-footnote>.

- Participants may leverage publicly available pretrained models within their systems. All such pretrained resources must also be clearly cited and described in the system description.

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
    <td rowspan="10">Training</td>
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
  <tr>
    <td>URGENT24-SQA<d-cite key="UniVERSAExt"/><d-cite key="URGENT-Zhang2024"/><d-cite key="P808-Sach2025"/></td>
    <td>640</td>
    <td>5</td>
    <td>0.84</td>
    <td>
      <a href="https://zenodo.org/records/10418311/files/CHiME-7-UDASE-evaluation-data.zip">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/CHiME-7-UDASE-evaluation-data.zip">[Huggingface]</a>
    </td>
    <td>CC BY-SA 4.0</td>
  </tr>
  <tr>
    <td>URGENT25-SQA<d-cite key="UniVERSAExt"/><d-cite key="Interspeech2025-Saijo2025"/><d-cite key="P808-Sach2025"/></td>
    <td>640</td>
    <td>5</td>
    <td>0.84</td>
    <td>
      <a href="https://zenodo.org/records/10418311/files/CHiME-7-UDASE-evaluation-data.zip">[Original]</a>
      <a href="https://huggingface.co/datasets/urgent-challenge/urgent26_track2_sqa/resolve/main/CHiME-7-UDASE-evaluation-data.zip">[Huggingface]</a>
    </td>
    <td>CC BY-SA 4.0</td>
  </tr>
  <tr>
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

The validation data is the MOS dataset from the 1st URGENT challenge served on huggingface. The official data preparation scripts includes the preparation of the validation data.

#### Non-Blind Test Data

The non-blind test data will be availabel after the non-blind test phase opens, stay tuned.

#### Blind Test Data

The blind test data will be availabel after the non-blind test phase opens, stay tuned.


## Ranking

Systems will be evaluated based on both correlation and error metrics between the predicted Mean Opinion Scores (MOS) and the ground-truth MOS labels. The following metrics will be used:

- **Mean Squared Error (MSE)** – Measures the average squared difference between predicted and true MOS.

- **Linear Correlation Coefficient (LCC)** – Assesses the strength of the linear relationship between predicted and true scores.

- **Spearman’s Rank Correlation Coefficient (SRCC)** – Evaluates the monotonic relationship between rankings of predicted and true scores.

- **Kendall’s Tau (KTAU)** – Measures the ordinal association between the predicted and true rankings.

## Baseline

- Official Baseline
  - [Github repo](https://github.com/urgent-challenge/urgent2026_challenge_track2)
  - Paper: [Uni-VERSA](https://arxiv.org/abs/2505.20741); [Uni-VERSA-Ext](https://arxiv.org/abs/2506.12260)
  - [Colab](https://colab.research.google.com/drive/1Y2OkPE0hGSG4XRj_b7RsmWMVSg4KkhM7#scrollTo=fefCV1-iJ670)
- Other Suggested MOS Predictors
  - [UTMOS2 (domain dependent)](https://github.com/sarulab-speech/UTMOSv2)
  - [SSL-MOS](https://github.com/nii-yamagishilab/mos-finetune-ssl)
  - [NISQA](https://github.com/gabrielmittag/NISQA)
  - [LDNet (listener dependent)](https://github.com/unilight/LDNet)


## Submission