---
language: 
  - "en"
license: "cc-by-sa-4.0"
datasets:
- debatelab/aaac
widget:
- text: "reason_statements: argument_source: If Peter likes fish, Peter has been to New York. So, Peter has been to New York."
  example_title: "Premise identification"
- text: "argdown_reconstruction: argument_source: If Peter likes fish, Peter has been to New York. So, Peter has been to New York."
  example_title: "Argdown reconstruction"
- text: "premises_formalized: reason_statements: If Peter likes fish, Peter has been to New York. (ref: (1))"
  example_title: "Formalization"
inference:
  parameters:
    max_length: 80
---

Pretraining Dataset: [AAAC01](https://huggingface.co/datasets/debatelab/aaac)

Demo: [DeepA2 Demo](https://huggingface.co/spaces/debatelab/deepa2-demo)

Paper: [DeepA2: A Modular Framework for Deep Argument Analysis with Pretrained Neural Text2Text Language Models](https://arxiv.org/abs/2110.01509)

Authors: *Gregor Betz, Kyle Richardson*

## Abstract

In this paper, we present and implement a multi-dimensional, modular framework for performing deep argument analysis (DeepA2) using current pre-trained language models (PTLMs). ArgumentAnalyst -- a T5 model (Raffel et al. 2020) set up and trained within DeepA2 -- reconstructs argumentative texts, which advance an informal argumentation, as valid arguments: It inserts, e.g., missing premises and conclusions, formalizes inferences, and coherently links the logical reconstruction to the source text. We create a synthetic corpus for deep argument analysis, and evaluate ArgumentAnalyst on this new dataset as well as on existing data, specifically EntailmentBank (Dalvi et al. 2021). Our empirical findings vindicate the overall framework and highlight the advantages of a modular design, in particular its ability to emulate established heuristics (such as hermeneutic cycles), to explore the model's uncertainty, to cope with the plurality of correct solutions (underdetermination), and to exploit higher-order evidence.