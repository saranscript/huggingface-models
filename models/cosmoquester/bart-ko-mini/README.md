---
language: ko
---

# Pretrained BART in Korean

This is pretrained BART model with multiple Korean Datasets.

I used multiple datasets for generalizing the model for both colloquial and written texts.

The training is supported by [TPU Research Cloud](https://sites.research.google/trc/) program.

The script which is used to pre-train model is [here](https://github.com/cosmoquester/transformers-bart-pretrain).

When you use the reference API, you must wrap the sentence with `[BOS]` and `[EOS]` like below example.

```
[BOS] 안녕하세요? 반가워요~~ [EOS]
```

You can also test mask filling performance using `[MASK]` token like this.
```
[BOS] [MASK] 먹었어? [EOS]
```

## Benchmark

<style>
table {
  border-collapse: collapse;
  border-style: hidden;
  width: 100%;
}

td, th {
  border: 1px solid #4d5562;
  padding: 8px;
}
</style>

<table>
 <tr>
  <th>Dataset</th>
  
  <td>KLUE NLI dev</th>
  <td>NSMC test</td>
  <td>QuestionPair test</td>
  <td colspan="2">KLUE TC dev</td>
  <td colspan="3">KLUE STS dev</td>
  <td colspan="3">KorSTS dev</td>
  <td colspan="2">HateSpeech dev</td>
 </tr>
 <tr>
  <th>Metric</th>
  
  <!-- KLUE NLI -->
  <td>Acc</th>
  
  <!-- NSMC -->
  <td>Acc</td>
  
  <!-- QuestionPair -->
  <td>Acc</td>
  
  <!-- KLUE TC -->
  <td>Acc</td>
  <td>F1</td>
  
  <!-- KLUE STS -->
  <td>F1</td>
  <td>Pearson</td>
  <td>Spearman</td>
  
  <!-- KorSTS -->
  <td>F1</td>
  <td>Pearson</td>
  <td>Spearman</td>
  
  <!-- HateSpeech -->
  <td>Bias Acc</td>
  <td>Hate Acc</td>
 </tr>
 
 <tr>
  <th>Score</th>
  
  <!-- KLUE NLI -->
  <td>0.5253</th>
  
  <!-- NSMC -->
  <td>0.8425</td>
  
  <!-- QuestionPair -->
  <td>0.8945</td>
  
  <!-- KLUE TC -->
  <td>0.8047</td>
  <td>0.7988</td>
  
  <!-- KLUE STS -->
  <td>0.7411</td>
  <td>0.7471</td>
  <td>0.7399</td>
  
  <!-- KorSTS -->
  <td>0.7725</td>
  <td>0.6503</td>
  <td>0.6191</td>
  
  <!-- HateSpeech -->
  <td>0.7537</td>
  <td>0.5605</td>
 </tr>
</table>

- The performance was measured using [the notebooks here](https://github.com/cosmoquester/transformers-bart-finetune) with colab.

## Used Datasets

### [모두의 말뭉치](https://corpus.korean.go.kr/)
- 일상 대화 말뭉치 2020
- 구어 말뭉치
- 문어 말뭉치
- 신문 말뭉치

### AIhub
- [개방데이터 전문분야말뭉치](https://aihub.or.kr/aidata/30717)
- [개방데이터 한국어대화요약](https://aihub.or.kr/aidata/30714)
- [개방데이터 감성 대화 말뭉치](https://aihub.or.kr/aidata/7978)
- [개방데이터 한국어 음성](https://aihub.or.kr/aidata/105)
- [개방데이터 한국어 SNS](https://aihub.or.kr/aidata/30718)

### [세종 말뭉치](https://ithub.korean.go.kr/)
