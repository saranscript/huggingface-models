---
language:
- en
- he

tags:
- translation

license: apache-2.0
---

### en-he

* source group: English 
* target group: Hebrew 
*  OPUS readme: [eng-heb](https://github.com/Helsinki-NLP/Tatoeba-Challenge/tree/master/models/eng-heb/README.md)

*  model: transformer
* source language(s): eng
* target language(s): heb
* model: transformer
* pre-processing: normalization + SentencePiece (spm32k,spm32k)
* download original weights: [opus-2020-10-04.zip](https://object.pouta.csc.fi/Tatoeba-MT-models/eng-heb/opus-2020-10-04.zip)
* test set translations: [opus-2020-10-04.test.txt](https://object.pouta.csc.fi/Tatoeba-MT-models/eng-heb/opus-2020-10-04.test.txt)
* test set scores: [opus-2020-10-04.eval.txt](https://object.pouta.csc.fi/Tatoeba-MT-models/eng-heb/opus-2020-10-04.eval.txt)

## Benchmarks

| testset               | BLEU  | chr-F |
|-----------------------|-------|-------|
| Tatoeba-test.eng.heb 	| 37.9 	| 0.602 |


### System Info: 
- hf_name: en-he

- source_languages: eng

- target_languages: heb

- opus_readme_url: https://github.com/Helsinki-NLP/Tatoeba-Challenge/tree/master/models/eng-heb/README.md

- original_repo: Tatoeba-Challenge

- tags: ['translation']

- languages: ['en', 'he']

- src_constituents: ('English', {'eng'})

- tgt_constituents: ('Hebrew', {'heb'})

- src_multilingual: False

- tgt_multilingual: False

- long_pair: eng-heb

- prepro:  normalization + SentencePiece (spm32k,spm32k)

- url_model: https://object.pouta.csc.fi/Tatoeba-MT-models/eng-heb/opus-2020-10-04.zip

- url_test_set: https://object.pouta.csc.fi/Tatoeba-MT-models/eng-heb/opus-2020-10-04.test.txt

- src_alpha3: eng

- tgt_alpha3: heb

- chrF2_score: 0.602

- bleu: 37.9

- brevity_penalty: 1.0

- ref_len: 60359.0

- src_name: English

- tgt_name: Hebrew

- train_date: 2020-10-04 00:00:00

- src_alpha2: en

- tgt_alpha2: he

- prefer_old: False

- short_pair: en-he

- helsinki_git_sha: 61fd6908b37d9a7b21cc3e27c1ae1fccedc97561

- transformers_git_sha: d99ed7ad618037ae878f0758157ed0764bd7f935

- port_machine: LM0-400-22516.local

- port_time: 2020-10-15-16:31