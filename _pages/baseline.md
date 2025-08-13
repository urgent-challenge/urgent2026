---
layout: page
permalink: /baseline/
title: Baseline
description:  
nav: true
nav_order: 5

bibliography: baseline.bib
---

<br>

## Baseline code and checkpoint

Please refer to `Baselines in ESPnet` below for more details.
- Baseline script: [https://github.com/kohei0209/espnet/tree/urgent2025/egs2/urgent25/enh1](https://github.com/kohei0209/espnet/tree/urgent2025/egs2/urgent25/enh1)
- Baseline TF-GridNet pre-trained model [https://huggingface.co/kohei0209/tfgridnet_urgent25/tree/main](https://huggingface.co/kohei0209/tfgridnet_urgent25/tree/main)

<br>

## Basic Framework

<img alt="framework" src="/urgent2025/assets/img/framework.png" style="max-width: 100%;"/>

The basic framework is detailed in the URGENT challenge 2024 description paper<d-cite key="URGENT-Zhang2024"/>.

As depicted in the figure above, we design a distortion model (simulation stage) <d-math>\mathcal{F}(\cdot)</d-math> to unify the data format for different distortion types, such that different speech enhancement (SE) sub-tasks can share a consistent input/output processing. In particular, we ensure that the sampling frequency (SF) at the output of the distortion model (degraded speech) is always equal to that of its input.

During training and inference, the processing of different SFs is supported for both <u>conventional SE models</u> (lower-right) that usually only operate at one SF and <u>adaptive STFT-based sampling-frequency-independent (SFI) SE models</u> (upper-right) that can directly handle different SFs.

* For conventional SE models (e.g., Conv-TasNet<d-cite key="Conv_TasNet-Luo2019"/>), we always **upsample** its input (degraded speech) to the highest SF (48 kHz) so that the model only need to operate at 48 kHz. The model output (48 kHz) is then **downsampled** to the same SF as the degraded speech.
* For adaptive STFT-based SFI<d-cite key="Sampling-Paulus2022,Toward-Zhang2023,Improving-Zhang2024"/> SE models (e.g., BSRNN<d-cite key="Music-Luo2023,Efficient-Yu2023,High-Yu2023"/>, TF-GridNet<d-cite key="TF_GridNet-Wang2023,TF_GridNet2-Wang2023"/>), we directly feed the degraded speech of different SFs into the model, which can adaptively adjust their STFT/iSTFT configuration according to the SF and generate the enhanced signal with the same SF.

<br>

## Baselines in ESPnet

We provide offical baselines and the corresponding recipe ([`egs2/urgent25/enh1`](https://github.com/kohei0209/espnet/tree/urgent2025/egs2/urgent25/enh1)) based on the ESPnet toolkit.

How to run training/inference is desribed in [egs2/urgent25/enh1/README.md](https://github.com/kohei0209/espnet/blob/urgent2025/egs2/urgent25/enh1/README.md).

> To install the ESPnet toolkit for model training, please follow the instructions at https://espnet.github.io/espnet/installation.html.
>
> You can check [“A quick tutorial on how to use ESPnet”](/urgent2025/espnet_tutorial) to have a quick overview on how to use ESPnet for speech enhancement.

  * For the basic usage of this toolkit, please refer to [egs2/TEMPLATE/enh1/README.md](https://github.com/espnet/espnet/blob/master/egs2/TEMPLATE/enh1/README.md).
  * Several baseline models are provided in the format of a `YAML` configuration file in [`egs2/urgent25/enh1/conf/tuning/`](https://github.com/kohei0209/espnet/tree/urgent2025/egs2/urgent25/enh1/conf/tuning/).
      * We will provide the pretrained TF-GridNet model using the [provided config](https://github.com/kohei0209/espnet/blob/urgent2025/egs2/urgent25/enh1/conf/tuning/train_enh_tfgridnet_dm.yaml) soon.
  * To run a recipe, you basically only need to execute the following command after [installing ESPnet from source](https://espnet.github.io/espnet/installation.html):
    <br/><span>For explanation of the arugments in `./run.sh`, please refer to [`egs2/TEMPLATE/enh1/enh.sh`](https://github.com/espnet/espnet/blob/master/egs2/TEMPLATE/enh1/enh.sh).</span>

<!--
# data preparation (this will clone the challenge repository)
./run.sh --stage 1 --stop-stage 1
mkdir -p dump
cp -r data dump/raw
./run.sh --stage 5 --stop-stage 5 --nj 8
<br/>
# training
./run.sh --stage 6 --stop-stage 6 --ngpu 4 --enh_config conf/tuning/&lt;your-favorite-config.yaml&gt;
<br/>
# inference (for both validation and test sets)
./run.sh --stage 7 --stop-stage 7 --enh_config conf/tuning/&lt;your-favorite-config.yaml&gt; \
<span>    </span>--inference_nj 8 --gpu_inference true
<br/>
# scoring (only for the validation set)
. ./path.sh
exp="exp/enh_train_enh_bsrnn_medium_noncausal_raw" # replace this with your exp directory
for x in "validation"; do
<span>    </span># non-intrusive metric (DNSMOS)
<span>    </span>python urgent2024_challenge/evaluation_metrics/calculate_nonintrusive_dnsmos.py \
<span>        </span>--inf_scp ${exp}/enhanced_${x}/spk1.scp \
<span>        </span>--output_dir ${exp}/enhanced_${x}/scoring_dnsmos \
<span>        </span>--device cuda \
<span>        </span>--convert_to_torch True \
<span>        </span>--primary_model urgent2024_challenge/DNSMOS/DNSMOS/sig_bak_ovr.onnx \
<span>        </span>--p808_model urgent2024_challenge/DNSMOS/DNSMOS/model_v8.onnx
<span>    </span># non-intrusive metric (NISQA)
<span>    </span>python urgent2024_challenge/evaluation_metrics/calculate_nonintrusive_nisqa.py \
<span>        </span>--inf_scp ${exp}/enhanced_${x}/spk1.scp \
<span>        </span>--output_dir ${exp}/enhanced_${x}/scoring_dnsmos \
<span>        </span>--device cuda \
<span>        </span>--nisqa_model urgent2024_challenge/lib/NISQA/weights/nisqa.tar
<br/>
<span>    </span># intrusive SE metrics (calculated on CPU)
<span>    </span>python urgent2024_challenge/evaluation_metrics/calculate_intrusive_se_metrics.py \
<span>        </span>--ref_scp dump/raw/${x}/spk1.scp \
<span>        </span>--inf_scp ${exp}/enhanced_${x}/spk1.scp \
<span>        </span>--output_dir ${exp}/enhanced_${x}/scoring \
<span>        </span>--nj 8 \
<span>        </span>--chunksize 500
<br/>
<span>    </span># downstream-task-independent metric (SpeechBERTScore)
<span>    </span>python urgent2024_challenge/evaluation_metrics/calculate_speechbert_score.py \
<span>        </span>--ref_scp dump/raw/${x}/spk1.scp \
<span>        </span>--inf_scp ${exp}/enhanced_${x}/spk1.scp \
<span>        </span>--output_dir ${exp}/enhanced_${x}/scoring_speech_bert_score \
<span>        </span>--device cuda
<span>    </span># downstream-task-independent metric (LPS)
<span>    </span>python urgent2024_challenge/evaluation_metrics/calculate_phoneme_similarity.py \
<span>        </span>--ref_scp dump/raw/${x}/spk1.scp \
<span>        </span>--inf_scp ${exp}/enhanced_${x}/spk1.scp \
<span>        </span>--output_dir ${exp}/enhanced_${x}/scoring_phoneme_similarity \
<span>        </span>--device cuda
<br/>
<span>    </span># downstream-task-dependent metric (SpkSim)
<span>    </span>python urgent2024_challenge/evaluation_metrics/calculate_speaker_similarity.py \
<span>        </span>--ref_scp dump/raw/${x}/spk1.scp \
<span>        </span>--inf_scp ${exp}/enhanced_${x}/spk1.scp \
<span>        </span>--output_dir ${exp}/enhanced_${x}/scoring_speaker_similarity \
<span>        </span>--device cuda
<span>    </span># downstream-task-dependent metric (WER or 1-WAcc)
<span>    </span>python urgent2024_challenge/evaluation_metrics/calculate_wer.py \
<span>        </span>--meta_tsv dump/raw/${x}/text \
<span>        </span>--inf_scp ${exp}/enhanced_${x}/spk1.scp \
<span>        </span>--output_dir ${exp}/enhanced_${x}/scoring_wer \
<span>        </span>--device cuda
done
    </d-code>

The average scores will be written respectively in `${exp}/enhanced_${x}/scoring*/RESULTS.txt`.
-->