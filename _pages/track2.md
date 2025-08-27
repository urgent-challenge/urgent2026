---
layout: page
permalink: /track2/
title: Track2
description:  
nav: true
nav_order: 4
# toc: true
bibliography: track2.bib
---

## Contents:

- [Rules](#rules)
- [Data](#data)
- [Evaluation](#evaluation)

## Rules

Participants are allowed to use any publicly available datasets for the development of their prediction systems. All datasets used must be explicitly listed in the system description.

The use of proprietary datasets, including collecting your own subjective ratings such as MOS scores, is not allowed, unless such resources have been publicly released and are freely accessible to the broader community.

Additionally, participants may leverage publicly available pretrained models for initialization or as components within their systems. All such pretrained resources must also be clearly cited and described in the system description.

## Data

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
    <th></th>
    <th>Corpus</th>
    <th>Standard</th>
    <th>#Samples</th>
    <th>#Systems</th>
    <th>Duration (hours)</th>
    <th>Links</th>
    <th>License</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="9">Train</td>
    <td>BC19</td>
    <td>ITU-T P.808</td>
    <td>136</td>
    <td>21</td>
    <td>0.32</td>
    <td></td>
    <td><a href="https://www.cstr.ed.ac.uk/projects/blizzard/data.html">Custom</a></td>
  </tr>
  <tr>
    <td>BVCC</td>
    <td>ITU-T P.808</td>
    <td>4973</td>
    <td>175</td>
    <td>5.56</td>
    <td></td>
    <td><a href="https://www.cstr.ed.ac.uk/projects/blizzard/data.html">Custom</a></td>
  </tr>
  <tr>
    <td>NISQA</td>
    <td>ITU-T P.808</td>
    <td>11020</td>
    <td>N/A</td>
    <td>27.21</td>
    <td></td>
    <td><a href="https://github.com/gabrielmittag/NISQA/wiki/NISQA-Corpus">Mixed</a></td>
  </tr>
  <tr>
    <td>PSTN</td>
    <td>ITU-T P.808</td>
    <td>52839</td>
    <td>N/A</td>
    <td>163.08</td>
    <td></td>
    <td>Unknown</td>
  </tr>
  <tr>
    <td>SOMOS</td>
    <td>ITU-T P.808</td>
    <td>14100</td>
    <td>181</td>
    <td>18.32</td>
    <td></td>
    <td>CC BY-NC-SA 4.0</td>
  </tr>
  <tr>
    <td>TCD-VoIP</td>
    <td>ITU-T P.800</td>
    <td>384</td>
    <td>24</td>
    <td>0.87</td>
    <td></td>
    <td>CC BY-NC-SA 4.0</td>
  </tr>
  <tr>
    <td>Tencent</td>
    <td>ITU-T P.808</td>
    <td>10408</td>
    <td>N/A</td>
    <td>21.15</td>
    <td></td>
    <td>Apache</td>
  </tr>
  <tr>
    <td>TMHINT-QI</td>
    <td>Custom</td>
    <td>11644</td>
    <td>98</td>
    <td>10.22</td>
    <td></td>
    <td>MIT</td>
  </tr>
  <tr>
    <td>TTSDS2</td>
    <td>Custom</td>
    <td>460</td>
    <td>80</td>
    <td>0.96</td>
    <td></td>
    <td>MIT</td>
  </tr>
  <tr>
    <td>Development</td>
    <td>ITU-T P.835</td>
    <td>CHiME-7 UDASE Eval</td>
    <td>640</td>
    <td>5</td>
    <td>0.84</td>
    <td></td>
    <td>CC BY-SA 4.0</td>
  </tr>
</tbody>
</table>


### Training / Development Data

For training data, we combine the datasets in the following tables, note that most of these datasets contain synthesized speech by TTS / VC models and simulated corrupted speech, which may hurt the performance if used for training. For development data, we use the CHiME-4-UDASE-Evaluation dataset.



### Validation Data

The validation data will be available after the validation phase opens.

### Non-Blind Test Data

The non-blind test data will be availabel after the non-blind test phase opens.

### Blind Test Data

The blind test data will be availabel after the non-blind test phase opens.


## Evaluation

Systems will be evaluated using correlation and error metrics — MSE (Mean Square Error), LCC (linear correlation coefficient), SRCC (Spearman’s rank correlation coefficient), and KTAU (Kendall’s tau) — between the predicted MOS and the provided MOS labels.
