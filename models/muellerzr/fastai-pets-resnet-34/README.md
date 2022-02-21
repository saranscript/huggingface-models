# The fastai models - PETS

This model is based on Lesson 1 of [fastai](https://course.fast.ai) and of [Walk with fastai](https://walkwithfastai.com/Pets)

## Dataset Used
This model was created with the [Oxford Pets](https://docs.fast.ai/data.external.html#Image-Classification-datasets) dataset in the fastai framework

## Model Training
The model was trained as a binary classifier, for cats or dogs

## How to use:
First, ensure that `huggingface_hub` is installed:
```bash
pip(3) install huggingface_hub
```
Next, download this model repo:
```python
from huggingface_hub import snapshot_download
snapshot_download(repo_id="muellerzr/fastai-pets-resnet-34")
```
Then install the correct fastai version:
```bash
cd fastai-pets-resnet34
pip(3) install -r requirements.txt
```
**NOTE: This is extremely important, as fastai versions are aggressively pinned based on training environment**

And finally load in the fastai `Learner` and predict
```python
from fastai.learner import load_learner
learn = load_learner('model.pth')
pred = learn.predict('myImage.jpg')
```

Versions of model used were taken with [dependency_checker](https://muellerzr.github.io/dependency_checker)
