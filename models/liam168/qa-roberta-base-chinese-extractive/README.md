---
language: zh
widget: 
- text: "著名诗歌《假如生活欺骗了你》的作者是"
  context: "普希金从那里学习人民的语言，吸取了许多有益的养料，这一切对普希金后来的创作产生了很大的影响。这两年里，普希金创作了不少优秀的作品，如《囚徒》、《致大海》、《致凯恩》和《假如生活欺骗了你》等几十首抒情诗，叙事诗《努林伯爵》，历史剧《鲍里斯·戈都诺夫》，以及《叶甫盖尼·奥涅金》前六章。"
---
# Chinese RoBERTa-Base Model for QA

## Model description

用中文预料微调的QA模型.

## Overview

- **Language model**: RoBERTa-Base
- **Model size**: 400M
- **Language**: Chinese
  
## How to use

You can use the model directly with a pipeline for extractive question answering:

```python
>>> from transformers import AutoModelForQuestionAnswering,AutoTokenizer,pipeline
>>> context = '卡利亚·基拔（，）生于英国汉默史密斯，是一名英格兰籍职业足球员，于2010年夏季约满离开母会阿仙奴。直到2005/06年，基拔通常在阿仙奴的青年后备队效力。他在首次在2005年11月29日的联赛杯赛事上场，并于12月7日，在一个欧洲联赛冠军杯比赛对阿积士，作为替代左后卫，入替受伤的劳伦。2006年7月21日阿仙奴宣布，将基拔出借卡迪夫城整个2006-07赛季，其后转借给修安联。2008年1月3日返回阿仙奴授予46号码。2008年2月11日，阿仙奴的英超联赛比赛中对布莱克本作为后备球员。但2008年7月10日，基拔被出借莱斯特城的一个赛季之久。2009年3月3日主场对-{zh-hans:斯托克港;zh-hk:史托港}-，开赛后仅两分钟，基拔的传中球「挞Q」却直入网角，是他个人首个入球。基拔在外借期间成为常规正选，整季上阵达39场及射入1球，协助莱斯特城赢取英甲联赛冠军及重返英冠。2009/10年上半季仅于两场英格兰联赛杯及一场无关痛痒的欧联分组赛上阵，将于季后约满的基拔获外借到英冠榜末球会彼德堡直到球季结束，期间上阵10场。2010年夏季基拔约满阿仙奴成为自由球员，仅为母会合共上阵10场，英超「升班马」黑池有意罗致，其后前往-{zh-hans:谢菲尔德联; zh-hk:锡菲联;}-参加试训，惟未有获得录用。'
>>> mode_name = 'liam168/qa-roberta-base-chinese-extractive'
>>> model = AutoModelForQuestionAnswering.from_pretrained(mode_name)
>>> tokenizer = AutoTokenizer.from_pretrained(mode_name)
>>> QA = pipeline('question-answering', model=model, tokenizer=tokenizer)
>>> QA_input = {'question': "卡利亚·基拔的职业是什么?",'context': context}
>>> QA(QA_input)
    {'score': 0.9999, 'start': 20, 'end': 31, 'answer': '一名英格兰籍职业足球员'}
```

## Contact

liam168520@gmail.com
