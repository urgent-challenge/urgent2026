---
layout: page
permalink: /track1/
nav_title: Track1
title: "Track1: Universal Speech Enhancement"
description:  
nav: true
nav_order: 3
# toc: true
bibliography: track1.bib
dropdown: true
children: 
    - title: Baseline
      permalink: /track1#baseline
    - title: Data
      permalink: /track1#datasets
    - title: Rules and Ranking
      permalink: /track1#rules-and-ranking
---

## Contents:

- [Contents:](#contents)
- [Baseline](#baseline)
- [Datasets](#datasets)
  - [Brief data description:](#brief-data-description)
  - [Detailed data description:](#detailed-data-description)
- [Rules and Ranking](#rules-and-ranking)



## Baseline


Please refer to the official [GitHub repository](https://github.com/urgent-challenge/urgent2026_challenge_track1) for more details.






**Discriminative Baseline.** We provide an adaptive STFT-based SFI<d-cite key="Sampling-Paulus2022,Toward-Zhang2023,Improving-Zhang2024"/>  BSRNN <d-cite key="Music-Luo2023,Efficient-Yu2023,High-Yu2023"/> as the discriminative baseline. The model is available at [here](https://github.com/urgent-challenge/urgent2026_challenge_track1). The details of the baseline training can be found in our [recent ASRU paper](https://arxiv.org/abs/2506.23859) <d-cite key="liLessMoreData2025"/>.

**Generative Baseline.** We follow a recent work named FlowSE<d-cite key="leeFlowSEFlowMatchingbased2025"/> to build generative SE models. It extends the flow matching method<d-cite key="lipmanFlowMatchingGenerative2023"/> to a conditional flow matching model that generates clean speech conditioned by the noisy speech. We reimplement an [improved BSRNN](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/baseline_code/models/bsrnn_flowse.py) to estimate the conditional vector field. The model is available at [here](https://github.com/urgent-challenge/urgent2026_challenge_track1), and the training details of the generative baseline model can be found in the [paper](https://arxiv.org/abs/2506.23859) <d-cite key="liLessMoreData2025"/>.

<br>


## Datasets
### Brief data description:

The training and validation data are both simulated by using several public speech/noise/rir corpora (see the table below for more details).
We provide the [data preparation pipeline](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/utils/prepare_train_data.sh) with the [official baseline](https://github.com/urgent-challenge/urgent2026_challenge_track1), which automatically downloads and pre-processes the data.

Non-blind/bind test set will be released later, check the [timeline](/urgent2026/timeline/) page for more details.

### Detailed data description:

The training and validation data are both simulated based on the following source data.
Based on the [dataset of the 2nd URGENT challenge](https://urgent-challenge.github.io/urgent2025/data/), we conducted a data selection using the data filtering method proposed in a recent paper <d-cite key="liLessMoreData2025"/>.

**It is noted that we encourage you to explore better ways of data selection and utilization in this challenge.** In addition to the data and filtering methods provided by our baseline, you can make use of larger-scale datasets, such as the [track2 data](https://urgent-challenge.github.io/urgent2025/data/) from the 2nd URGENT challenge, or other allowed data (please check it in the [rules](/urgent2026/rules/) section).

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

th {
font-weight: bold;
border: 1px solid #cccccc;  /* Change the border-color of heading here */
padding: 8px;
}

td {
border: 1px solid #cccccc;  /* Change the border-color of cells here */
padding: 8px;
}

/* Stylized */

/* Adding Striped Effect for even rows */

tr {
/* background-color: transparent; Change the default background-color of rows here */
background-color: white; /* Change the default background-color of rows here */
}

tr:nth-of-type(2n) {
background-color: #f6f8fa;  /* Change the background-color of even rows here */
}

/* Reset styles for the shortcut helper */
.light-keys tr:nth-of-type(2n) {background-color: black;}
.light-keys tr:hover {background-color: black;}
.light-keys table {border: none;}
.light-keys tr {border: none;}
.light-keys td {border: none;}
.light-keys th {border: none;}

tr th {
background-color: white;    /* Change the background-color of heading here */
}

/* Adding Hover Effect for rows */

tr {
-moz-transition: background-color 300ms ease-in-out 0s;
-ms-transition: background-color 300ms ease-in-out 0s;
-o-transition: background-color 300ms ease-in-out 0s;
-webkit-transition: background-color 300ms ease-in-out 0s;
transition: background-color 300ms ease-in-out 0s;
}

tr:hover {
background-color: #fff176;  /* Change the hover background-color of rows here */
}

/* Removing left and right border of rows for modern UIs */

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
    <th>Type</th>
    <th>Corpus</th>
    <th>Condition</th>
    <th>Sampling Frequency (kHz)</th>
    <th>Duration of in 2nd URGENT</th>
    <th>Duration of in 3rd URGENT</th>
    <th>License</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="10">Speech</td>
    <td>LibriVox data from <a href="https://github.com/microsoft/DNS-Challenge/blob/master/download-dns-challenge-5-headset-training.sh">DNS5 challenge</a></td>
    <td>Audiobook</td>
    <td>8~48</td>
    <td>~350 h</td>
    <td>~150 h</td>
    <td>CC BY 4.0</td>
  </tr>
  <tr>
    <td>LibriTTS reading speech</td>
    <td>Audiobook</td>
    <td>8~24</td>
    <td>~200 h</td>
    <td>~109 h</td>
    <td>CC BY 4.0</td>
  </tr>
  <tr>
    <td>VCTK reading speech</td>
    <td>Newspaper, etc.</td>
    <td>48</td>
    <td>~80 h</td>
    <td>~44 h</td>
    <td>ODC-BY</td>
  </tr>
  <tr>
    <td>EARS speech</td>
    <td>Studio recording</td>
    <td>48</td>
    <td>~100 h</td>
    <td>~16 h</td>
    <td> CC-NC 4.0</td>
  </tr>
  <tr>
    <td>Multilingual Librispeech (de, en, es, fr)<d-footnote>We collected less compressed MLS from LibriVox, which have higher audio quality than the original MLS for ASR.</d-footnote></td>
    <td>Audiobook</td>
    <td>8~48</td>
    <td>~450 (48600) h</td>
    <td>~129 h</td>
    <td>CC0</td>
  </tr>
  <tr>
    <td>CommonVoice 19.0 (de, en, es, fr, zh-CN)</td>
    <td>Crowd-sourced voices</td>
    <td>8~48</td>
    <td>~1300 (9500) h</td>
    <td>~250 h</td>
    <td>CC0</td>
  </tr>

  <tr>
    <td>NNCES</td>
    <td>Children speech</td>
    <td>44.1</td>
    <td>-</td>
    <td>~20 h</td>
    <td>CC0</td>
  </tr>

  <tr>
    <td>SeniorTalk</td>
    <td>Elderly speech</td>
    <td>16</td>
    <td>-</td>
    <td>~50 h</td>
    <td>CC BY-NC-SA 4.0</td>
  </tr>

  <tr>
    <td>VocalSet</td>
    <td>Singing voice</td>
    <td>44.1</td>
    <td>-</td>
    <td>~10 h</td>
    <td>CC BY 4.0</td>
  </tr>

  <tr>
    <td>ESD</td>
    <td>Emotional speech</td>
    <td>16</td>
    <td>-</td>
    <td>~30 h</td>
    <td>non-commercial, <a href="https://github.com/HLTSingapore/Emotional-Speech-Data">custom</a> <d-footnote>You need to sign a license to obtain this dataset.</d-footnote> </td>
  </tr>
  <!-- <tr>
    <td>Other RIRs simulated by participants</td>
    <td>-</td>
    <td>8~48</td>
    <td>-</td>
    <td>-</td>
  </tr> -->
</tbody>
</table>

For the noise source and RIRs, we follow the same configuration as in the [2nd URGENT challenge](https://urgent-challenge.github.io/urgent2025/data/).

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
    <th>Type</th>
    <th>Corpus</th>
    <th>Condition</th>
    <th>Sampling Frequency (kHz)</th>
    <th>Duration of in 2nd URGENT</th>
    <th>License</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="5">Noise</td>
    <td>Audioset+FreeSound noise in DNS5 challenge</td>
    <td>Crowd-sourced + Youtube</td>
    <td>8~48</td>
    <td>~180 h</td>
    <td>CC BY 4.0</td>
  </tr>
  <tr>
    <td>WHAM! noise</td>
    <td>4 Urban environments</td>
    <td>48</td>
    <td>~70 h</td>
    <td>CC BY-NC 4.0</td>
  </tr>
  <tr>
    <td>FSD50K (human voice filtered)</td>
    <td>Crowd-sourced</td>
    <td>8~48</td>
    <td>~100 h</td>
    <td>CC0, CC-BY, CC-BY-NC, CC Sampling+</td>
  </tr>
  <tr>
    <td>Free Music Archive (medium)</td>
    <td>Free Music Archive (directed by WFMU) </td>
    <td>8~44.1</td>
    <td>~200 h</td>
    <td>CC</td>
  </tr>
  <tr>
    <td>Wind noise simulated by participants</td>
    <td>-</td>
    <td>any</td>
    <td>-</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td rowspan="2">RIR</td>
    <td>Simulated RIRs from DNS5 challenge</td>
    <td><a href="https://www.openslr.org/28/">SLR28</a></td>
    <td>48</td>
    <td>~60k samples</td>
    <td>CC BY 4.0</td>
  </tr>
  <tr>
    <td>RIRs simulated by participants</td>
    <td>-</td>
    <td>any</td>
    <td>-</td>
    <td>N/A</td>
  </tr>

</tbody>
</table>


Note that external data, not included in the above listed datasets cannot be used for the purpose of this challenge. 
However we allow participants to simulate their own RIRs using existing tools 3 for generating the training data. The participants can also propose publicly available real recorded RIRs to be included in the above data list during the grace period. See [rules](#rules-and-ranking) section for more details.


**Data selection and Simulation.** We apply the data selection to the track1 data of the [2nd URGENT](https://urgent-challenge.github.io/urgent2025/) using the data filtering method proposed in the recent paper <d-cite key="liLessMoreData2025"/>. The selected data list is available at [here](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/meta/train_selected_700h). The speech source from NNCES, SeniorTalk, VocalSet, and ESD is not filtered.

Note that the data filtering of paper <d-cite key="liLessMoreData2025"/> is obviously not the best method to utilize the large-scale dataset for SE.
**The goal of this challenge is to encourage participants to develop how to better leverage large-scale data** to improve the final SE performance.

The simulation data can be generated as follows:

1. In the first step, a manifest `meta.tsv` is first generated by [`simulation/generate_data_param.py`](https://github.com/urgent-challenge/urgent2025_challenge/blob/main/simulation/generate_data_param.py) from the given list of speech, noise, and room impulse response (RIR) samples. It specifies how each sample will be simulated, including the type of distortion to be applied, the speech/noise/RIR sample to be used, the signal-to-noise ratio (SNR), the random seed, and so on.

2. In the second step, the simulation can be done in parallel via [`simulation/simulate_data_from_param.py`](https://github.com/urgent-challenge/urgent2025_challenge/blob/main/simulation/simulate_data_from_param.py) for different samples according to the manifest while ensuring reproducibility. This procedure can be used to generate training and validation datasets.

3. By default, we applied a [high-pass filter](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/simulation/simulate_data_from_param.py) to the speech signals since we have noticed that there is high-energy noise in the infrasound frequency band in some speech sources. You can turn it off by setting `highpass=False` in your simulation.

For the training set, **we recommend dynamically generating degraded speech samples during training** to increase the data diversity.






<img alt="framework" src="/urgent2026/assets/img/framework.jpg" style="max-width: 100%;"/>

**Distortions Model.** As depicted in the figure above, we design a distortion model (simulation stage) <d-math>\mathcal{F}(\cdot)</d-math> to unify the data format for different distortion types, such that different speech enhancement (SE) sub-tasks can share a consistent input/output processing. In particular, we ensure that the sampling frequency (SF) at the output of the distortion model (degraded speech) is always equal to that of its input.

During training and inference, the processing of different SFs is supported for both <u>conventional SE models</u> (lower-right) that usually only operate at one SF and <u>adaptive STFT-based sampling-frequency-independent (SFI) SE models</u> (upper-right) that can directly handle different SFs.

* For conventional SE models (e.g., Conv-TasNet<d-cite key="Conv_TasNet-Luo2019"/>), we always **upsample** its input (degraded speech) to the highest SF (48 kHz) so that the model only needs to operate at 48 kHz. The model output (48 kHz) is then **downsampled** to the same SF as the degraded speech.
* For adaptive STFT-based SFI<d-cite key="Sampling-Paulus2022,Toward-Zhang2023,Improving-Zhang2024"/> SE models (e.g., BSRNN<d-cite key="Music-Luo2023,Efficient-Yu2023,High-Yu2023"/>, TF-GridNet<d-cite key="TF_GridNet-Wang2023,TF_GridNet2-Wang2023"/>), we directly feed the degraded speech of different SFs into the model, which can adaptively adjust their STFT/iSTFT configuration according to the SF and generate the enhanced signal with the same SF.
<br>

In the challenge, the SE system has to address the following seven distortions:

1. Additive noise
2. Reverberation
3. Clipping
4. Bandwidth limitation
5. Codec distortion
6. Packet loss
7. Wind noise

We provide an example simulation script as [`simulation/simulate_data_from_param.py`](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/simulation/simulate_data_from_param.py).



<br>

## Rules and Ranking

1. When generating the training and validation datasets, **ONLY the speech, noise, and room impulse response (RIR) corpora listed in the [`Data`](/urgent2025/data) tab shall be used to ensure a fair comparison** and proper understanding of various SE approaches.
    

    * The first month of the challenge will be a grace period when participants can propose additional public datasets to be included in the list. We (organizers) will reply to the requests and may update the list. Updates will be recorded in the [`Notice`](/urgent2026/notice) tab. 
    
    * **It is NOT allowed to use pre-trained speech enhancement models trained on other than official Challenge data**.
      * However, it IS allowed to use a pre-trained model trained on the official challenge data (e.g., [URGENT 2024](https://huggingface.co/wyz/tfgridnet_for_urgent24) / [URGENT 2025](https://huggingface.co/kohei0209/tfgridnet_urgent25) / [URGENT 2026](TODO link)  official baseline ) 
    
    * Although the speech enhancement model should only be trained on the listed data, we allow the use of pre-trained foundation models such as [HuBERT](https://github.com/facebookresearch/fairseq/blob/main/examples/hubert/README.md), [WavLM](https://github.com/microsoft/unilm/blob/master/wavlm/README.md), [EnCodec](https://github.com/facebookresearch/encodec), [Llama](https://llama.meta.com/llama-downloads/), and so on. **We also allow the use of a pretrained speech enhancement/restoration model to improve the quality of clean speech for simulation.** The use of all pre-trained models must meet the following requirements:
        * They are publicly available before the challenge begins
        * They are explicitly mentioned in the submitted system description.
        * Note:
            * Their parameters can be fine-tuned on the listed data.
            * It is not allowed to fine-tune any model, be it pre-trained or not, on any extra data other than the listed data.<br/><br/>

    * **If you are unsure whether the pre-trained model you would like to use is allowed, please reach out to the organizers.**

2. We allow participants to simulate their own RIRs using existing tools<d-footnote>For example, <a href="https://github.com/ehabets/RIR-Generator">RIR-Generator</a>, <a href="https://github.com/LCAV/pyroomacoustics">pyroomacoustics</a>, <a href="https://github.com/DavidDiazGuerra/gpuRIR">gpuRIR</a>,  and so on.</d-footnote> for generating the training data. The participants can also propose publicly available real recorded RIRs to be included in the above data list during the grace period (See [`Timeline`](/urgent2026/timeline)).
> Note: If participants used additional RIRs to train their model, the related information should be provided in the README.yaml file in the submission. Check the [template](/urgent2026/template) for more information.

3. We allow participants to simulate wind noise using some tools such as <a href="https://github.com/audiolabs/SC-Wind-Noise-Generator/tree/main">SC-Wind-Noise-Generator</a>. In default, the simulation script in our repository simulates 200 and 100 wind noises for training and validation for each sampling frequency. The configuration can be easily changed in <a href="https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/conf/wind_noise_simulation_train.yaml">wind_noise_simulation_train.yaml</a> and <a href="https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/conf/wind_noise_simulation_validation.yaml">wind_noise_simulation_validation.yaml</a>

4. The test data should only be used for evaluation purposes. **Techniques such as test-time adaptation, unsupervised domain adaptation, and self-training on the test data are NOT allowed**.


5. There is no constraint on the latency or causality of the developed system in this challenge. Any type of model can be used as long as it conforms to the other rules as listed on this page.


6. Registration is required to submit results to the challenge (Check the [`Leaderboard`](/urgent2025/leaderboard) tab for more information). Note that the team information (including affiliation, team name, and team members) should be provided when submitting the results. For detailed submission requirements, please check the [`Submission`](/urgent2025/submission) tab.
    * Only the team name will be shown in the leaderboard, while the affiliation and team members will be kept confidential.<br/><br/>


7. The following evaluation metrics will be calculated for evaluation.
    
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
        <th class="tg-uzvj">Need Reference Signals?</th>
        <th class="tg-uzvj">Supported Sampling Frequencies</th>
        <th class="tg-uzvj">Value Range</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td class="tg-r6l2" rowspan="4">Non-intrusive SE metrics</td>
        <td class="tg-rt8k"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_dnsmos.py">DNSMOS</a> ↑<d-cite key="DNSMOS-Reddy2022"/></td>
        <td class="tg-51oy">❌</td>
        <td class="tg-51oy">16 kHz</td>
        <td class="tg-51oy">[1, 5]</td>
    </tr>
    <tr>
        <td class="tg-0a7q"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_nisqa.py">NISQA</a> ↑<d-cite key="NISQA-Mittag2021"/></td>
        <td class="tg-xwyw"><span style="font-weight:400;font-style:normal;text-decoration:none">❌</span></td>
        <td class="tg-xwyw">48 kHz</td>
        <td class="tg-xwyw">[1, 5]</td>
    </tr>
    <tr>
        <td class="tg-0a7q"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_mos.py">UTMOS</a> ↑<d-cite key="UTMOS-SAEKI2022"/></td>
        <td class="tg-xwyw"><span style="font-weight:400;font-style:normal;text-decoration:none">❌</span></td>
        <td class="tg-xwyw">16 kHz</td>
        <td class="tg-xwyw">[1, 5]</td>
    </tr>
    <!-- new -->
    <tr>
        <td class="tg-0a7q"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_mos.py">ScoreQ</a> ↑<d-cite key="NEURIPS2024_bece7e02"/></td>
        <td class="tg-xwyw"><span style="font-weight:400;font-style:normal;text-decoration:none">❌</span></td>
        <td class="tg-xwyw">16 kHz</td>
        <td class="tg-xwyw">[0.0, 1.0]</td>
    </tr>
    <!-- <tr>
        <td class="tg-0a7q"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_mos.py">Distill-MOS</a> ↑<d-cite key="stahlDistillationPruningScalable2025"/></td>
        <td class="tg-xwyw"><span style="font-weight:400;font-style:normal;text-decoration:none">❌</span></td>
        <td class="tg-xwyw">16 kHz</td>
        <td class="tg-xwyw">[1, 5]</td>
    </tr>
    <tr>
        <td class="tg-0a7q"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_mos.py">SIGMOS</a> ↑<d-cite key="risteaICASSP2024Speech2025"/></td>
        <td class="tg-xwyw"><span style="font-weight:400;font-style:normal;text-decoration:none">❌</span></td>
        <td class="tg-xwyw">16 kHz</td>
        <td class="tg-xwyw">[1, 5]</td>
    </tr>
    <tr>
        <td class="tg-0a7q"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_mos.py">Torchaudio-Squim SDR</a> ↑<d-cite key="kumarTorchaudioSquimReferenceLessSpeech2023"/></td>
        <td class="tg-xwyw"><span style="font-weight:400;font-style:normal;text-decoration:none">❌</span></td>
        <td class="tg-xwyw">16 kHz</td>
        <td class="tg-xwyw"> (-∞, +∞) </td>
    </tr> -->
    <!-- new -->

    <tr>
        <td class="tg-kyy7" rowspan="6">Intrusive SE metrics</td>
        <td class="tg-d459"><a href="http://www.polqa.info" style="color:#e97c36;">POLQA</a><d-footnote>This metric will only be used for evaluation of the final blind test set.</d-footnote> ↑</td>
        <td class="tg-kyy7">✔</td>
        <td class="tg-kyy7"><span style="font-weight:400;font-style:normal;text-decoration:none">8~48 kHz</span></td>
        <td class="tg-kyy7"><span style="font-weight:400;font-style:normal;text-decoration:none">[1, 5]</span></td>
    </tr>
    <tr>
        <td class="tg-d459"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_intrusive_se_metrics.py">PESQ</a> ↑<d-cite key="PESQ-Rix2001"/></td>
        <td class="tg-kyy7">✔</td>
        <td class="tg-kyy7"><span style="font-weight:400;font-style:normal;text-decoration:none">{8, 16} kHz</span></td>
        <td class="tg-kyy7"><span style="font-weight:400;font-style:normal;text-decoration:none">[-0.5, 4.5]</span></td>
    </tr>
    <tr>
        <td class="tg-r2ra"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_intrusive_se_metrics.py">ESTOI</a> ↑<d-cite key="ESTOI-Jensen2016"/></td>
        <td class="tg-ligs">✔</td>
        <td class="tg-ligs"><span style="font-weight:400;font-style:normal;text-decoration:none">10 kHz</span></td>
        <td class="tg-ligs">[0, 1]</td>
    </tr>
    <tr>
        <td class="tg-d459"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_intrusive_se_metrics.py">SDR</a> ↑<d-cite key="SDR-Vincent2006"/></td>
        <td class="tg-kyy7">✔</td>
        <td class="tg-kyy7">Any</td>
        <td class="tg-kyy7">(-∞, +∞)</td>
    </tr>
    <tr>
        <td class="tg-r2ra"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_intrusive_se_metrics.py">MCD</a> ↓<d-cite key="MCD-Kubichek1993"/></td>
        <td class="tg-ligs">✔</td>
        <td class="tg-ligs">Any</td>
        <td class="tg-ligs">[0, +∞)</td>
    </tr>
    <tr>
        <td class="tg-d459"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_intrusive_se_metrics.py">LSD</a> ↓<d-cite key="LSD-Gray1976"/></td>
        <td class="tg-kyy7">✔</td>
        <td class="tg-kyy7">Any</td>
        <td class="tg-kyy7">[0, +∞)</td>
    </tr>
    <tr>
        <td class="tg-rq3n" rowspan="2">Downstream-task-independent metrics</td>
        <td nowrap class="tg-mfxt"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_speechbert_score.py">SpeechBERTScore</a><d-footnote>To evaluate multilingual speech, we adopt the MHuBERT-147 backend for calculating the SpeechBERTScore, which differs from its defalut backend (WavLM-Large).</d-footnote> ↑<d-cite key="SpeechBERTScore-Saeki2024"/></td>
        <td class="tg-rq3n">✔</td>
        <td class="tg-rq3n">16 kHz</td>
        <td class="tg-rq3n">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-qmuc"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_phoneme_similarity.py">LPS</a> ↑<d-cite key="Evaluation-Pirklbauer2023"/></td>
        <td class="tg-r6l2">✔</td>
        <td class="tg-r6l2">16 kHz</td>
        <td class="tg-r6l2"><span style="font-weight:400;font-style:normal;text-decoration:none">(-∞, 1]</span></td>
    </tr>
    <tr>
        <td class="tg-ligs" rowspan="4">Downstream-task-dependent metrics</td>
        <td class="tg-r2ra"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_speaker_similarity.py">Speaker Similarity</a> ↑</td>
        <td class="tg-ligs">✔</td>
        <td class="tg-ligs">16 kHz</td>
        <td class="tg-ligs">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-d459"><a href="">EMOTION2VEC Similarity</a> ↑</td>
        <td class="tg-kyy7">❌</td>
        <td class="tg-kyy7">16 kHz</td>
        <td class="tg-kyy7">[-1, 1]</td>
    </tr>
    <tr>
        <td class="tg-d459"><a href="">Language identification accuracy</a> ↑</td>
        <td class="tg-kyy7">❌</td>
        <td class="tg-kyy7">16 kHz</td>
        <td class="tg-kyy7">[0, 1]</td>
    </tr>
    <tr>
        <td class="tg-d459"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_wer.py">Character accuracy (1 - CER)</a><d-footnote></d-footnote> ↑</td>
        <td class="tg-kyy7">❌</td>
        <td class="tg-kyy7">16 kHz</td>
        <td class="tg-kyy7">(-∞, 1]</td>
    </tr>
    <tr>
        <td class="tg-r6l2" rowspan="1">Subjective SE metrics</td>
        <td class="tg-rt8k"><a href="https://github.com/microsoft/P.808" style="color:#e97c36;">MOS</a><d-footnote>This metric will only be used for evaluation of the final blind test set.</d-footnote> ↑</td>
        <td class="tg-51oy">❌</td>
        <td class="tg-51oy">Any</td>
        <td class="tg-51oy">[1, 5]</td>
    </tr>
    </tbody>
    </table><br/>

    > **Note:** For real recorded test samples that do not have a strictly matched reference signal, part of the above metrics will be used.


6. The overall ranking will be determined via the following procedure:

    1. Calculate the average score of each metric for each submission.
    2. Calculate the per-metric ranking based on the average score.
       * We adopt the dense ranking ("1223" ranking)<d-footnote><a href="https://en.wikipedia.org/wiki/Ranking#Dense_ranking_(%221223%22_ranking)">https://en.wikipedia.org/wiki/Ranking#Dense_ranking_(&quot;1223&quot;_ranking)</a></d-footnote> strategy for handling ties.
    3. Calculate the `per-category ranking` by averaging the rankings within each category.
    4. Calculate the overall ranking by averaging the `per-category rankings`.<br/><br/>

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

    > Note: Only <u>the original test data</u>, <u>the best baseline system</u>, and <u>participant submissions</u> are taken into account in the ranking procedure.
