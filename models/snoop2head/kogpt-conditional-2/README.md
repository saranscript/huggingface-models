# KoGPT-Conditional-2

### Condition format
```python
# create condition sentence
random_main_logit = np.random.normal(
    loc=3.368,
    scale=1.015,
    size=1
    )[0].round(1)
random_sub_logit = np.random.normal(
    loc=1.333,
    scale=0.790,
    size=1
    )[0].round(1)
condition_sentence = f"{random_main_logit}만큼 행복감정인 문장이다. {random_sub_logit}만큼 놀람감정인 문장이다. "

```

### Input Format
```python
# make input sentence
input_sentence = "수상한 밤들이 계속되던 날, 언젠가부터 나는"
condition_plus_input = condition_sentence + input_sentence
print(condition_plus_input)
```
```
3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는
```

### How to infer
```
inferred_sentence = infer_sentence(condition_plus_input, k=10, output_token_length=max_token_length)
inferred_sentence
```
```
['3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 서서히 제정신을 차리고 일어날 수 있었다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 달 보는 걸 좋아하게 되었다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 수상한 사람들의 입을 들여다 볼 수 있었다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 이상한 나라의 앨리스가 되어 있었다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 기이한 경험을 했다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 이상하게도 평화가 찾아온다는 사실을 깨달았다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 어둠을 뚫는 무언가가 있다는 걸 알았다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 달빛의 의미를 이해하기 시작했다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 안방에서 잘 때 내 손을 꼭 잡았다',
 '3.9만큼 행복감정인 문장이다. 1.2만큼 놀람감정인 문장이다. 수상한 밤들이 계속되던 날, 언젠가부터 나는 이상한 나라의 앨리스처럼 눈을 반짝이며 주위를 탐구하기 시작했다']

```
