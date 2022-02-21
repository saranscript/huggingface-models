---
license: apache-2.0
datasets:
- billsum
tags:
- summarization
- t5
widget:
- text: "The people of the State of California do enact as
follows: SECTION 1. The Legislature hereby finds
and declares as follows: (a) Many areas of the
state are disproportionately impacted by drought
because they are heavily dependent or completely
reliant on groundwater from basins that are in
overdraft and in which the water table declines
year after year or from basins that are
contaminated. (b) There are a number of state
grant and loan programs that provide financial
assistance to communities to address drinking
water and wastewater needs. Unfortunately, there
is no program in place to provide similar
assistance to individual homeowners who are
reliant on their own groundwater wells and who may
not be able to afford conventional private loans
to undertake vital water supply, water quality,
and wastewater improvements. (c) The program
created by this act is intended to bridge that gap
by providing low-interest loans, grants, or both,
to individual homeowners to undertake actions
necessary to provide safer, cleaner, and more
reliable drinking water and wastewater treatment.
These actions may include, but are not limited to,
digging deeper wells, improving existing wells and
related equipment, addressing drinking water
contaminants in the homeowner’s water, or
connecting to a local water or wastewater system. SEC. 2. Chapter 6.6 (commencing with Section
13486) is added to Division 7 of the Water Code,
to read: CHAPTER  6.6. Water and Wastewater Loan
and Grant Program 13486. (a) The board shall
establish a program in accordance with this
chapter to provide low-interest loans and grants
to local agencies for low-interest loans and
grants to eligible applicants for any of the
following purposes:"
  example_title: "Water use"
- text: "The people of the State of California do enact as
follows:   SECTION 1. Section 2196 of the
Elections Code is amended to read: 2196. (a) (1)
Notwithstanding any other provision of law, a
person who is qualified to register to vote and
who has a valid California driver’s license or
state identification card may submit an affidavit
of voter registration electronically on the
Internet Web site of the Secretary of State. (2)
An affidavit submitted pursuant to this section is
effective upon receipt of the affidavit by the
Secretary of State if the affidavit is received on
or before the last day to register for an election
to be held in the precinct of the person
submitting the affidavit. (3) The affiant shall
affirmatively attest to the truth of the
information provided in the affidavit. (4) For
voter registration purposes, the applicant shall
affirmatively assent to the use of his or her
signature from his or her driver’s license or
state identification card. (5) For each electronic
affidavit, the Secretary of State shall obtain an
electronic copy of the applicant’s signature from
his or her driver’s license or state
identification card directly from the Department
of Motor Vehicles. (6) The Secretary of State
shall require a person who submits an affidavit
pursuant to this section to submit all of the
following: (A) The number from his or her
California driver’s license or state
identification card. (B) His or her date of birth.
(C) The last four digits of his or her social
security number. (D) Any other information the
Secretary of State deems necessary to establish
the identity of the affiant. (7) Upon submission
of an affidavit pursuant to this section, the
electronic voter registration system shall provide
for immediate verification of both of the
following:"
  example_title: "Election"
metrics:
- rouge
model-index:
- name: t5-small-finetuned-billsum-ca_test
  results:
  - task:
      name: Sequence-to-sequence Language Modeling
      type: text2text-generation
    dataset:
      name: billsum
      type: billsum
      args: default
    metrics:
    - name: Rouge1
      type: rouge
      value: 12.6315
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# t5-small-finetuned-billsum-ca_test

This model is a fine-tuned version of [t5-small](https://huggingface.co/t5-small) on the billsum dataset.
It achieves the following results on the evaluation set:
- Loss: 2.3376
- Rouge1: 12.6315
- Rouge2: 6.9839
- Rougel: 10.9983
- Rougelsum: 11.9383
- Gen Len: 19.0

## Model description

More information needed

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 2
- eval_batch_size: 2
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 4
- mixed_precision_training: Native AMP

### Training results

| Training Loss | Epoch | Step | Validation Loss | Rouge1  | Rouge2 | Rougel  | Rougelsum | Gen Len |
|:-------------:|:-----:|:----:|:---------------:|:-------:|:------:|:-------:|:---------:|:-------:|
| No log        | 1.0   | 495  | 2.4805          | 9.9389  | 4.1239 | 8.3979  | 9.1599    | 19.0    |
| 3.1564        | 2.0   | 990  | 2.3833          | 12.1026 | 6.5196 | 10.5123 | 11.4527   | 19.0    |
| 2.66          | 3.0   | 1485 | 2.3496          | 12.5389 | 6.8686 | 10.8798 | 11.8636   | 19.0    |
| 2.5671        | 4.0   | 1980 | 2.3376          | 12.6315 | 6.9839 | 10.9983 | 11.9383   | 19.0    |


### Framework versions

- Transformers 4.12.2
- Pytorch 1.9.0+cu111
- Datasets 1.14.0
- Tokenizers 0.10.3
