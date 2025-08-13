---
layout: page
permalink: /data/
title: Data
description:  
nav: true
nav_order: 3
# toc: true
bibliography: data.bib
---

## Contents:

- [Contents:](#contents)
- [Brief data description: Track 1](#brief-data-description-track-1)
    - [Training/validation data](#trainingvalidation-data)
    - [Non-blind test set](#non-blind-test-set)
    - [Blind test set](#blind-test-set)
  - [Detailed data description](#detailed-data-description)
  - [Data selection and Simulation](#data-selection-and-simulation)
    - [Distortions](#distortions)
    - [Simulation metadata](#simulation-metadata)
- [Track 2](#data-description-track-2)


## Brief data description: Track 1

#### Training/validation data
The training and validation data are both simulated by using several public speech/noise/rir corpora (see the table below for more details).
We provide the data preparation pipeline with the [official baseline](https://github.com/urgent-challenge/urgent2026_challenge_track1), which automatically downloads and pre-processes the data.

The [data preparetion script](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/utils/prepare_train_data.sh) will generate two types of training data:

The first is the pre-simulated data, which has the following form of directory structure:
```bash
data/train_simulation/
├── speech_length.scp # Speech duration in number of sample points.
├── spk1.scp # Clean speech file list of id and audio path.
├── utt2fs  # id to sampling rate mapping
├── utt2spk # utterance to speaker mapping 
└── wav.scp # Noisy speech file list of id and audio path.
```
The pre-simulated dataset can be loaded by the `PreSimulatedDataset` in the [baseline code](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/baseline_code/dataset.py) .


The other is the dynamic mixing dataset; we also provided a `DynamicMixingDataset` class in the [baseline code](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/baseline_code/dataset.py) for loading data in a dynamic mixing manner.
The dataset has the following form of directory structure:

```bash
data/train_sources
├── noise_scoures.scp # Noise audio id and audio path.
├── rirs.scp # Room impulse response id and audio path.
├── source_length.scp # Speech duration in number of sample points.
├── speech_sources.scp # Clean speech id and audio path.
└── wind_noise_scoures.scp # # Wind noise audio id and audio path.
```

By default, we only generate the pre-simulated data for validation.

<!-- There are two types of validation data. One is automatically generated during data preparation, and the other is provided by the organizers 
- Unofficial validation set: participants can generate their own validation set using the validation subset of the official challenge datasets to choose the best model.
- Official validation set: We organizers provide the validation set for the leaderboard submission. It contains 1000 samples and all of them are synthetic data. The maximum duration per utterance is 15 seconds. Unlike the unofficial one, **we manually picked up clean speeches for the noisy corpora (i.e., CommonVoice)** so it better reflects the enhancement quality. [Noisy speech](https://drive.google.com/file/d/1Ip-C5tUNGCssT8KAjHUUoh99jkzRH6nm/view), [Clean speech](https://drive.google.com/file/d/11geBBf24WKN1xT_NasnI4JrmKpqNo8h9/view), and [metadata](https://drive.google.com/file/d/1CU5QKYOgG4fUuJ8oAC6BEhI9ZDhQYZpF/view) are available. -->

#### Non-blind test set
<!-- The non-blind test set are prepared in a similar way as the validation set but there are several differences:
- The test split of the official challenge datasets were used.
- Several unseen noise and rir were also used when simulating the non-blind test set.
- Sampling rates are almost equally distributed (there are ~1000/7 data for each of 8k, 16k, 22.05k, 24k, 32k, 44.1k, and 48kHz). We downsampled some data to achieve this. -->
- Available online after November 3rd, 2025.

<!-- The [noisy](https://drive.google.com/file/d/1rxV6RgA4LAp2I1EnHsln7wI7-UCP6Qer/view) and [clean](https://drive.google.com/file/d/1RarjxOgWkaDV8EjH_eLX169y89PVa3sg/view?usp=sharing) speeches as well as the [metadata](https://drive.google.com/file/d/1CfhKjfkkUZ60UEOHnlntcQY2m_9pn1uA/view?usp=sharing) are available. 
After the non-blind test phase ends, clean speech and metadata will be available. -->

#### Blind test set

- Available online after November 18th, 2025.

<!-- The blind test set, which will **be used for the final ranking**, is available [here](https://drive.google.com/file/d/1dHvYEGHCf9rsB1q-Cd9rXOeQaa_vjG2u/view?usp=sharing).

To evaluate the universality, robustness, and generalizability of the submitted systems as outlined in the theme of this challenge, the blind test set is primarily from domains other than the training set:
- consist of **50% real-recorded data** (without audio ground truth) and 50% synthetic data,
- primarily be derived from **from unseen corpora/datasets**,
- include **one unseen language** in addition to the five languages present in the training data,
- be distorted by **some unseen distortions**  in addition to those used in training, and
- contain 150 samples for each language, amounting to 900 samples in total.

Note that the evaluation procedure during the blind testing phase differs from that in the validation/non-blind test phase in the following ways:
- Two additional metrics (POLQA and MOS) will be included. (As previously announced, only the English subset will be used for the MOS evaluation due to the short evaluation period.)
- Only a subset of metrics (DNSMOS, NISQA, UTMOS, MOS, and CER if transcription is available) will be considered for the real-recorded data. -->

<br>

### Detailed data description

The training and validation data are both simulated based on the following source data.
Based on the [dataset of the 2nd URGENT challenge](https://urgent-challenge.github.io/urgent2025/data/), we conducted a data selection using the data filtering method proposed in a recent paper <d-cite key="liLessMoreData2025"/>.

**It is noted that we encourage you to explore better ways of data selection and utilization in this challenge.** In addition to the data and filtering methods provided by our baseline, you can make use of larger-scale datasets, such as the [track2 data](https://urgent-challenge.github.io/urgent2025/data/) from the 2nd URGENT challenge, or other allowed data (please check it in the [rules pages](/urgent2026/rules/)).

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
    <td>-</td>
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
    <td>any</a></td>
    <td>-</td>
    <td>-</td>
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


> We allow participants to simulate their own RIRs using existing tools<d-footnote>For example, <a href="https://github.com/ehabets/RIR-Generator">RIR-Generator</a>, <a href="https://github.com/LCAV/pyroomacoustics">pyroomacoustics</a>, <a href="https://github.com/DavidDiazGuerra/gpuRIR">gpuRIR</a>,  and so on.</d-footnote> for generating the training data.
> The participants can also propose publicly available real recorded RIRs to be included in the above data list during the grace period (See [`Timeline`](/urgent2026/timeline)).
> Note: If participants used additional RIRs to train their model, the related information should be provided in the README.yaml file in the submission. Check the [template](/urgent2026/template) for more information.
>
> We allow participants to simulate wind noise using some tools such as <a href="https://github.com/audiolabs/SC-Wind-Noise-Generator/tree/main">SC-Wind-Noise-Generator</a>. In default, the simulation script in our repository simulates 200 and 100 wind noises for training and validation for each sampling frequency. The configuration can be easily changed in <a href="https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/conf/wind_noise_simulation_train.yaml">wind_noise_simulation_train.yaml</a> and <a href="https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/conf/wind_noise_simulation_validation.yaml">wind_noise_simulation_validation.yaml</a>


<br>

### Data selection and Simulation

<!-- <img alt="pre-processing" src="/urgent2026/assets/img/preprocessing.png" style="max-width: 100%;"/> -->

We apply the data selection to the Track 1 data of the 2nd URGENT using the data filtering method proposed in the recent paper <d-cite key="liLessMoreData2025"/>. The selected data list is available at [here](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/meta/train_selected_700h). The speech source from NNCES, SeniorTalk, VocalSet, and ESD is not filtered.

Note that the data filtering of paper <d-cite key="liLessMoreData2025"/> is not the best method to utilize the large-scale dataset for SE.
**The goal of this challenge is to encourage participants to develop how to better leverage large-scale data** to improve the final SE performance.

The simulation data can be generated as follows:

1. In the first step, a manifest `meta.tsv` is first generated by [`simulation/generate_data_param.py`](https://github.com/urgent-challenge/urgent2025_challenge/blob/main/simulation/generate_data_param.py) from the given list of speech, noise, and room impulse response (RIR) samples. It specifies how each sample will be simulated, including the type of distortion to be applied, the speech/noise/RIR sample to be used, the signal-to-noise ratio (SNR), the random seed, and so on.

2. In the second step, the simulation can be done in parallel via [`simulation/simulate_data_from_param.py`](https://github.com/urgent-challenge/urgent2025_challenge/blob/main/simulation/simulate_data_from_param.py) for different samples according to the manifest while ensuring reproducibility. This procedure can be used to generate training and validation datasets.

3. By default, we applied a [high-pass filter](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/simulation/simulate_data_from_param.py) to the speech signals since we have noticed that there is high-energy noise in the infrasound frequency band in some speech sources. You can turn it off by setting `highpass=False` in your simulation.

For the training set, **we recommend dynamically generating degraded speech samples during training** to increase the data diversity.



#### Distortions
In this challenge, the SE system has to address the following seven distortions.
In addition to the first four distortions considered in our first challenge, **we added three more distortions (bold ones) often observed in real recordings**.
Furthermore, in this challenge, **inputs may have multiple distortions**.

We provide an example simulation script as [`simulation/simulate_data_from_param.py`](https://github.com/urgent-challenge/urgent2026_challenge_track1/blob/main/simulation/simulate_data_from_param.py).

1. Additive noise
2. Reverberation
3. Clipping
4. Bandwidth limitation
5. **Codec distortion**
6. **Packet loss**
7. **Wind noise**



#### Simulation metadata

The manifest mentioned above is a `tsv` file containing several columns (separated by `\t`). For example:

| id | noisy_path | speech_uid | speech_sid | clean_path | noise_uid | snr_dB | rir_uid | augmentation | fs | length | text |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|unique ID|path to the generated degraded speech|utterance ID of clean speech|speaker ID of clean speech|path to the paired clean speech|utterance ID of noise|SNR in decibel|utterance ID of the RIR|augmentation type|sampling frequency|sample length|raw transcript|
|fileid_1|simulation_validation/noisy/fileid_1.flac|p226_001_mic1|vctk_p226|simulation_validation/clean/fileid_1.flac|JC1gBY5vXHI|16.106643714525433|mediumroom-Room119-00056|bandwidth_limitation-kaiser_fast->24000|48000|134338|Please call Stella.|
|fileid_2|simulation_validation/noisy/fileid_2.flac|p226_001_mic2|vctk_p226|simulation_validation/clean/fileid_2.flac|file205_039840000_loc32_day1|2.438365163611807|none|bandwidth_limitation-kaiser_best->22050|48000|134338|Please call Stella.|
|fileid_1561|simulation_validation/noisy/fileid_1561.flac|p315_001_mic1|vctk_p315|simulation_validation/clean/fileid_1561.flac|AvbnjyrHq8M|1.3502745341597029|mediumroom-Room076-00093|clipping(min=0.016037324066971528,<wbr>max=0.9890219800761639)|48000|114829|&lt;not-available&gt;|


**Note**

* If the `rir_uid` value is not `none`, the specified RIR is applied to the clean speech sample.

* If the `augmentation` value is not `none`, the specified augmentation is applied to the degraded speech sample.

* `<not-available>` in the `text` column is a placeholder for transcripts that are not available.

* The audios in `noisy_path`, `clean_path`, and (optional) `noise_path` are consistently scaled such that `noisy_path = clean_path + noise_path`.

* However, the scale of the enhanced audio is not critical for objective evaluation the challenge, as the evaluation metrics are made largely insensitive to the scale. For subjective listening in the final phase, however, it is recommended that the participants properly scale the enhanced audios to facilitate a consistent evaluation.

* For all different distortion types, the original sampling frequency of each clean speech sample is always preserved, i.e., the degraded speech sample also shares the same sampling frequency. For `bandwidth_limitation` augmentation, this means that the generated speech sample is resampled to the original sampling frequency `fs`.



# Data description: Track 2

## Training/Validation Data

We allow the use of any public datasets for training. Please include the data usage in technical report. See https://github.com/urgent-challenge/urgent2026_challenge_track2 for training and validation data usage in official baseline.

## Non-blind test set

- The urgent 2024 MOS dataset will be used for non-blind test sets. Available online after November 3rd, 2025

## Blind test set

- Available online after November 18th, 2025