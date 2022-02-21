# Reddit exercise feedback classification

Model to classify Reddit's comments for exercise feedback. Current classes are good, correction, bad posture, not informative. If you want to use it locally,

### Usage:
```py
from transformers import pipeline
classifier = pipeline("text-classification", "kittinan/exercise-feedback-classification")
classifier("search for alan thrall deadlift video he will explain basic ques")
#[{'label': 'correction', 'score': 0.9998193979263306}]
```