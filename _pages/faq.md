---
layout: page
permalink: /faq/
title: FAQ
description:
nav: true
nav_order: 8
---

Below we summarize some frequently asked questions (FAQ) about the URGENT Challenge. If you have any other questions, please feel free to [contact us](/urgent2025/contact).

<details>

  <summary><strong> 1. How can I check why my submission failed in the leaderboard?  </strong></summary>

  <br>

  You could go to <code>Participate</code> → <code>Submit / View Results</code> and unfold the corresponding failed submission. Then click the text <code>View scoring error log</code> to download the error message file. It should display the detailed information about the failure.

  <div><img alt="error_message" src="/urgent2025/assets/img/error_log.png" style="max-width: 100%;"/></div>

</details>

<br>

<details><summary><strong>  2. What does the error message from the leaderboard mean? </strong></summary>

<br>

Message 1:
<pre><code class="language-bash">data_pairs.append((uid, refs[uid], audio_path))
KeyError: 'fileid_10009'
</code></pre>

<strong>Answer</strong>: Your submission contains an invalid file name that is not included in the provided test dataset. Please carefully check whether you are using the correct dataset corresponding to the current evaluation phase.

<br>
<br>

Message 2:
<pre><code class="language-bash">assert ref.shape == inf.shape, (ref.shape, inf.shape)
AssertionError: ((315934,), (315936,))
</code></pre>

<strong>Answer</strong>: You submission contains an audio sample that has a different length from the corresponding test sample provided in the official test dataset. Please carefully check your enhanced audios to make sure all sample lengths are consistent with the original audio length. Please also check whether you are using the correct test dataset corresponding to the current evaluation phase.

<br>
<br>

Message 3:
<pre><code class="language-bash">RuntimeError: Error : flac decoder lost sync.
</code></pre>

<strong>Answer</strong>: You submission contains an invalid audio sample that cannot be properly decoded by the FLAC decoder on the server. Please validate the enhanced audios on your side. FLAC v1.4.3 is recommended.

<br>
<br>

Message 4:
<pre><code class="language-bash">RuntimeError: Error : unknown error in flac decoder.
</code></pre>

<strong>Answer</strong>: You submission contains an invalid audio sample that cannot be properly decoded by the FLAC decoder on the server. Please validate the enhanced audios on your side. FLAC v1.4.3 is recommended.

<br>
<br>

Message 5:
<pre><code class="language-bash">slurmstepd: error: *** JOB 24880048 ON r288 CANCELLED AT 2024-08-02T04:17:40 DUE TO TIME LIMIT ***
</code></pre>

or 

<pre><code class="language-bash">Timeout: The evaluation server is busy. Please try to resubmit later.
</code></pre>

<strong>Answer</strong>: Evaluation jobs for your submission were killed due to a timeout. This may be caused by unexpected long queuing in our SLURM system on the server. Please contact us and we will rerun the evaluation for you.

<br>
<br>

Message 6:
<pre><code class="language-bash">
RuntimeError: CUDA error: uncorrectable ECC error encountered
CUDA kernel errors might be asynchronously reported at some other API call, so the stacktrace below might be incorrect.
For debugging consider passing CUDA_LAUNCH_BLOCKING=1.
Compile with `TORCH_USE_CUDA_DSA` to enable device-side assertions.
</code></pre>

<strong>Answer</strong>: Evaluation jobs for your submission were terminated likely due to a hardware issue of the specific node assigned to evaluate your submission. Please contact us and we will rerun the evaluation using another node for you.

</details>

<br>


<details><summary><strong>  3. I would like to speecd up calculate_wer.py </strong></summary>

<br>

<code>calculate_wer.py</code> takes around 30~40 minutes (depending on the environment) to evaluate 1000 samples using a single GPU.
It takes some time since it does beam search in decoding.

To make it faster, you can skip the beam search by setting <code>BEAMSIZE</code> to 1 <a href="https://github.com/urgent-challenge/urgent2025_challenge/blob/2de19bab56c7d7fa5f61f5fdda193a7710c62475/evaluation_metrics/calculate_wer.py#L16">here</a>.

Note that <code>BEAMSIZE</code> is set to 5 in the leaderboard evaluation.
If you would like to check the consistency of the scores between your local and the leaderbord, <code>BEAMSIZE</code> should be set to 5.

</details>

<br>


<details><summary><strong>  4. How long is the maximum duration of the speech in the test set? </strong></summary>

<br>

The maximum duration will be around <strong>15 seconds</strong>.
Please note that this number may change.

</details>

<br>


<details><summary><strong> 5. Why is not my leaderboard registration approved? </strong></summary>

<br>

The leaderboard registration is usually approved at least within a day.

If your application is not approved for more than a day, <strong>please check if you have submitted the Google Form</strong>.
We do not approve the registration until we receive it.

If you have done it but have not gotten the approval yet, please reach out to the organizers.

</details>
