---
language: english
datasets:
- bioASQ
pipeline_tag: question-answering
license: mit
---

# T5-base model fine-tuned on BioASQ for Biological Question Answering 👩‍⚕️👨‍⚕️
[Google's T5-base](https://huggingface.co/t5-base) fine-tuned on [BioASQ](https://github.com/dmis-lab/biobert) (secondary task) for **Q&A** downstream task.

## Details of T5
[Google's T5](https://ai.googleblog.com/2020/02/exploring-transfer-learning-with-t5.html) 

Pretraining Dataset: [C4](https://huggingface.co/datasets/c4)

Paper: [Exploring the Limits of Transfer Learning with a Unified Text-to-Text Transformer](https://arxiv.org/pdf/1910.10683.pdf)

Authors: *Colin Raffel, Noam Shazeer, Adam Roberts, Katherine Lee, Sharan Narang, Michael Matena, Yanqi Zhou, Wei Li, Peter J. Liu* 

## Dependencies

transformers == 4.3.3

sentencepiece >= 0.1.94

## Usage 🚀

```python
import torch
from transformers import T5ForConditionalGeneration, T5Tokenizer

tokenizer = T5Tokenizer.from_pretrained("ozcangundes/T5-base-for-BioQA")
model = T5ForConditionalGeneration.from_pretrained("ozcangundes/T5-base-for-BioQA")

def get_answer(question,context):
  source_encoding=tokenizer(
    question,
    context,
    max_length=512,
    padding="max_length",
    truncation="only_second",
    return_attention_mask=True,
    add_special_tokens=True,
    return_tensors="pt")
  
  generated_ids=model.generate(
      input_ids=source_encoding["input_ids"],
      attention_mask=source_encoding["attention_mask"])

  preds=[tokenizer.decode(gen_id, skip_special_tokens=True, clean_up_tokenization_spaces=True) for gen_id in generated_ids]

  return "".join(preds)
```

### Example 1
```python
question={
    "context":"Effect of food on the pharmacokinetics of empagliflozin, a sodium glucose cotransporter 2 (SGLT2) inhibitor, and assessment of dose proportionality in healthy volunteers. OBJECTIVES: Empagliflozin is an orally available, potent and highly selective inhibitor of the sodium glucose cotransporter 2 (SGLT2). This study was undertaken to investigate the effect of food on the pharmacokinetics of 25 mg empagliflozin and to assess dose proportionality between 10 mg and 25 mg empagliflozin under fasted conditions. MATERIALS AND METHODS: In this open-label, 3-way, cross-over study, 18 healthy volunteers received 3 single doses of empagliflozin in a randomized sequence (25 mg empagliflozin under fasted conditions, 25 mg empagliflozin after a high-fat, high-calorie breakfast and 10 mg empagliflozin under fasted conditions), each separated by a washout period of at least 7 days. Serial plasma samples were collected at selected time points over a period of 72 hours. RESULTS: Administration with food had no clinically relevant effect on the area under the plasma concentration-time curve (AUC0-∞) of empagliflozin (geometric mean ratio (GMR): 84.04, 90% confidence interval (CI): 80.86 - 87.34). The decrease observed in the maximum plasma concentrations (Cmax) of empagliflozin (GMR: 63.22, 90% CI: 56.74 - 70.44) when administered with food was not considered clinically meaningful. The increases in AUC0-∞ and Cmax for 10 mg vs. 25 mg empagliflozin administered under fasting conditions were roughly dose-proportional, as demonstrated by the slope β of the regression lines being slightly less than 1 (slope β for AUC0-∞: 0.94, 95% CI: 0.90 - 0.97; slope β for Cmax: 0.91, 95% CI: 0.80 - 1.01). Empagliflozin was well tolerated under fed and fasting conditions. CONCLUSIONS: The results support administration of empagliflozin tablets independently of food. Increases in empagliflozin exposure under fasting conditions were roughly dose-proportional between 10 mg and 25 mg empagliflozin.",
    "question":"Which protein does empagliflozin inhibit?"
    }
    
get_answer(question["question"],question["context"])
```
> SGLT2

### Example 2
```python
question2={
    "context":"Dermatitis herpetiformis: jejunal findings and skin response to gluten free diet. Fifty seven children with dermatitis herpetiformis, 18 from Finland and 39 from Hungary, were studied. Diagnostic criteria included the finding of granular IgA deposits in the skin of all patients. The mean age at onset of the rash was 7 X 2 years and favoured sites were the elbows, knees, and buttocks. Symptoms suggesting small intestinal disease were rare but in 35 (61%) of the children subtotal villous atrophy and in 16 (28%) partial villous atrophy were found on jejunal biopsy. Eighteen children underwent a second biopsy after a mean of 21 months on a gluten free diet; villous height was found to be increased and the intraepithelial lymphocyte count decreased in all these patients. Gluten challenge caused a reversal in the two children who underwent a third biopsy. The effect of the gluten free diet on the rash was examined in Finnish children by observing the daily requirements of dapsone, a drug used to control the rash at the beginning of the diet. Eight (67%) of the 12 children were able to stop taking dapsone after a mean of 11 months on the diet and all three patients treated with diet alone became asymptomatic after three to 6 months on the diet. These results confirm that most children with dermatitis herpetiformis have jejunal villous atrophy, though they rarely have gastrointestinal symptoms. The central role of gluten in childhood dermatitis herpetiformis is evidenced by the fact that a gluten free diet helps the damaged jejunal mucosa to recover and controls the rash even in those children who do not have an abnormal jejunal biopsy.",
    "question":"What is the typical rash associated with gluten?"
    }
    
get_answer(question2["question"],question2["context"])
```
> dermatitis herpetiformis

Created by Özcan Gündeş ✌️
---

Twitter: <a href="https://twitter.com/ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/twitter.svg" alt="ozcangundes" height="30" width="30" /></a>
Linkedin: <a href="https://www.linkedin.com/in/%C3%B6zcan-g%C3%BCnde%C5%9F-7693055b/" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg" alt="13198517" height="30" width="30" /></a>
Medium: <a href="https://medium.com/@ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/medium.svg" alt="@ozcangundes" height="30" width="30" /></a>
Github: <a href="https://github.com/ozcangundes" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/github.svg" alt="@ozcangundes" height="30" width="30" /></a>
