---
layout: page
permalink: /template_track2/
title: Template for README.yaml in each submission
description:  
nav: false
nav_order: 10
---

```yaml
#-------------------------------------------
# Basic information
#-------------------------------------------
team: your_team_name
team_email: email_for_receiving_notification
team_members:
    # Member 1
    1:
        name: member1_name
        affiliation: member1_affiliation
    # Member 2
    2:
        name: member2_name
        affiliation: member2_affiliation
    # Member 3
    3:
        name: member3_name
        affiliation: member3_affiliation

#-------------------------------------------
# Data description
#-------------------------------------------
# e.g., "bvcc bc19 somos tmhint-qi pstn tcd-voip tencent nisqa ttsds2 urgent24-sqa urgnet25-sqa"
training_data: 

# e.g., "same as official validation data"
validation_data: 


#-------------------------------------------
# System Description
#-------------------------------------------
# System types: provide one or more descriptions (free-form text allowed).
# You may use common terms or your own description.
# Examples:
#   - listener dependent:     Model takes listener id as input
#   - domain dependent:       Model takes domain id as input
#   - language dependent:     Model takes language id as input
#   - single-metric predictor: Predicts only MOS 
#   - multi-metric predictor: Predicts multiple metrics (e.g., MOS, SCOREQ, DNSMOS)
#   - supervised:             Fully supervised learning
#   - semi-supervised:         Uses labeled + unlabeled data
#   - self-supervised:         Uses self-supervised pretraining
#   - ensemble:                Combines multiple models
system_type: []

# Briefly describe the architecture here
# e.g., CNN, Transformer.
model_architecture:

# model parameter size in million, e.g., 6.23 [M]
model_size:

# Loss function(s) used, e.g., "CrossEntropy", "MSE"
loss_function: 


use_pretrained_models:  # true or false
pretrained_models:
    # example:
        # name: HuBERT-Large
        # link: https://huggingface.co/facebook/hubert-large-ll60k
        # usage: used for converting the input speech signal into discrete tokens

    # Pre-trained model 1
    1:
        name:
        link:
        usage:
    # Pre-trained model 2
    2:
        name:
        link:
        usage:
```
