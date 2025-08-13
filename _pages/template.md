---
layout: page
permalink: /template/
title: Template for README.yaml in each submission
description:  
nav: false
nav_order: 10
---

```yaml
#-------------------------------------------
# Basic information
#-------------------------------------------
team: your_teamname
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
# e.g., "simulated on the fly using the official configuration"
training_data: 

use_additional_rirs:  # true or false
additional_rir_info:
    # example:
        # is_real: True
        # source: https://url.to.real.rirs
        # number_of_samples: 1000

    # RIR 1 (for real RIRs, only those included in the official data list are allowed)
    1:
        is_real:
        source:
        number_of_samples:
    # RIR 2
    2:
        is_real:
        source:
        number_of_samples:

# e.g., "same as official validation data"
validation_data: 


#-------------------------------------------
# System description
#-------------------------------------------
# "discriminative", "generative", "discriminative followed by generative", etc.
system_type: 

# please briefly describe the architecture here
# e.g., CNN, Transformer.
model_architecture:

# model parameter size in million, e.g., 6.23 [M]
model_size:

# time, time-frequency, etc.
domain:

# please briefly describe loss function here
# e.g., "time-domain si-snr", "time-domain l1 + TF-domain gan", etc.
loss_funcition:

# please briefly describe data augmentation here
# mp3 compression, wind noise, etc.
data_augmentation: 


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
