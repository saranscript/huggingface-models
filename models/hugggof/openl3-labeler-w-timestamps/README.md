---
tags:
- audacity
inference: false
---

# Labeler With Timestamps
## Being used for the `Audio Labeler` effect in Audacity

This is a audio labeler model which is used in Audacity's labeler effect. 

metadata: 
```
{
               "sample_rate": 48000, 
               "domain_tags": ["Music"], 
               "tags": ["Audio Labeler"], 
               "effect_type": "waveform-to-labels",  
               "multichannel": false, 
               "labels": ["Acoustic Guitar", "Auxiliary Percussion", "Brass", "Clean Electric Guitar", "Distorted Electric Guitar", "Double Bass", "Drum Set", "Electric Bass", "Flute", "piano", "Reeds", "Saxophone", "Strings", "Trumpet", "Voice"], 
               "short_description": "Use me to label some instruments!", 
               "long_description": "An audio labeler, which outputs label predictions and time ranges for the labels. This model can label various instruments listed in the labels section."
}
 ```