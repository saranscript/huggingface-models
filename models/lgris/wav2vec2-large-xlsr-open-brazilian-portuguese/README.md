---
language: pt
datasets:
- common_voice 
- mls
- cetuc
- lapsbm
- voxforge
metrics:
- wer
tags:
- audio
- speech
- wav2vec2
- pt
- portuguese-speech-corpus
- automatic-speech-recognition
- speech
- PyTorch
license: apache-2.0
model-index:
- name: Lucas Gris XLSR Wav2Vec2 Large 53 Brazilian Portuguese 
  results:
  - task: 
      name: Speech Recognition
      type: automatic-speech-recognition
    metrics:
       - name: Test WER
         type: wer
         value: 12.905054857823264%
---

# Wav2vec 2.0 With Open Brazilian Portuguese Datasets

This a the demonstration of a fine-tuned Wav2vec model for Brazilian Portuguese using the following datasets:

- [CETUC](http://www02.smt.ufrj.br/~igor.quintanilha/alcaim.tar.gz): contains approximately 145 hours of Brazilian Portuguese speech distributed among 50 male and 50 female speakers, each pronouncing approximately 1,000 phonetically balanced sentences selected from the [CETEN-Folha](https://www.linguateca.pt/cetenfolha/) corpus.
- [Multilingual Librispeech (MLS)](https://arxiv.org/abs/2012.03411): a massive dataset available in many languages. The MLS is based on audiobook recordings in public domain like [LibriVox](https://librivox.org/). The dataset contains a total of 6k hours of transcribed data in many languages. The set in Portuguese [used in this work](http://www.openslr.org/94/) (mostly Brazilian variant) has approximately 284 hours of speech, obtained from 55 audiobooks read by 62 speakers.
- [VoxForge](http://www.voxforge.org/): is a project with the goal to build open datasets for acoustic models. The corpus contains approximately 100 speakers and 4,130 utterances of Brazilian Portuguese, with sample rates varying from 16kHz to 44.1kHz.
- [Common Voice 6.1](https://commonvoice.mozilla.org/pt) (_only train_): is a project proposed by Mozilla Foundation with the goal to create a wide open dataset in different languages to train ASR models. In this project, volunteers donate and validate speech using the [oficial site](https://commonvoice.mozilla.org/pt). The set in Portuguese (mostly Brazilian variant) used in this work is the 6.1 version (pt_63h_2020-12-11) that contains about 50 validated hours and 1,120 unique speakers.
- [Lapsbm](https://github.com/falabrasil/gitlab-resources): "Falabrasil - UFPA" is a dataset used by the Fala Brasil group to benchmark ASR systems in Brazilian Portuguese. Contains 35 speakers (10 females), each one pronouncing 20 unique sentences, totalling  700 utterances in Brazilian Portuguese. The audios were recorded in 22.05 kHz without environment control.

These datasets were combined to build a larger Brazilian Portuguese dataset. All data was used for training except Common Voice dev/test sets, that were used for validation/test respectively.

The original model was fine-tuned using [fairseq](https://github.com/pytorch/fairseq). This notebook uses a converted version of the original one. The link to the original fairseq model is available [here](https://drive.google.com/drive/folders/1XTKIUB4kp3oYOavwH97wq8IPFsxP5sNz?usp=sharing).

This model was trained in 80k updates.

#### Datasets in number of instances and number of frames

The following image shows the overall distribution of the dataset:

![datasets](https://drive.google.com/uc?export=view&id=1DF2_PehB2pZlEJLcBA7yeZQ9EAuLGh_r)

#### Transcription examples

| Text                                                                                                       | Transcription                                                                                                |
|------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| É comum os usuários confundirem software livre com software livre                                          | É comum os __usuares__ __confunder em__ __softwerlivr__ com __softwerlivre__                                          |
| Ele fez tanto ghostwriting que ele começa a se sentir como um fantasma também                              | Ele fez tanto __golstraitn__ que ele __começou__ a se sentir como um fantasma também                           |
| Arnold apresentou um gráfico mostrando quantas cegonhas ele havia contado nos últimos dez anos             | Arnold apresentou um gráfico mostrando quantas __segonhas__ ele havia contado nos últimos dez anos            |
| Mais cedo ou mais tarde eles descobrirão como ler esses hieróglifos                                        | Mais __sedo__ ou mais tarde eles descobriram como __de__ esses __ierogrôficos__                                 |
| Viver juntos compartilhar objetivos e ter um bom relacionamento                                            | __E ver__ juntos __signafica__ viver juntos ou __fartlhar__ objetivos ter um bom __relacionamentoo__             |
| Da mesma forma uma patente pode impedir que concorrentes desenvolvam produtos similares                    | Da mesma forma uma patente pode impedir que concorrentes __desenvolva__ produtos similares                    |
| Duas mulheres e uma menina levantam com troféus                                                            | Duas mulheres e uma menina levantam com __trofés__                                                            |
| Esse acrobata de circo deve ter um sistema vestibular bem treinado pensou o espectador                     | Esse acrobata de __cirko__ deve ter um sistema vestibular __bemtreinado__ pensou o espectador                  |
| Durante a exposição o tribunal pode fazer quaisquer perguntas ou esclarecimentos que considere apropriados | Durante a exposição o tribunal pode fazer quaisquer perguntas ou esclarecimentos que considere __apropriado__ |

## Imports and dependencies


```python
%%capture
!pip install datasets
!pip install jiwer
!pip install torchaudio
!pip install transformers
!pip install soundfile
```


```python
import torchaudio
from datasets import load_dataset, load_metric
from transformers import (
    Wav2Vec2ForCTC,
    Wav2Vec2Processor,
)
import torch
import re
import sys
```

## Preparation


```python
chars_to_ignore_regex = '[\,\?\.\!\;\:\"]'  # noqa: W605
wer = load_metric("wer")
device = "cuda"
```

```python
model_name = 'lgris/wav2vec2-large-xlsr-open-brazilian-portuguese'
model = Wav2Vec2ForCTC.from_pretrained(model_name).to(device)
processor = Wav2Vec2Processor.from_pretrained(model_name)
```

```python
def map_to_pred(batch):
    features = processor(batch["speech"], sampling_rate=batch["sampling_rate"][0], padding=True, return_tensors="pt")
    input_values = features.input_values.to(device)
    attention_mask = features.attention_mask.to(device)
    with torch.no_grad():
        logits = model(input_values, attention_mask=attention_mask).logits
    pred_ids = torch.argmax(logits, dim=-1)
    batch["predicted"] = processor.batch_decode(pred_ids)
    batch["predicted"] = [pred.lower() for pred in batch["predicted"]]
    batch["target"] = batch["sentence"]
    return batch
```

## Tests

### Test against Common Voice (In-domain)


```python
dataset = load_dataset("common_voice", "pt", split="test", data_dir="./cv-corpus-6.1-2020-12-11")

resampler = torchaudio.transforms.Resample(orig_freq=48_000, new_freq=16_000)

def map_to_array(batch):
    speech, _ = torchaudio.load(batch["path"])
    batch["speech"] = resampler.forward(speech.squeeze(0)).numpy()
    batch["sampling_rate"] = resampler.new_freq
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch
```

```python
ds = dataset.map(map_to_array)
result = ds.map(map_to_pred, batched=True, batch_size=1, remove_columns=list(ds.features.keys()))
print(wer.compute(predictions=result["predicted"], references=result["target"]))
for pred, target in zip(result["predicted"][:10], result["target"][:10]):
    print(pred, "|", target) 
```

    0.12905054857823264
    nem o varanin os altros influmindo os de teterno um bombederster | nem o radar nem os outros instrumentos detectaram o bombardeiro stealth
    pedir dinheiro é emprestado das pessoas do aldeia | pedir dinheiro emprestado às pessoas da aldeia
    oito | oito
    teno calcos | trancá-los
    realizaram a investigação para resolver o problema | realizar uma investigação para resolver o problema
    iotube ainda é a melhor plataforma de vídeos | o youtube ainda é a melhor plataforma de vídeos
    menina e menino beijando nas sombras | menina e menino beijando nas sombras
    eu sou o senhor | eu sou o senhor
    duas metcas sentam-se para baixo randes jornais | duas mulheres que sentam-se para baixo lendo jornais
    eu originalmente esperava | eu originalmente esperava


**Result**: 12.90%

### Test against [TEDx](http://www.openslr.org/100/) (Out-of-domain)


```python
!gdown --id 1HJEnvthaGYwcV_whHEywgH2daIN4bQna
!tar -xf tedx.tar.gz
```

```python
dataset = load_dataset('csv', data_files={'test': 'tedx/test.csv'})['test']

def map_to_array(batch):
    speech, _ = torchaudio.load(batch["path"])
    batch["speech"] = speech.squeeze(0).numpy()
    batch["sampling_rate"] = resampler.new_freq
    batch["sentence"] = re.sub(chars_to_ignore_regex, '', batch["sentence"]).lower().replace("’", "'")
    return batch
```

```python
ds = dataset.map(map_to_array)
result = ds.map(map_to_pred, batched=True, batch_size=1, remove_columns=list(ds.features.keys()))
print(wer.compute(predictions=result["predicted"], references=result["target"]))
for pred, target in zip(result["predicted"][:10], result["target"][:10]):
    print(pred, "|", target) 
```

    0.35215851987208774
    com isso a gente vê que essa rede de pactuação de de deparcerias nos remete a um raciocínio lógico que ao que a gente crê que é a prevenção | com isso a gente vê que essa rede de pactuação de parcerias nos remete a um raciocínio lógico que é o que a gente crê que é a prevenção
    ente vai para o resultado | e aí a gente vai pro resultado
    curiosidade hé o que eu descobri desde que comecei a fazer pesquisa lá no ensino médio | e a curiosidade é algo que descobri desde que comecei a fazer pesquisa lá no ensino médio
    val des quemesho | há vários caminhos
    que é uma opcissão por comer soldado | que é uma obsessão por comer saudável
    isso é tão é forte algoltão universal que existem dados que mostram que setenta e cinco por cento das reuniões são dominadas pela voz masculina | e isso é tão forte é algo tão universal que existem dados que mostram que  das reuniões são dominadas pela voz masculina
    não era exatamente isso não estávamos deveto | e não era exatamente isso que nós estávamos a ver
    durante meci do médio ofiz pesquisa estudei numa escola que chamam a fundação liberate ficava relativamente próximo daqui | durante o ensino médio eu fiz pesquisa estudei numa escola que se chama fundação liberato que fica relativamente próxima daqui
    oito anos atrás eu fui apresentado por uma doença que até então eu não conhecia e que é bem provável que a maior parte de nós todos aqui não conheçamos | oito anos atrás fui apresentado para uma doença que até então eu não conhecia e que é bem provável que a maior parte de nós todos aqui não conheçamos
    o terceiro é o museu do ripiopeco | o terceiro é o museu do hip hop


**Result**: 35.21%