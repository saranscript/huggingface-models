# Targeted Sentiment Analysis in News Headlines

BERT classifier fine-tuned in a news headlines dataset annotated for target polarity.

(details to be published)


## Examples

Input is as follows

`Headline [SEP] Target`

where headline is the news title and target is an entity present in the headline.

Try

`Alberto Fernández: "El gobierno de Macri fue un desastre" [SEP] Macri` (should be NEG)

and

`Alberto Fernández: "El gobierno de Macri fue un desastre" [SEP] Alberto Fernández` (POS or NEU)
