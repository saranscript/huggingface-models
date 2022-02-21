---
language: tr
---
# Logo Turkish Question Answering Model : Question Answering

Inspired by savasy/bert-base-turkish-squad, 
* Inspired model: https://huggingface.co/savasy/bert-base-turkish-squad
* BERT-base: https://huggingface.co/dbmdz/bert-base-turkish-uncased
* Dataset:  Logo Private QnA Chatbot Database

# Training Code
```
model_args = QuestionAnsweringArgs()
model_args.train_batch_size = 16
model_args.evaluate_during_training = True
model_args.n_best_size=3
model_args.num_train_epochs=5

train_args = {
    "reprocess_input_data": True,
    "overwrite_output_dir": True,
    "use_cached_eval_features": True,
    "output_dir": f"outputs/bert",
    "best_model_dir": f"outputs/bert/best_model1",
    "evaluate_during_training": True,
    "max_seq_length": 128,
    "num_train_epochs": 10,
    "evaluate_during_training_steps": 1000,
    "wandb_project": "Question Answer Application",
    "wandb_kwargs": {"name": "dbmdz/bert-base-turkish-uncased\"},
    "save_model_every_epoch": False,
    "save_eval_checkpoints": False,
    "n_best_size":3,
    # "use_early_stopping": True,
    # "early_stopping_metric": "mcc",
    "n_gpu": 4,
    # "manual_seed": 4,
    "use_multiprocessing": True,
    "train_batch_size": 126,
    "eval_batch_size": 64,
    # "config": {
    #     "output_hidden_states": True
    # }
}
model = QuestionAnsweringModel(
    "bert","dbmdz/bert-base-turkish-uncased\", args=train_args
)

model.train_model(train, eval_data=test)
```
# Dataset Sample
```
{
        "context": "Varlıklara ait yeniden değerleme toplamlarının özet olarak alındığı rapor seçeneğidir. Varlık Yönetimi program bölümünde Raporlar menüsü altında yer alır. Rapor yıllık olarak alınır. Toplamların alınacağı yıl, Yıl filtre satırında belirtilir. Rapor filtre seçenekleri aşağıdaki tabloda yer almaktadır.",
        "qas": [
            {
                "id": "01017",
                "is_impossible": false,
                "question": "Yeniden Değerleme Özeti ne işe yarar",
                "answers": [
                    {
                        "text": "Varlıklara ait yeniden değerleme toplamlarının özet olarak alındığı rapor seçeneğidir.",
                        "answer_start": 0
                    }
                ]
            },
            {
                "id": "01018",
                "is_impossible": false,
                "question": " Yeniden Değerleme Özetine nereden ulaşırım",
                "answers": [
                    {
                        "text": "Varlık Yönetimi program bölümünde Raporlar menüsü altında yer alır.",
                        "answer_start": 87
                    }
                ]
            }
        }

```
# Example Usage

> Load Model
```
#Required Libraries
from transformers import AutoTokenizer, AutoModelForQuestionAnswering, pipeline
import torch
#Model Path
hface_path = "yunusemreemik/logo-qna-model"
#For tokenize context and question
tokenizer = AutoTokenizer.from_pretrained(hface_path)
#For generate NN eval outputs
model = AutoModelForQuestionAnswering.from_pretrained(hface_path)
#For functional pipe
nlp = pipeline("question-answering", model=model, tokenizer=tokenizer)
```
> Apply the model.
> Please dont forget the delete backslashes "\" before run
```
e_arsiv ="e-Arşiv Tipleri, e-Arşiv fatura türünün belirlendiği alandır. İlgili cari hesap kartında \\nLogoConnect sayfasında belirlenen e-arşiv tipi alana öndeğer olarak \\naktarılır. Standart faturalar için herhangi bir seçim yapılmaz. \\nÖzel matrah uygulanan tütün, altın, gümüş, gazete, dergi, belediye \\nşehir yolcu taşımacılığı ve telefon kartı satışları için kesilen faturalar. \\nİstisna uygulanan faturalar. (İhracat teslimleri ve bu teslimlere ilişkin hizmetler, \\nmal ihracatı, hizmet ihracatı, serbest bölgelerdeki müşteriler için yapılan fason hizmetler vs..) \\nAraç Tescil Faturası, Araç tescil için kesilen faturalardır."

answer_text = nlp(question="İlgili cari hesap kartları nerede belirlenir?", context=e_arsiv)
print(answer_text )

```
```

print(nlp(question="", context=e_arsiv))
```
# Evaluation
```
(160,
 {'global_step': [16, 32, 48, 64, 80, 96, 112, 128, 144, 160],
  'correct': [11, 15, 18, 18, 19, 16, 16, 16, 14, 14],
  'similar': [23, 26, 22, 21, 21, 24, 24, 23, 25, 25],
  'incorrect': [8, 1, 2, 3, 2, 2, 2, 3, 3, 3],
  'train_loss': [0.8277238607406616,
   0.7876648306846619,
   0.44657397270202637,
   0.32337626814842224,
   0.2009371519088745,
   0.15247923135757446,
   0.11289173364639282,
   0.06762214750051498,
   0.06813357770442963,
   0.04011240229010582],
  'eval_loss': [-9.3046875,
   -8.8984375,
   -9.1171875,
   -9.03125,
   -9.046875,
   -8.984375,
   -9.1171875,
   -9.296875,
   -9.296875,
   -9.296875]})
```