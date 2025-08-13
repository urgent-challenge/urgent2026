---
layout: page
permalink: /leaderboard/
title: Leaderboard
description:  
nav: true
nav_order: 7
---

<!--
The blind test leaderboard has been closed since the challenge has completed. The final results can be found at https://urgent-challenge.com/competitions/5#final_results.

<del>The blind test leaderboard is now live at [https://urgent-challenge.com](https://urgent-challenge.com/).</del>

-->

<br>

### Leaderboard registration

1. Sign up the [competition page](https://urgent-challenge.com). Please click the link in the verification email to activate your account.

2. Register the leaderboard from the `Participate` tab at the [competition page](https://urgent-challenge.com/competitions/13).

3. <u><b>Submit the Google Form</b></u> (in the email you receieve after step 2). 

4. Your application wii be approved AFTER we organizers receive the Google Form.

<!-- 5. Then you can download the test set from the `Participate → Get Data` tab and start to make submissions in the `Participate → Submit / View Results` tab.
> It usually takes ~1 hour to finish the evaluation for each submission. You can click the `Refresh status` to check the evaluation status in the `Participate → Submit / View Results` tab.-->

<br>

### How to read the leaderboard?

  * Each row represents the best submission from one user (team).
  * For all evaluation phases, there are four categories of metrics for each submission: non-intrusive SE metrics, intrusive SE metrics, downstream-task-independent metrics, and downstream-task-dependent metrics. Each category includes several metrics.
      * For each metric cell, the first number represents the metric value, and the second number in parentheses represents the rank of this metric among all submissions.
      * For the final blind test phase, an additional category (`Subjective SE metrics`) will be added to evaluate the MOS score. See [`Data`](/urgent2025/data) for more information.
  * The last column (overall ranking score) represents the final score used for ranking all submissions. It is calculated following the rules defined in the [`Rules`](/urgent2025/rules) tab.

<br>

### Note

There are two official entries in the leaderboard:
  * The entry submitted by the user `urgent` represents the official baseline.
  * The entry submitted by the user `noisy` represents the result of the original noisy input speech (without enhancement).