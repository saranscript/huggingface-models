---
language: ar
datasets:
- tydiqa
widget:
- text: "ما هو نظام الحكم في لبنان؟"
  context: "لبنان أو (رسميا: الجمهورية اللبنانية)، هي دولة عربية واقعة في الشرق الأوسط في غرب القارة الآسيوية. تحدها سوريا من الشمال و الشرق، و فلسطين المحتلة - إسرائيل من الجنوب، وتطل من جهة الغرب على البحر الأبيض المتوسط. هو بلد ديمقراطي جمهوري طوائفي. معظم سكانه من العرب المسلمين و المسيحيين. وبخلاف غالبية الدول العربية هناك وجود فعال للمسيحيين في الحياة العامة والسياسية. هاجر وانتشر أبناؤه حول العالم منذ أيام الفينيقيين، وحاليا فإن عدد اللبنانيين المهاجرين يقدر بضعف عدد اللبنانيين المقيمين. واجه لبنان منذ القدم تعدد الحضارات التي عبرت فيه أو احتلت أراضيه وذلك لموقعه الوسطي بين الشمال الأوروبي والجنوب العربي والشرق الآسيوي والغرب الأفريقي، ويعد هذا الموقع المتوسط من أبرز الأسباب لتنوع الثقافات في لبنان، وفي الوقت ذاته من الأسباب المؤدية للحروب والنزاعات على مر العصور تجلت بحروب أهلية ونزاع مصيري مع إسرائيل. ويعود أقدم دليل على استيطان الإنسان في لبنان ونشوء حضارة على أرضه إلى أكثر من 7000 سنة. في القدم، سكن الفينيقيون أرض لبنان الحالية مع جزء من أرض سوريا و فلسطين، وهؤلاء قوم ساميون اتخذوا من الملاحة والتجارة مهنة لهم، وازدهرت حضارتهم طيلة 2500 سنة تقريبا (من حوالي سنة 3000 حتى سنة 539 ق.م). وقد مرت على لبنان عدة حضارات وشعوب استقرت فيه منذ عهد الفينيقين، مثل المصريين القدماء، الآشوريين، الفرس، الإغريق، الرومان، الروم البيزنطيين، العرب، الصليبيين، الأتراك العثمانيين، فالفرنسيين."  
---

<img src="https://raw.githubusercontent.com/WissamAntoun/arabic-wikipedia-qa-streamlit/main/is2alni_logo.png" width="150" align="center"/>


# Arabic QA

AraELECTRA powered Arabic Wikipedia QA system with Streamlit [![Open in Streamlit](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://share.streamlit.io/wissamantoun/arabic-wikipedia-qa-streamlit/main)

This model is trained on the Arabic section of ArTyDiQA using the colab here [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1hik0L_Dxg6WwJFcDPP1v74motSkst4gE?usp=sharing)

# How to use:
```bash
git clone https://github.com/aub-mind/arabert
pip install pyarabic
```
```python
from arabert.preprocess import ArabertPreprocessor
from transformers import pipeline

prep = ArabertPreprocessor("aubmindlab/araelectra-base-discriminator") #or empty string it's the same
qa_pipe =pipeline("question-answering",model="wissamantoun/araelectra-base-artydiqa")

text = " ما هو نظام الحكم في لبنان؟"
context = """
لبنان أو (رسميًّا: الجُمْهُورِيَّة اللبنانيَّة)، هي دولة عربيّة واقِعَة في الشَرق الأوسط في غرب القارة الآسيويّة. تَحُدّها سوريا من الشمال و‌الشرق، و‌فلسطين المحتلة - إسرائيل من الجنوب، وتطل من جهة الغرب على البحر الأبيض المتوسط. هو بلد ديمقراطي جمهوري طوائفي. مُعظم سكانه من العرب المسلمين و‌المسيحيين. وبخلاف غالبيّة الدول العربيّة هناك وجود فعّال للمسيحيين في الحياة العامّة والسياسيّة. هاجر وانتشر أبناؤه حول العالم منذ أيام الفينيقيين، وحاليًّا فإن عدد اللبنانيين المهاجرين يُقدَّر بضعف عدد اللبنانيين المقيمين.
واجه لبنان منذ القدم تعدد الحضارات التي عبرت فيه أو احتلّت أراضيه وذلك لموقعه الوسطي بين الشمال الأوروبي والجنوب العربي والشرق الآسيوي والغرب الأفريقي، ويعد هذا الموقع المتوسط من أبرز الأسباب لتنوع الثقافات في لبنان، وفي الوقت ذاته من الأسباب المؤدية للحروب والنزاعات على مر العصور تجلت بحروب أهلية ونزاع مصيري مع إسرائيل. ويعود أقدم دليل على استيطان الإنسان في لبنان ونشوء حضارة على أرضه إلى أكثر من 7000 سنة.
في القدم، سكن الفينيقيون أرض لبنان الحالية مع جزء من أرض سوريا و‌فلسطين، وهؤلاء قوم ساميون اتخذوا من الملاحة والتجارة مهنة لهم، وازدهرت حضارتهم طيلة 2500 سنة تقريبًا (من حوالي سنة 3000 حتى سنة 539 ق.م). وقد مرّت على لبنان عدّة حضارات وشعوب استقرت فيه منذ عهد الفينيقين، مثل المصريين القدماء، الآشوريين، الفرس، الإغريق، الرومان، الروم البيزنطيين، العرب، الصليبيين، الأتراك العثمانيين، فالفرنسيين.
"""

context = prep.preprocess(context)# don't forget to preprocess the question and the context to get the optimal results
result = qa_pipe(question=text,context=context)
"""
{'answer': 'ديمقراطي جمهوري طوائفي',
 'end': 241,
 'score': 0.4910127818584442,
 'start': 219}
 """
 ```
 
 # If you used this model please cite us as :
 ```
@misc{antoun2020araelectra,
      title={AraELECTRA: Pre-Training Text Discriminators for Arabic Language Understanding},
      author={Wissam Antoun and Fady Baly and Hazem Hajj},
      year={2020},
      eprint={2012.15516},
      archivePrefix={arXiv},
      primaryClass={cs.CL}
}
```