---
tags:
- audacity
inference: false
---

# Text to Speech Model
## Being used for the `Audio Labeler` effect in Audacity

metadata: 
```
{
metadata = {
    'sample_rate': 16000, 
    'domain_tags': ['speech'],
    'short_description': 'I will label your speech into text :]',
    'long_description': 
              'This is an Audacity wrapper for the model, '
              'forked from the repository '
              'facebook/s2t-medium-librispeech-asr'
              'This model was trained by Changhan Wang'
              'and Yun Tang and Xutai Ma and Anne Wu' 
              'and Dmytro Okhonko and Juan Pino.',
    'tags': ['speech-to-text'],
    'effect_type': 'waveform-to-labels',
    'multichannel': False,
    'labels': ["<pad>", "<s>", "</s>", "<unk>", "|", "E", "T", "A", "O", "N", "I", "H", "S", "R", "D", "L", "U", "M", "W", "C", "F", "G", "Y", "P", "B", "V", "K", "'", "X", "J", "Q", "Z"], 
}
 ```