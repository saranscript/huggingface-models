#                                         **Evaluation of the NER models in medical dataset**

The goal of the whole project is to  compare the NER models and feature evaluation in the medical dataset, and the program of model comparison needs to be executed in the GPU environment. Here are the instructions for the two project.


## 1. Model Comparison


### 1.1 Environment setting: 

(1) Python 3 environment (Python 3.6 and above)

The user can click the link (https://www.python.org/) to select the appropriate python version and download.


(2) Some related package in python

The version of the package we used is as follows:

```shell
Transformers: 4.8.2
NERDA: 0.9.5
Pytorch: 1.8.1+cu101
Tensorflow: 2.3.0
```

The user can execute the following command in python environment.

```shell
pip install tensorflow-gpu==2.3.0 -i https://pypi.doubanio.com/simple
pip install transformers==4.8.2
pip install NERDA
pip install sentencepiece
pip install torch==1.8.1+cu101 torchvision==0.9.1+cu101 torchaudio===0.8.1 -f https://download.pytorch.org/whl/torch_stable.html
```


### 1.2 The process of implementation 

(1) Training and testing 

Users can check the "training&testing.ipynb" file. The user can load the models to be trained and download them locally, or directly import it into the internal model of transformers website. 

For example:

```python
# Model loading in the "training&testing.ipynb" file

transformer = '../../Model/bigbird-roberta-base/'
or
transformer = 'google/bigbird-roberta-base'
```

Address of model download:

```http
https://huggingface.co/dmis-lab/biobert-base-cased-v1.1
https://huggingface.co/roberta-base
https://huggingface.co/google/bigbird-roberta-base
https://huggingface.co/microsoft/deberta-base
```

The user can download models through the above websites and put them in the "model" folder.

(2) Prediction program

Users can load the trained models and input new text to make that the model recognize the entities in the text. We give five trained models with the best training effect for RoBERTa, BigBird, DeBERTa, and BioBERT NER models ( The suffix of the five models ends with ". bin" ). These models is saved in "Trained model" file.

For example:

```python
import torch
model = torch.load('../../Trained model/deberta_x.bin')
model.predict_text('Number of glucocorticoid receptors in lymphocytes and their sensitivity to hormone action.')


->> ([['Number', 'of', 'glucocorticoid', 'receptors', 'in', 'lymphocytes', 'and', 'their', 'sensitivity', 'to', 'hormone','action','.']], 
[['O', 'O', 'B-protein','I-protein','o','B-cell_type','O','O','O','O','O','O','O']])
```


## 2. Feature Evaluation


### 2.1 Environment setting: 

(1) Some related package in python

Packages we used is as follows, users can download the latest packages by ”pip install package name“ commend.

```shell
1. warnings
2. matplotlib
3. pandas
4. seaborn
5. statsmodels
6. sklearn
```

### 2.2 The process of implementation 

Users can check the "feature_selection.ipynb" and "feature_evaluation.ipynb"file. Due to the privacy of the data, we did not upload the feature data, so users can view different methods of feature selection in this file.


### 3. Contact

If user have any questions, please contact us.

(1) Sizhu Wu - [wu.sizhu@imicams.ac.cn]

(2) Shengyu Liu - [liu.shengyu@imicams.ac.cn]