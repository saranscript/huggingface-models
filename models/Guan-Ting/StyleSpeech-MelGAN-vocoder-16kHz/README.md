### The MelGAN vocoder for StyleSpeech
#### About StyleSpeech
* StyleSpeech or Meta-StyleSpeech is a model for Multi-Speaker Adaptive Text-to-Speech Generation
* The StyleSpeech model can be trained by official implementation (https://github.com/KevinMIN95/StyleSpeech).
#### About MelGAN vocoder
* This MelGAN vocoder is used to transform the mel-spectrogram back to the waveform. 
* StyleSpeech is based on 16k Hz sampling rate, and there is no available 16k Hz multi-speaker vocoder.
* Thus I train this vocoder from scratch using Libri-TTS train-100 hour dataset. The training pipeline is the same as the official MelGAN (https://github.com/descriptinc/melgan-neurips).
* The synthesized sounds are close to the official demo with good quality.
#### Usage
* Please follow the official MelGAN (https://github.com/descriptinc/melgan-neurips) to load pre-trained checkpoint and convert your mel-spectrogram back to the waveform.

#### Training Details 
* GPU: RTX 2080Ti
* Training epoch: 3000
