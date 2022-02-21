---
license: agpl-3.0
language: 
- is
---
# FastText model trained on Icelandic

This model is trained on the lemmas of the Icelandic Gigaword Corpus version 20.05. It is trained using the gensim package, version 4.1.0. and parameters were set to default (100 dimensions, windows size 5)

This model can not be loaded directly since it uses gensim, clone the repository and run the following to use it.

```python
import gensim
model = gensim.models.FastText.load("./rmh.w2v.model")
```

## Example output

```bash
In [1]: model.wv.most_similar("england")
Out[1]: 
[('englands', 0.8778558969497681),
 ('southland', 0.8573296070098877),
 ('skotland', 0.846065878868103),
 ('englaland', 0.8320872187614441),
 ('hoogland', 0.8299505114555359),
 ('hoagland', 0.8277317881584167),
 ('totland', 0.8265103697776794),
 ('lackland', 0.8234561681747437),
 ('skarpengland', 0.8227219581604004),
 ('langland', 0.8222305774688721)]

In [2]: model.wv.most_similar("kanína")
Out[2]: 
[('loðkanína', 0.9271067976951599),
 ('dvergkanína', 0.9106121063232422),
 ('angórakanína', 0.895512044429779),
 ('angórukanína', 0.8741581439971924),
 ('feldkanína', 0.8696010708808899),
 ('kanínubangsi', 0.8562541604042053),
 ('holdakanína', 0.8543838858604431),
 ('villikanína', 0.8525990843772888),
 ('silkikanína', 0.8515204191207886),
 ('kaníni', 0.8445548415184021)]
```


