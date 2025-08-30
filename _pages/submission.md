---
layout: page
permalink: /submission/
title: Submission
description:  
nav: true
nav_order: 6
---

<br>


<br>

### Submission format and requirements (Track1)

* Each submission should be **a zip file** containing two parts:
    1. enhanced audios corresponding to the subset to be tested;
    2. a YAML (README.yaml) file containing the basic information about the submission (as listed below). The template can be found [here](/urgent2025/template).
        * team information (team name, affiliation, team mambers)
        * description of the training & validation data used for the submission
        * description of pre-trained models used for the submission (if applicable)

<!-- * The zip file should be named as `{your_teamname}.zip`. Here, `{your_teamname}` should be replaced with your team name. -->
* The zip file should only contain a single YAML (README.yaml) file and a folder named `enhanced` that contains all the enhanced audio files. That is, the directory structure after executing `unzip {your_teamname}.zip` should be as follows:

```bash
./
├── README.yaml
└── enhanced/
    ├── fileid_1.flac
    ├── fileid_2.flac
    ├── ...
    └── fileid_N.flac
```
* **Note that the submission without README.yaml is rejected by the leaderboard system.**
* Please encode all audio files in the 16-bit [**FLAC**](https://xiph.org/flac/) format to reduce the file size (< 300 MB).
    * The audio files should be encoded in mono-channel with its original sampling frequency.
    * All audio files should have the same **name** and **length** as the original audio files in the provided subset to be tested.
* Be careful not to include hidden directories in the zip file such as `__MACOSX/` which may cause evaluation failure.
* The submission should be done via our [official leaderboard website](https://urgent-challenge.com/):
  * A registration (please sign up at [https://urgent-challenge.com](https://urgent-challenge.com/)) is required to participate in our challenge.
  * Each team shall only register **once**. Multiple registrations from different members in one team are not allowed.
* Each team can submit up to **2 submissions per day** during the challenge.
  * The third and later submissions will be ignored. The quota will be reset at 00:00 (UTC timezone) every day.
  * Failed submissions are not taken into account when counting the submissions per day.
  * No submission will be accepted after the deadline (January 15th, 2025).
* For each team, only the submission with the best leaderboard performance will be used for the final evaluation.


> Submissions that fail to conform to the above requirements may be rejected.
>
> Should you encounter any problem during the submission, please feel free to [contact the organizers](mailto:urgent.challenge@gmail.com).

<br>


### Submission format and requirements (Track2)

TODO



### Paper submission (By invitation only)

Upto five top-ranked teams can submit a paper describing the submitted SE system to the [ICASSP 2026](https://2026.ieeeicassp.org/). Accepted papers will be published in the ICASSP proceedings. The review process is coordinated by the challenge organizers and the SPGC chairs.
Paper submission link: [https://cmsworkshops.com/ICASSP2026/Papers/Submission.asp?Type=Challenge&ID=13](https://cmsworkshops.com/ICASSP2026/Papers/Submission.asp?Type=Challenge&ID=13)


### Agreement

By submitting the results, the participants agree to the following conditions:

<d-code block language="markdown">
As a condition of submission, entrants grant the organizers, a perpetual,
irrevocable, worldwide, royalty-free, and non-exclusive license to use,
reproduce, adapt, modify, publish, distribute, publicly perform, create a
derivative work from, and publicly display the submitted audio signals and
CSV files (containing the performance scores).

The main motivation for this condition is to donate the submitted audio
signals and corresponding performance scores to the community as a
voice quality dataset.
</d-code>
