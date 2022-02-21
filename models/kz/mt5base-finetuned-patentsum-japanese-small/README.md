---
language: "ja"
widget:
- text: "請求項 <extra_id_0>"
license: "mit"
---

Google's mt5-base fine-tuned in Japanese to summarize patent claims in a limited Pharmaceutical domain.

#日本語特許請求項要約（医薬特定ドメイン限定）

- """【請求項１】
  ヒトＣＤ３８（配列番号１）及びカニクイザルＣＤ３８（配列番号２）に特異的に結合する単離された抗体であって、
ａ）以下を含む重鎖可変領域：
  ｉ）配列番号３を含む第１のＣＤＲ；
  ｉｉ）配列番号４を含む第２のＣＤＲ；
  ｉｉｉ）配列番号５を含む第３のＣＤＲ；及び
ｂ）以下を含む軽鎖可変領域：
  ｉ）配列番号６を含む第１のＣＤＲ；
  ｉｉ）配列番号７を含む第２のＣＤＲ；
  ｉｉｉ）配列番号８を含む第３のＣＤＲ；
を含む、抗体。(請求項２～１９省略)【請求項２０】
  前記自己免疫疾患が、関節リウマチ、全身性エリテマトーデス、炎症性腸疾患、潰瘍性大腸炎及び移植片対宿主病からなる群から選択される、請求項１９記載の方法。
"""
- →"本発明は、ヒトCD38タンパク質(配列番号0)及びカニクイザルCD38(配列番号2)に特異的に結合する抗体に関する。本発明はまた、ヒトCD38タンパク質(配列番号0)及びカニクイザルCD38(配列番号2)に特異的に結合する抗体を、それを必要とする患者に投与することを含む、自己免疫疾患の治療方法に関する。"

- "-small" has been trained on 20,000 text pairs only. 
- dataset: ＊
- prefix: "patent claim summarization: "　（notice: single task trained.)

#参考

- https://huggingface.co/blog/how-to-generate
- 前処理が最適ではなかった。修正する。
- 任意に上位概念・下位概念と変換できるようprefixを追加する。
- 任意のテーマに沿った要約とできるようprefixを追加する。
- prefixを追加せずとも、ある程度任意のテーマに沿った要約とすることは可能。請求項の構造を利用する、任意のテーマに沿っているか判定するモデルを用い生成を補正するなど。

**check in progress**

##Licenese
- The MIT license