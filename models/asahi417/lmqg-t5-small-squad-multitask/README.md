---
language: 
  - en
tags:
- question generation
- question answer generation
license: mit
datasets:
- squad
metrics:
- bleu
- meteor
- rouge
widget:
- text: "generate question: <hl> Beyonce <hl> further expanded her acting career, starring as blues singer Etta James in the 2008 musical biopic, Cadillac Records."
  example_title: "Question Generation Example 1"
- text: "generate question: Beyonce further expanded her acting career, starring as blues singer <hl> Etta James <hl> in the 2008 musical biopic, Cadillac Records."
  example_title: "Question Generation Example 2"
- text: "generate question: Beyonce further expanded her acting career, starring as blues singer Etta James in the 2008 musical biopic,  <hl> Cadillac Records  <hl> ."
  example_title: "Question Generation Example 3"
- text: "extract answers: <hl> Beyonce further expanded her acting career, starring as blues singer Etta James in the 2008 musical biopic, Cadillac Records. <hl>"
  example_title: "Answer Extraction Example 1"
---

# T5 finetuned on Question Generation
T5 model for question generation. Please visit [our repository](https://github.com/asahi417/t5-question-generation) for more detail.