---
tags:
- generated_from_trainer
metrics:
- accuracy
- f1
model-index:
- name: sbert_large-finetuned-sent_in_news_sents
  results: []
---

<!-- This model card has been generated automatically according to the information the Trainer had access to. You
should probably proofread and complete it, then remove this comment. -->

# sbert_large-finetuned-sent_in_news_sents

This model is a fine-tuned version of [sberbank-ai/sbert_large_nlu_ru](https://huggingface.co/sberbank-ai/sbert_large_nlu_ru) on an unknown dataset.
It achieves the following results on the evaluation set:
- Loss: 1.7056
- Accuracy: 0.7301
- F1: 0.5210

## Model examples
Model responds to label X in news text. For exaple:

For 'Газпром отозвал лицензию у X, сообщает Финам' the model will return negative label -3

For 'X отозвал лицензию у Сбербанка, сообщает Финам' the model will return neutral label 0

For 'Газпром отозвал лицензию у Сбербанка, сообщает X' the model will return neutral label 0

For 'X демонстрирует высокую прибыль, сообщает Финам' the model will return positive label 1


##  Simple example of News preprocessing for Russian before BERT
```
from natasha import (
    Segmenter,
    MorphVocab,
    NewsEmbedding,
    NewsMorphTagger,
    NewsSyntaxParser,
    NewsNERTagger,
    PER,
    NamesExtractor,
    Doc
)
segmenter = Segmenter()
emb = NewsEmbedding()
morph_tagger = NewsMorphTagger(emb)
syntax_parser = NewsSyntaxParser(emb)
morph_vocab = MorphVocab()


### ----------------------------- key sentences block -----------------------------

def find_synax_tokens_with_order(doc, start, tokens, text_arr, full_str):
    ''' Находит все синтаксические токены, соответствующие заданному набору простых токенов (найденные
        для определенной NER другими функциями).
        Возвращает словарь найденных синтаксических токенов (ключ - идентификатор токена, состоящий
        из номера предложения и номера токена внутри предложения).
        Начинает поиск с указанной позиции в списке синтаксических токенов, дополнительно возвращает
        позицию остановки, с которой нужно продолжить поиск следующей NER.
    '''
    found = []
    in_str = False
    str_candidate = ''
    str_counter = 0
    if len(text_arr) == 0:
        return [], start
    for i in range(start, len(doc.syntax.tokens)):
        t = doc.syntax.tokens[i]
        if in_str:
            str_counter += 1
            if str_counter < len(text_arr) and t.text == text_arr[str_counter]:
                str_candidate += t.text
                found.append(t)
                if str_candidate == full_str:
                    return found, i+1
            else:
                in_str = False
                str_candidate = ''
                str_counter = 0
                found = []
        if t.text == text_arr[0]:
            found.append(t)
            str_candidate = t.text
            if str_candidate == full_str:
                return found, i+1
            in_str = True
    return [], len(doc.syntax.tokens)


def find_tokens_in_diap_with_order(doc, start_token, diap):
    ''' Находит все простые токены (без синтаксической информации), которые попадают в
        указанный диапазон. Эти диапазоны мы получаем из разметки NER.
        Возвращает набор найденных токенов и в виде массива токенов, и в виде массива строчек.
        Начинает поиск с указанной позиции в строке и дополнительно возвращает позицию остановки.
    '''
    found_tokens = []
    found_text = []
    full_str = ''
    next_i = 0
    for i in range(start_token, len(doc.tokens)):
        t = doc.tokens[i]
        if t.start > diap[-1]:
            next_i = i
            break
        if t.start in diap:
            found_tokens.append(t)
            found_text.append(t.text)
            full_str += t.text
    return found_tokens, found_text, full_str, next_i


def add_found_arr_to_dict(found, dict_dest):
    for synt in found:
        dict_dest.update({synt.id: synt})
    return dict_dest


def make_all_syntax_dict(doc):
    all_syntax = {}
    for synt in doc.syntax.tokens:
        all_syntax.update({synt.id: synt})
    return all_syntax


def is_consiquent(id_1, id_2):
    ''' Проверяет идут ли токены друг за другом без промежутка по ключам. '''
    id_1_list = id_1.split('_')
    id_2_list = id_2.split('_')
    if id_1_list[0] != id_2_list[0]:
        return False
    return int(id_1_list[1]) + 1 == int(id_2_list[1])


def replace_found_to(found, x_str):
    ''' Заменяет последовательность токенов NER на «заглушку». '''
    prev_id = '0_0'
    for synt in found:
        if is_consiquent(prev_id, synt.id):
            synt.text = ''
        else:
            synt.text = x_str
        prev_id = synt.id


def analyze_doc(text):
    ''' Запускает Natasha для анализа документа. '''
    doc = Doc(text)
    doc.segment(segmenter)
    doc.tag_morph(morph_tagger)
    doc.parse_syntax(syntax_parser)
    ner_tagger = NewsNERTagger(emb)
    doc.tag_ner(ner_tagger)
    return doc


def find_non_sym_syntax_short(entity_name, doc, add_X=False, x_str='X'):
    ''' Отыскивает заданную сущность в тексте, среди всех NER (возможно, в другой грамматической форме).

        entity_name - сущность, которую ищем;
        doc - документ, в котором сделан препроцессинг Natasha;
        add_X - сделать ли замену сущности на «заглушку»;
        x_str - текст замены.

        Возвращает:
        all_found_syntax - словарь всех подходящих токенов образующих искомые сущности, в котором
        в случае надобности произведена замена NER на «заглушку»;
        all_syntax - словарь всех токенов.
    '''
    all_found_syntax = {}
    current_synt_number = 0
    current_tok_number = 0

    # идем по всем найденным NER
    for span in doc.spans:
        span.normalize(morph_vocab)
        if span.type != 'ORG':
            continue
        diap = range(span.start, span.stop)
        # создаем словарь всех синтаксических элементов (ключ -- id из номера предложения и номера внутри предложения)
        all_syntax = make_all_syntax_dict(doc)
        # находим все простые токены внутри NER
        found_tokens, found_text, full_str, current_tok_number = find_tokens_in_diap_with_order(doc, current_tok_number,
                                                                                                diap)
        # по найденным простым токенам находим все синтаксические токены внутри данного NER
        found, current_synt_number = find_synax_tokens_with_order(doc, current_synt_number, found_tokens, found_text,
                                                                  full_str)
        # если текст NER совпадает с указанной сущностью, то делаем замену
        if entity_name.find(span.normal) >= 0 or span.normal.find(entity_name) >= 0:
            if add_X:
                replace_found_to(found, x_str)
            all_found_syntax = add_found_arr_to_dict(found, all_found_syntax)
    return all_found_syntax, all_syntax


def key_sentences(all_found_syntax):
    ''' Находит номера предложений с искомой NER. '''
    key_sent_numb = {}
    for synt in all_found_syntax.keys():
        key_sent_numb.update({synt.split('_')[0]: 1})
    return key_sent_numb


def openinig_punct(x):
    opennings = ['«', '(']
    return x in opennings


def key_sentences_str(entitiy_name, doc, add_X=False, x_str='X', return_all=True):
    ''' Составляет окончательный текст, в котором есть только предложения, где есть ключевая сущность,
        эта сущность, если указано, заменяется на «заглушку».
    '''
    all_found_syntax, all_syntax = find_non_sym_syntax_short(entitiy_name, doc, add_X, x_str)
    key_sent_numb = key_sentences(all_found_syntax)
    str_ret = ''

    for s in all_syntax.keys():
        if (s.split('_')[0] in key_sent_numb.keys()) or (return_all):
            to_add = all_syntax[s]

            if s in all_found_syntax.keys():
                to_add = all_found_syntax[s]
            else:
                if to_add.rel == 'punct' and not openinig_punct(to_add.text):
                    str_ret = str_ret.rstrip()

            str_ret += to_add.text
            if (not openinig_punct(to_add.text)) and (to_add.text != ''):
                str_ret += ' '

    return str_ret


### ----------------------------- key entities block -----------------------------


def find_synt(doc, synt_id):
    for synt in doc.syntax.tokens:
        if synt.id == synt_id:
            return synt
    return None


def is_subj(doc, synt, recursion_list=[]):
    ''' Сообщает является ли слово подлежащим или частью сложного подлежащего. '''
    if synt.rel == 'nsubj':
        return True
    if synt.rel == 'appos':
        found_head = find_synt(doc, synt.head_id)
        if found_head.id in recursion_list:
            return False
        return is_subj(doc, found_head, recursion_list + [synt.id])
    return False


def find_subjects_in_syntax(doc):
    ''' Выдает словарик, в котором для каждой NER написано, является ли он
        подлежащим в предложении.
        Выдает стартовую позицию NER и было ли оно подлежащим (или appos)
    '''
    found_subjects = {}
    current_synt_number = 0
    current_tok_number = 0

    for span in doc.spans:
        span.normalize(morph_vocab)
        if span.type != 'ORG':
            continue

        found_subjects.update({span.start: 0})
        diap = range(span.start, span.stop)

        found_tokens, found_text, full_str, current_tok_number = find_tokens_in_diap_with_order(doc,
                                                                                                current_tok_number,
                                                                                                diap)

        found, current_synt_number = find_synax_tokens_with_order(doc, current_synt_number, found_tokens,
                                                                  found_text, full_str)

        found_subjects.update({span.start: 0})
        for synt in found:
            if is_subj(doc, synt):
                found_subjects.update({span.start: 1})
    return found_subjects


def entity_weight(lst, c=1):
    return c*lst[0]+lst[1]


def determine_subject(found_subjects, doc, new_agency_list, return_best=True, threshold=0.75):
    ''' Определяет ключевую NER и список самых важных NER, основываясь на том, сколько
        раз каждая из них встречается в текста вообще и сколько раз в роли подлежащего '''
    objects_arr = []
    objects_arr_ners = []
    should_continue = False
    for span in doc.spans:
        should_continue = False
        span.normalize(morph_vocab)
        if span.type != 'ORG':
            continue
        if span.normal in new_agency_list:
            continue
        for i in range(len(objects_arr)):
            t, lst = objects_arr[i]

            if t.find(span.normal) >= 0:
                lst[0] += 1
                lst[1] += found_subjects[span.start]
                should_continue = True
                break

            if span.normal.find(t) >= 0:
                objects_arr[i] = (span.normal, [lst[0]+1, lst[1]+found_subjects[span.start]])
                should_continue = True
                break

        if should_continue:
            continue
        objects_arr.append((span.normal, [1, found_subjects[span.start]]))
        objects_arr_ners.append(span.normal)

    max_weight = 0
    opt_ent = 0
    for obj in objects_arr:
        t, lst = obj
        w = entity_weight(lst)
        if max_weight < w:
            max_weight = w
            opt_ent = t

    if not return_best:
        return opt_ent, objects_arr_ners

    bests = []
    for obj in objects_arr:
        t, lst = obj
        w = entity_weight(lst)
        if max_weight*threshold < w:
            bests.append(t)

    return opt_ent, bests


text = '''В офисах Сбера начали тестировать технологию помощи посетителям в экстренных ситуациях. «Зеленая кнопка» будет
 в зонах круглосуточного обслуживания офисов банка в Воронеже, Санкт-Петербурге, Подольске, Пскове, Орле и Ярославле.
 В них находятся стенды с сенсорными кнопками, обеспечивающие связь с операторами центра мониторинга службы безопасности
 банка. Получив сигнал о помощи, оператор центра может подключиться к объекту по голосовой связи. С помощью камер
 видеонаблюдения он оценит обстановку и при необходимости вызовет полицию или скорую помощь. «Зеленой кнопкой» можно
 воспользоваться в нерабочее для отделения время, если возникла угроза жизни или здоровью. В остальных случаях помочь
 клиентам готовы сотрудники отделения банка. «Одно из направлений нашей работы в области ESG и устойчивого развития
 — это забота об обществе. И здоровье людей как высшая ценность является его основой. Поэтому задача банка в области
 безопасности гораздо масштабнее, чем обеспечение только финансовой безопасности клиентов. Этот пилотный проект
 приурочен к 180-летию Сбербанка: мы хотим, чтобы, приходя в банк, клиент чувствовал, что его жизнь и безопасность
 — наша ценность», — отметил заместитель председателя правления Сбербанка Станислав Кузнецов.'''

doc = analyze_doc(text)
key_entity = determine_subject(find_subjects_in_syntax(doc), doc, [])[0]
text_for_model = key_sentences_str(key_entity, doc, add_X=True, x_str='X', return_all=False)
```

## Intended uses & limitations

More information needed

## Training and evaluation data

More information needed

## Training procedure

### Training hyperparameters

The following hyperparameters were used during training:
- learning_rate: 2e-05
- train_batch_size: 6
- eval_batch_size: 6
- seed: 42
- optimizer: Adam with betas=(0.9,0.999) and epsilon=1e-08
- lr_scheduler_type: linear
- num_epochs: 20

### Training results

| Training Loss | Epoch | Step | Validation Loss | Accuracy | F1     |
|:-------------:|:-----:|:----:|:---------------:|:--------:|:------:|
| No log        | 1.0   | 176  | 0.9504          | 0.6903   | 0.2215 |
| No log        | 2.0   | 352  | 0.9065          | 0.7159   | 0.4760 |
| 0.8448        | 3.0   | 528  | 0.9687          | 0.7045   | 0.4774 |
| 0.8448        | 4.0   | 704  | 1.2436          | 0.7045   | 0.4686 |
| 0.8448        | 5.0   | 880  | 1.4809          | 0.7273   | 0.4630 |
| 0.2074        | 6.0   | 1056 | 1.5866          | 0.7330   | 0.5185 |
| 0.2074        | 7.0   | 1232 | 1.7056          | 0.7301   | 0.5210 |
| 0.2074        | 8.0   | 1408 | 1.6982          | 0.7415   | 0.5056 |
| 0.0514        | 9.0   | 1584 | 1.8088          | 0.7273   | 0.5203 |
| 0.0514        | 10.0  | 1760 | 1.9250          | 0.7102   | 0.4879 |


### Framework versions

- Transformers 4.11.2
- Pytorch 1.9.0+cu102
- Datasets 1.12.1
- Tokenizers 0.10.3
