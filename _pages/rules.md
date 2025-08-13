---
layout: page
permalink: /rules/
title: Rules
description:  
nav: true
nav_order: 4

bibliography: rules.bib
---

> EMO2VEC
> LID for language
> https://huggingface.co/espnet/owsm_ctc_v4_1B
> SCOREQ

1. When generating the training and validation datasets, **ONLY the speech, nosie, and room impulse response (RIR) corpora listed in the [`Data`](/urgent2025/data) tab shall be used to ensure a fair comparison** and proper understanding of various SE approaches.
    
    > [update]Should We Keep This Below?

    * The first month of the challenge  will be a grace period when participants can propose additional public datasets to be included in the list. We (organizers) will reply to the requests and may update the list. Updates will be recorded in the [`Notice`](/urgent2025/notice) tab. 
    
    
    * **It is NOT allowed to use pre-trained speech enhancement models trained on other than official Challenge data**.
      * However, it IS allowed to use a pre-trained model trained on the official challenge data (e.g., [URGENT 2024](https://huggingface.co/wyz/tfgridnet_for_urgent24) / [URGENT 2025](https://huggingface.co/kohei0209/tfgridnet_urgent25) / [URGENT 2026](TODO link)  official baseline ) 
    

    > [update] Data cleaning model.


    * Although the speech enhancement model should only be trained on the listed data, we allow the use of pre-trained foundation models such as [HuBERT](https://github.com/facebookresearch/fairseq/blob/main/examples/hubert/README.md), [WavLM](https://github.com/microsoft/unilm/blob/master/wavlm/README.md), [EnCodec](https://github.com/facebookresearch/encodec), [Llama](https://llama.meta.com/llama-downloads/) and so on. **We also allow the use of pretrained speech enhancement/restoration model to improve the quality of clean speech for simulation.** The use of all pre-trained models must meet the following requirements:
        * they are publicly available before the challenge begins
        * they are explicitly mentioned in the submitted system description.
        * Note:
            * Their parameters can be fine-tuned on the listed data.
            * It is not allowed to fine-tune any model, be it pre-trained or not, on any extra data other than the listed data.<br/><br/>

    * **If you are unsure whether the pre-trained model you would like to use is allowed, please reach out to the organizers.**


2. The test data should only be used for evaluation purposes. **Techniques such as test-time adaptation, unsupervised domain adaptation, and self-training on the test data are NOT allowed**.


3. There is no constraint on the latency or causality of the developed system in this challenge. Any type of model can be used as long as they conform to the other rules as listed in this page.


4. Registration is required to submit results to the challenge (Check the [`Leaderboard`](/urgent2025/leaderboard) tab for more information). Note that the team information (including affiliation, team name, and team members) should be provided when submitting the results. For detailed submission requirements, please check the [`Submission`](/urgent2025/submission) tab.
    * Only the team name will be shown in the leaderboard, while the affiliation and team members will be kept confidential.<br/><br/>

    > [update] Add four Non-intrusive metrics.

5. The following evaluation metrics will be calculated for evaluation.
    
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
        <td class="tg-r6l2" rowspan="7">Non-intrusive SE metrics</td>
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
        <td class="tg-0a7q"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_nonintrusive_mos.py">DNSMOS Pro</a> ↑<d-cite key="cumlinDNSMOSProReducedSize2024"/></td>
        <td class="tg-xwyw"><span style="font-weight:400;font-style:normal;text-decoration:none">❌</span></td>
        <td class="tg-xwyw">16 kHz</td>
        <td class="tg-xwyw">[1, 5]</td>
    </tr>
    <tr>
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
    </tr>
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
        <td class="tg-ligs" rowspan="2">Downstream-task-dependent metrics</td>
        <td class="tg-r2ra"><a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/main/evaluation_metrics/calculate_speaker_similarity.py">SpkSim</a> ↑</td>
        <td class="tg-ligs">✔</td>
        <td class="tg-ligs">16 kHz</td>
        <td class="tg-ligs">[-1, 1]</td>
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


<details><summary>Below is an example of how we calculate the overall ranking.</summary><div>

<style type="text/css">
.unselectable {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* visibility: hidden; */
  /* display: block; */
 }
.tg2  {border:none;border-collapse:collapse;border-spacing:0;}
.tg2 td{border-style:solid;border-width:0px;font-family:Arial, sans-serif;font-size:14px;overflow:hidden;
  padding:10px 5px;word-break:normal;}
.tg2 th{border-style:solid;border-width:0px;font-family:Arial, sans-serif;font-size:14px;font-weight:normal;
  overflow:hidden;padding:10px 5px;word-break:normal;}
.tg2 .tg2-lboi{border-color:inherit;text-align:left;vertical-align:middle}
.tg2 .tg2-ia6h{background-color:#EFEFEF;border-color:inherit;font-weight:bold;text-align:center;vertical-align:middle}
.tg2 .tg2-gfnm{background-color:#efefef;border-color:#000000;text-align:center;vertical-align:middle}
.tg2 .tg2-18eh{border-color:#000000;font-weight:bold;text-align:center;vertical-align:middle}
.tg2 .tg2-9wq8{border-color:inherit;text-align:center;vertical-align:middle}
.tg2 .tg2-2bax{color:#fe0000;font-weight:bold;text-align:center;vertical-align:middle}
.tg2 .tg2-wa1i{font-weight:bold;text-align:center;vertical-align:middle}
.tg2 .tg2-qbk9{background-color:#efefef;border-color:inherit;font-weight:bold;text-align:center;vertical-align:middle}
.tg2 .tg2-g7yy{background-color:#EFEFEF;border-color:inherit;text-align:center;vertical-align:middle}
.tg2 .tg2-1tol{border-color:#000000;font-weight:bold;text-align:left;vertical-align:middle}
.tg2 .tg2-0a7q{border-color:#000000;text-align:left;vertical-align:middle}
.tg2 .tg2-fsme{background-color:#efefef;border-color:inherit;text-align:center;vertical-align:middle}
.tg2 .tg2-xwyw{border-color:#000000;text-align:center;vertical-align:middle}
.tg2 .tg2-y0n7{background-color:#efefef;text-align:center;vertical-align:middle}
.tg2 .tg2-nrix{text-align:center;vertical-align:middle}
.tg2 .tg2-dbp2{color:#fe0000;text-align:center;vertical-align:middle}
.tg2 .tg2-uzvj{border-color:inherit;font-weight:bold;text-align:center;vertical-align:middle}
</style>
<table class="tg2">
<thead>
  <tr>
    <th class="tg2-1tol" colspan="2" rowspan="3">System</th>
    <th class="tg2-18eh" colspan="11">Per-metric ranking</th>
  </tr>
  <tr>
    <th class="tg2-qbk9" colspan="6">Non-intrusive SE metrics</th>
    <th class="tg2-18eh" colspan="5">Intrusive SE metrics</th>
    <th class="tg2-qbk9" colspan="2">Downstream-task-independent metrics</th>
    <th class="tg2-18eh" colspan="2"><span style="font-style:normal;text-decoration:none">Downstream-task-dependent metrics</span></th>
  </tr>
  <tr>
    <th nowrap class="tg2-qbk9">DNSMOS ↑</th>
    <th nowrap class="tg2-qbk9">NISQA ↑</th>
    <th nowrap class="tg2-qbk9">DNSMOS PRO ↑</th>
    <th nowrap class="tg2-qbk9">Distill-MOS ↑</th>
    <th nowrap class="tg2-qbk9">SIGMOS ↑</th>
    <th nowrap class="tg2-qbk9">Torchaudio-Squim SDR ↑</th>
    <th nowrap class="tg2-18eh">PESQ ↑</th>
    <th nowrap class="tg2-18eh">ESTOI ↑</th>
    <th nowrap class="tg2-18eh">SDR ↑</th>
    <th nowrap class="tg2-18eh">MCD ↓</th>
    <th nowrap class="tg2-18eh">LSD ↓</th>
    <th nowrap class="tg2-qbk9">SpeechBERTScore ↑</th>
    <th nowrap class="tg2-qbk9">LPS ↑</th>
    <th nowrap class="tg2-18eh">SpkSim ↑</th>
    <th nowrap class="tg2-18eh">WAcc ↑</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg2-0a7q" colspan="2">Noisy input</td>
    <td class="tg2-fsme">6</td>
    <td class="tg2-fsme">6</td>    <td class="tg2-fsme">6</td>
    <td class="tg2-fsme">6</td>    <td class="tg2-fsme">6</td>
    <td class="tg2-fsme">6</td>
    <td class="tg2-xwyw">5</td>
    <td class="tg2-xwyw">4</td>
    <td class="tg2-xwyw">5</td>
    <td class="tg2-xwyw">5</td>
    <td class="tg2-xwyw">5</td>
    <td class="tg2-gfnm">1</td>
    <td class="tg2-gfnm">5</td>
    <td class="tg2-xwyw">3</td>
    <td class="tg2-xwyw">3</td>
  </tr>
  <tr>
    <td class="tg2-lboi" colspan="2">Baseline</td>
    <td class="tg2-fsme">5</td>
    <td class="tg2-fsme">5</td>    <td class="tg2-fsme">5</td>
    <td class="tg2-fsme">5</td>    <td class="tg2-fsme">5</td>
    <td class="tg2-fsme">5</td>
    <td class="tg2-9wq8">4</td>
    <td class="tg2-9wq8">5</td>
    <td class="tg2-9wq8">4</td>
    <td class="tg2-9wq8">4</td>
    <td class="tg2-9wq8">4</td>
    <td class="tg2-fsme">4</td>
    <td class="tg2-fsme">4</td>
    <td class="tg2-9wq8">5</td>
    <td class="tg2-9wq8">4</td>
  </tr>
  <tr>
    <td class="tg2-lboi" colspan="2">Submission 1</td>
    <td class="tg2-fsme">1</td>
    <td class="tg2-fsme">1</td>    <td class="tg2-fsme">1</td>
    <td class="tg2-fsme">1</td>    <td class="tg2-fsme">1</td>
    <td class="tg2-fsme">1</td>
    <td class="tg2-9wq8">6</td>
    <td class="tg2-9wq8">6</td>
    <td class="tg2-9wq8">6</td>
    <td class="tg2-9wq8">6</td>
    <td class="tg2-9wq8">6</td>
    <td class="tg2-fsme">6</td>
    <td class="tg2-fsme">6</td>
    <td class="tg2-9wq8">6</td>
    <td class="tg2-9wq8">6</td>
  </tr>
  <tr>
    <td class="tg2-lboi" colspan="2"><span style="font-weight:400;font-style:normal;text-decoration:none">Submission 2</span></td>
    <td class="tg2-fsme">4</td>
    <td class="tg2-fsme">4</td>    <td class="tg2-fsme">4</td>
    <td class="tg2-fsme">4</td>    <td class="tg2-fsme">4</td>
    <td class="tg2-fsme">4</td>
    <td class="tg2-9wq8">3</td>
    <td class="tg2-9wq8">3</td>
    <td class="tg2-9wq8">3</td>
    <td class="tg2-9wq8">3</td>
    <td class="tg2-9wq8">3</td>
    <td class="tg2-fsme">4</td>
    <td class="tg2-fsme">3</td>
    <td class="tg2-9wq8">4</td>
    <td class="tg2-9wq8">5</td>
  </tr>
  <tr>
    <td class="tg2-lboi" colspan="2"><span style="font-weight:400;font-style:normal;text-decoration:none">Submission 3</span></td>
    <td class="tg2-fsme">3</td>
    <td class="tg2-fsme">3</td>    <td class="tg2-fsme">3</td>
    <td class="tg2-fsme">3</td>    <td class="tg2-fsme">3</td>
    <td class="tg2-fsme">3</td>
    <td class="tg2-9wq8">2</td>
    <td class="tg2-9wq8">2</td>
    <td class="tg2-9wq8">2</td>
    <td class="tg2-9wq8">2</td>
    <td class="tg2-9wq8">2</td>
    <td class="tg2-fsme">1</td>
    <td class="tg2-fsme">2</td>
    <td class="tg2-9wq8">2</td>
    <td class="tg2-9wq8">2</td>
  </tr>
  <tr>
    <td class="tg2-lboi" colspan="2"><span style="font-weight:400;font-style:normal;text-decoration:none">Submission 4</span></td>
    <td class="tg2-fsme">2</td>
    <td class="tg2-fsme">2</td>    <td class="tg2-fsme">2</td>
    <td class="tg2-fsme">2</td>    <td class="tg2-fsme">2</td>
    <td class="tg2-fsme">2</td>
    <td class="tg2-9wq8">1</td>
    <td class="tg2-9wq8">1</td>
    <td class="tg2-9wq8">1</td>
    <td class="tg2-9wq8">1</td>
    <td class="tg2-9wq8">1</td>
    <td class="tg2-fsme">1</td>
    <td class="tg2-fsme">1</td>
    <td class="tg2-9wq8">1</td>
    <td class="tg2-9wq8">1</td>
  </tr>
  <tr>
    <td class="tg2-9wq8 unselectable" colspan="12">⬇ ⬇ ⬇ ⬇ ⬇</td>
    <td class="tg2-lboi"></td>
  </tr>
  <tr>
  <th class="tg2-18eh" colspan="2"></th>
    <th class="tg2-18eh" colspan="11">Per-category ranking</th>
  </tr>
  <tr>
    <td class="tg2-1tol">System</td>
    <td class="tg2-wa1i">Overall ranking</td>
    <td class="tg2-y0n7" colspan="2"><span style="font-weight:700;font-style:normal;text-decoration:none">Non-intrusive SE metrics</span></td>
    <td class="tg2-nrix" colspan="5"><span style="font-weight:700;font-style:normal;text-decoration:none">Intrusive SE metrics</span></td>
    <td class="tg2-y0n7" colspan="2"><span style="font-weight:700;font-style:normal;text-decoration:none">Downstream-task-independent metrics</span></td>
    <td class="tg2-nrix" colspan="2"><span style="font-weight:700;font-style:normal;text-decoration:none">Downstream-task-dependent metrics</span></td>
  </tr>
  <tr>
    <td class="tg2-lboi">Noisy input</td>
    <td class="tg2-dbp2">4.200</td>
    <td class="tg2-g7yy" colspan="2">6.0</td>
    <td class="tg2-9wq8" colspan="5">4.8</td>
    <td class="tg2-g7yy" colspan="2">3.0</td>
    <td class="tg2-9wq8" colspan="2">3.0</td>
  </tr>
  <tr>
    <td class="tg2-lboi">Baseline</td>
    <td class="tg2-dbp2">4.425</td>
    <td class="tg2-g7yy" colspan="2">5.0</td>
    <td class="tg2-9wq8" colspan="5">4.2</td>
    <td class="tg2-g7yy" colspan="2">4.0</td>
    <td class="tg2-9wq8" colspan="2">4.5</td>
  </tr>
  <tr>
    <td nowrap class="tg2-lboi">Submission 1</td>
    <td class="tg2-dbp2">4.750</td>
    <td class="tg2-ia6h" colspan="2">1.0</td>
    <td class="tg2-9wq8" colspan="5">6.0</td>
    <td class="tg2-g7yy" colspan="2">6.0</td>
    <td class="tg2-9wq8" colspan="2">6.0</td>
  </tr>
  <tr>
    <td nowrap class="tg2-lboi"><span style="font-weight:400;font-style:normal;text-decoration:none">Submission 2</span></td>
    <td class="tg2-dbp2">3.750</td>
    <td class="tg2-g7yy" colspan="2">4.0</td>
    <td class="tg2-9wq8" colspan="5">3.0</td>
    <td class="tg2-g7yy" colspan="2">3.5</td>
    <td class="tg2-9wq8" colspan="2">4.5</td>
  </tr>
  <tr>
    <td nowrap class="tg2-lboi"><span style="font-weight:400;font-style:normal;text-decoration:none">Submission 3</span></td>
    <td class="tg2-dbp2">2.125</td>
    <td class="tg2-g7yy" colspan="2">3.0</td>
    <td class="tg2-9wq8" colspan="5">2.0</td>
    <td class="tg2-g7yy" colspan="2">1.5</td>
    <td class="tg2-9wq8" colspan="2">2.0</td>
  </tr>
  <tr>
    <td nowrap class="tg2-lboi"><span style="font-weight:400;font-style:normal;text-decoration:none">Submission 4</span></td>
    <td class="tg2-2bax">1.250</td>
    <td class="tg2-g7yy" colspan="2">2.0</td>
    <td class="tg2-uzvj" colspan="5">1.0</td>
    <td class="tg2-ia6h" colspan="2">1.0</td>
    <td class="tg2-uzvj" colspan="2">1.0</td>
  </tr>
</tbody>
</table>

</div></details>