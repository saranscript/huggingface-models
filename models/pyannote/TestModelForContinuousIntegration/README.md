---
tags:
- pyannote
- pyannote-audio-model
license: mit
inference: false
---

## Dummy model used for continuous integration purposes

```bash
$ pyannote-audio-train protocol=Debug.SpeakerDiarization.Debug \
                       task=VoiceActivityDetection \
                       task.duration=2. \
                       model=DebugSegmentation \
                       trainer.max_epochs=10
```
