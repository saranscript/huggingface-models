---
language: en
datasets: COCA
---
# docusco-bert

## Model description

**docusco-bert** is a fine-tuned BERT model that is ready to use for **token classification**. The model was trained on data from the Corpus of Contemporary American English ([COCA](https://www.english-corpora.org/coca/)) and classifies tokens and token sequences according to a system developed for the [**DocuScope**](https://www.cmu.edu/dietrich/english/research-and-publications/docuscope.html) dictionary-based tagger. Descriptions of the categories are included in a table below. 

## About DocuScope
DocuScope is a dicitonary-based tagger that has been developed at Carnegie Mellon University by **David Kaufer** and **Suguru Ishizaki** since the early 2000s. Its categories are rhetorical in their orientation (as opposed to part-of-speech tags, for example, which are morphosyntactic).

DocuScope has been been used in [a wide variety of studies](https://scholar.google.com/scholar?hl=en&as_sdt=0%2C5&q=docuscope&btnG=). Here, for example, is [a short analysis of King Lear](https://graphics.cs.wisc.edu/WP/vep/2017/02/14/guest-post-data-mining-king-lear/), and here is [a published study of Tweets](https://journals.sagepub.com/doi/full/10.1177/2055207619844865).

## Intended uses & limitations

#### How to use

The model was trained on data with tags formatted using [IOB](https://en.wikipedia.org/wiki/Inside%E2%80%93outside%E2%80%93beginning_(tagging)), like those used in common tasks like Named Entity Recogition (NER). Thus, you can use this model with a Transformers NER *pipeline*.

```python
from transformers import AutoTokenizer, AutoModelForTokenClassification
from transformers import pipeline

tokenizer = AutoTokenizer.from_pretrained("browndw/docusco-bert")
model = AutoModelForTokenClassification.from_pretrained("browndw/docusco-bert")

nlp = pipeline("ner", model=model, tokenizer=tokenizer)
example = "Globalization is the process of interaction and integration among people, companies, and governments worldwide."

ds_results = nlp(example)
print(ds_results)
```

#### Limitations and bias

This model is limited by its training dataset of American English texts. Moreover, the current version is trained on only a small subset of the corpus. The goal is to train later versions on more data, which should increase accuracy. 

## Training data

This model was fine-tuned on data from the Corpus of Contemporary American English ([COCA](https://www.english-corpora.org/coca/)). The training data contain 1500 randomly sampled texts from each of 5 text-types: Academic, Fiction, Magazine, News, and Spoken.

#### # of texts/chunks/tokens per dataset
Dataset |Texts |Chunks |Tokens
-|-|-|-
Train |7500 |1,167,584 |32,203,828
Test |500 |58,117 |1,567,997

## Training procedure

This model was trained on a single 2.3 GHz Dual-Core Intel Core i5 with recommended hyperparameters from the [original BERT paper](https://arxiv.org/pdf/1810.04805). 

## Eval results
### Overall
metric|test
-|-
f1 |.743
accuracy |.801

### By category
category|precision|recall|f1-score|support
-|-|-|-|-
AcademicTerms|0.76|0.77|0.76|140805
AcademicWritingMoves|0.36|0.46|0.40|8182
Character|0.74|0.78|0.76|123856
Citation|0.73|0.81|0.77|13428
CitationAuthority|0.55|0.49|0.51|4552
CitationHedged|0.58|0.89|0.70|285
ConfidenceHedged|0.76|0.84|0.79|14765
ConfidenceHigh|0.64|0.72|0.68|11462
ConfidenceLow|0.70|0.39|0.50|380
Contingent|0.68|0.69|0.69|9537
Description|0.60|0.67|0.63|108186
Facilitate|0.63|0.63|0.63|7421
FirstPerson|0.62|0.73|0.67|6235
ForceStressed|0.65|0.72|0.69|37910
Future|0.63|0.69|0.66|9049
InformationChange|0.64|0.72|0.68|14560
InformationChangeNegative|0.59|0.57|0.58|1840
InformationChangePositive|0.61|0.58|0.60|4265
InformationExposition|0.80|0.83|0.82|84977
InformationPlace|0.80|0.82|0.81|18783
InformationReportVerbs|0.71|0.79|0.75|17572
InformationStates|0.74|0.80|0.77|21048
InformationTopics|0.69|0.72|0.70|58677
Inquiry|0.50|0.58|0.53|12735
Interactive|0.64|0.70|0.67|18135
MetadiscourseCohesive|0.90|0.93|0.92|33312
MetadiscourseInteractive|0.54|0.62|0.58|6888
Narrative|0.70|0.76|0.73|116896
Negative|0.63|0.69|0.66|60534
Positive|0.60|0.67|0.63|54374
PublicTerms|0.70|0.74|0.72|38229
Reasoning|0.71|0.76|0.74|30157
Responsibility|0.59|0.63|0.61|3451
Strategic|0.60|0.62|0.61|28064
SyntacticComplexity|0.83|0.87|0.85|297387
Uncertainty|0.43|0.44|0.43|2915
Updates|0.52|0.53|0.53|6156
-|-|-|-|-
micro|avg|0.72|0.77|0.74|1427008
macro|avg|0.65|0.69|0.67|1427008
weighted|avg|0.72|0.77|0.74|1427008


## DocuScope Category Descriptions

Category (Cluster)|Description|Examples
-|-|-
Academic Terms|Abstract, rare, specialized, or disciplinary-specific terms that are indicative of informationally dense writing|*market price*, *storage capacity*, *regulatory*, *distribution*
Academic Writing Moves|Phrases and terms that indicate academic writing moves, which are common in research genres and are derived from the work of Swales (1981) and Cotos et al. (2015, 2017)|*in the first section*, *the problem is that*, *payment methodology*, *point of contention*
Character|References multiple dimensions of a character or human being as a social agent, both individual and collective|*Pauline*, *her*, *personnel*, *representatives*
Citation|Language that indicates the attribution of information to, or citation of, another source.|*according to*, *is proposing that*, *quotes from*
Citation Authorized|Referencing the citation of another source that is represented as true and not arguable|*confirm that*, *provide evidence*, *common sense*
Citation Hedged|Referencing the citation of another source that is presented as arguable|*suggest that*, *just one opinion*
Confidence Hedged|Referencing language that presents a claim as uncertain|*tends to get*, *maybe*, *it seems that*
Confidence High|Referencing language that presents a claim with certainty|*most likely*, *ensure that*, *know that*, *obviously*
Confidence Low|Referencing language that presents a claim as extremely unlikely|*unlikely*, *out of the question*, *impossible*
Contingent|Referencing contingency, typically contingency in the world, rather than contingency in one's knowledge|*subject to*, *if possible*, *just in case*, *hypothetically*
Description|Language that evokes sights, sounds, smells, touches and tastes, as well as scenes and objects|*stay quiet*, *gas-fired*, *solar panels*, *soft*, *on my desk*
Facilitate|Language that enables or directs one through specific tasks and actions|*let me*, *worth a try*, *I would suggest*
First Person|This cluster captures first person.|*I*, *as soon as I*, *we have been*
Force Stressed|Language that is forceful and stressed, often using emphatics, comparative forms, or superlative forms|*really good*, *the sooner the better*, *necessary*
Future|Referencing future actions, states, or desires|*will be*, *hope to*, *expected changes*
Information Change|Referencing changes of information, particularly changes that are more neutral|*changes*, *revised*, *growth*, *modification to*
Information Change Negative|Referencing negative change|*going downhill*, *slow erosion*, *get worse*
Information Change Positive|Referencing positive change|*improving*, *accrued interest*, *boost morale*
Information Exposition|Information in the form of expository devices, or language that describes or explains, frequently in regards to quantities and comparisons|*final amount*, *several*, *three*, *compare*, *80%*
Information Place|Language designating places|*the city*, *surrounding areas*, *Houston*, *home*
Information Report Verbs|Informational verbs and verb phrases of reporting|*report*, *posted*, *release*, *point out*
Information States|Referencing information states, or states of being|*is*, *are*, *existing*, *been*
Information Topics|Referencing topics, usually nominal subjects or objects, that indicate the “aboutness” of a text|*time*, *money*, *stock price*, *phone interview*
Inquiry|Referencing inquiry, or language that points to some kind of inquiry or investigation|*find out*, *let me know if you have any questions*, *wondering if*
Interactive|Addresses from the author to the reader or from persons in the text to other persons. The address comes in the language of everyday conversation, colloquy, exchange, questions, attention-getters, feedback, interactive genre markers, and the use of the second person.|*can you*, *thank you for*, *please see*, *sounds good to me*
Metadiscourse Cohesive|The use of words to build cohesive markers that help the reader navigate the text and signal linkages in the text, which are often additive or contrastive|*or*, *but*, *also*, *on the other hand*, *notwithstanding*, *that being said*
Metadiscourse Interactive|The use of words to build cohesive markers that interact with the reader|*I agree*, *let’s talk*, *by the way*
Narrative|Language that involves people, description, and events extending in time|*today*, *tomorrow*, *during the*, *this weekend*
Negative|Referencing dimensions of negativity, including negative acts, emotions, relations, and values|*does not*, *sorry for*, *problems*, *confusion*
Positive|Referencing dimensions of positivity, including actions, emotions, relations, and values|*thanks*, *approval*, *agreement*, *looks good*
Public Terms|Referencing public terms, concepts from public language, media, the language of authority, institutions, and responsibility|*discussion*, *amendment*, *corporation*, *authority*, *settlement*
Reasoning|Language that has a reasoning focus, supporting inferences about cause, consequence, generalization, concession, and linear inference either from premise to conclusion or conclusion to premise|*because*, *therefore*, *analysis*, *even if*, *as a result*, *indicating that*
Responsibility|Referencing the language of responsibility|*supposed to*, *requirements*, *obligations*
Strategic|This dimension is active when the text structures strategies activism, advantage-seeking, game-playing cognition, plans, and goal-seeking.|*plan*, *trying to*, *strategy*, *decision*, *coordinate*, *look at the*
Syntactic Complexity|The features in this category are often what are called “function words,” like determiners and prepositions.|*the*, *to*, *for*, *in*, *a lot of*
Uncertainty|References uncertainty, when confidence levels are unknown|*kind of*, *I have no idea*, *for some reason*
Updates|References updates that anticipate someone searching for information and receiving it|*already*, *a new*, *now that*, *here are some*



### BibTeX entry and citation info
```
@incollection{ishizaki2012computer,
  title    = {Computer-aided rhetorical analysis},
  author   = {Ishizaki, Suguru and Kaufer, David},
  booktitle= {Applied natural language processing: Identification, investigation and resolution},
  pages    = {276--296},
  year     = {2012},
  publisher= {IGI Global},
  url      = {https://www.igi-global.com/chapter/content/61054}
}
```
```
@article{DBLP:journals/corr/abs-1810-04805,
  author    = {Jacob Devlin and
               Ming{-}Wei Chang and
               Kenton Lee and
               Kristina Toutanova},
  title     = {{BERT:} Pre-training of Deep Bidirectional Transformers for Language
               Understanding},
  journal   = {CoRR},
  volume    = {abs/1810.04805},
  year      = {2018},
  url       = {http://arxiv.org/abs/1810.04805},
  archivePrefix = {arXiv},
  eprint    = {1810.04805},
  timestamp = {Tue, 30 Oct 2018 20:39:56 +0100},
  biburl    = {https://dblp.org/rec/journals/corr/abs-1810-04805.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

