---
language:
- zh
tags:
- generation
- poetry
widget:
- text: "疆场-思乡-归家-耕织《丘处机》"

---

# 终于落不了油腻俗套， 来弄这劳什子的藏头诗模型
> This is a model to generated Chinese poetry with leading characters and certain tune of mood.

## 本模型为了达到两个目的 Objectives
* 创作藏头诗 🎸
* 创作时尽量融入关键词的意境🪁 🌼 ❄️ 🌝

## 运作原理 How
这个模型充分利用了[gpt2论文](https://d4mucfpksywv.cloudfront.net/better-language-models/language_models_are_unsupervised_multitask_learners.pdf)的精髓， 论文标题为**《语言模型即学万事万物》**， 也就是许许多多的学习任务， 可以安排成文本序列的形式，来管理输入输出， 即模型如能根据 **「所有自然常数的导数是0， 0的cos是1 ，」**算出后面的句子应该是**「 四个1相加的阶乘是4， 4的阶乘是24」**也就学会了二十四点。 模型在训练上只做了猜测语言序列的任务， 但会兼通万物。

这个码诗模型就是这么来的， 训练任务， 是输入0~10来个关键词+藏头标题+藏头字数+把头换成分类符```[CLS]```之后的诗句。
```
'忍看-窈窕-孤寝-勾带-嫩-黄昏《粉度》『二』[CLS]堞云齐，[CLS]清笳、愁入暮烟林杪。素艳透春，玉骨凄凉，勾带月痕生早。江天苍莽黄昏後，依然是、粉寒香瘦。动追感、西园嫩约，夜深人悄。记得东风窈窕。曾夜踏横斜，醉携娇小。惆怅旧欢，回首俱非，忍看绿笺红豆。香销纸帐人孤寝，相思恨、花还知否。梦回处，霜飞翠楼已晓。'
```

## Inference 通道矫情了一点， 大家照抄就是了
### 不然藏头就不见了

```python

tokenizer  = AutoTokenizer.from_pretrained('raynardj/keywords-cangtou-chinese-poetry')
model  = AutoModel.from_pretrained('raynardj/keywords-cangtou-chinese-poetry')

def inference(lead, keywords = []):
    """
    lead: 藏头的语句， 比如一个人的名字， 2，3 或4个字
    keywords：关键词, 0~12个关键词比较好
    """
    leading = f"《{lead}》"
    text = "-".join(keywords)+leading
    input_ids = tokenizer(text, return_tensors='pt', ).input_ids[:,:-1]
    lead_tok = tokenizer(lead, return_tensors='pt',  ).input_ids[0,1:-1]

    with torch.no_grad():
        pred = model.generate(
            input_ids,
            max_length=256,
            num_beams=5,
            do_sample=True,
            repetition_penalty=2.1,
            top_p=.6,
            bos_token_id=tokenizer.sep_token_id,
            pad_token_id=tokenizer.pad_token_id,
            eos_token_id=tokenizer.sep_token_id,
        )[0,1:]
    
    # 我们需要将[CLS] 字符， 也就是101, 逐个换回藏头的字符
    mask = (pred==101)
    while mask.sum()<len(lead_tok):
        lead_tok = lead_tok[:mask.sum()]
    while mask.sum()>len(lead_tok):
        reversed_lead_tok = lead_tok.flip(0)
        lead_tok = torch.cat([
            lead_tok, reversed_lead_tok[:mask.sum()-len(lead_tok)]])
    pred[mask] = lead_tok
    # 从 token 编号解码成语句
    generate = tokenizer.decode(pred, skip_special_tokens=True)
    # 清理语句
    generate = generate.replace("》","》\n").replace("。","。\n").replace(" ","")
    return generate
```

## Cherry picking
大家下了模型,可以自己玩耍。
却也可以尝尝我替大家摘的樱桃🍒
```python
>>> inference("上海",["高楼","虹光","灯红酒绿","华厦"])
高楼-虹光-灯红酒绿-华厦《上海》
『二』
上台星月明如昼。
海阁珠帘卷画堂。

>>> inference("刘先生",["妆容","思","落花","空镜"])
妆容-思-落花-空镜《刘先生》
『三』
刘郎何事不相逢，先把金尊酒未空。
生意自知人薄命，多情只有月明中。
```

## 其他文言诗词的资源
* [项目源代码 🌟, 欢迎+star提pr](https://github.com/raynardj/yuan)
* [跨语种搜索 🔎](https://huggingface.co/raynardj/xlsearch-cross-lang-search-zh-vs-classicical-cn)
* [现代文翻译古汉语的模型 ⛰](https://huggingface.co/raynardj/wenyanwen-chinese-translate-to-ancient)
* [古汉语到现代文的翻译模型, 输入可以是未断句的句子 🚀](https://huggingface.co/raynardj/wenyanwen-ancient-translate-to-modern)
* [断句模型 🗡](https://huggingface.co/raynardj/classical-chinese-punctuation-guwen-biaodian)
* [意境关键词 和 藏头写诗🤖](https://huggingface.co/raynardj/keywords-cangtou-chinese-poetry)