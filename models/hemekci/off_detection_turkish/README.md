---
language: tr
widget:
- text: "sevelim sevilelim bu dunya kimseye kalmaz"
---



## Offensive Language Detection Model in Turkish

 - uses Bert and pytorch
 - fine tuned with Twitter data.
 - UTF-8 configuration is done

###	Training Data
Number of training sentences: 31,277

**Example Tweets**
 - 19823 Daliaan yifng cok erken attin be...      1.38 ...| NOT|
 - 30525 @USER Bak biri kollarımda uyuyup gitmem diyor..|NOT|
 - 26468 Helal olsun be :) Norveçten sabaha karşı geldi aq... |  OFF|
 - 14105 @USER Sunu cekecek ve güzel oldugunu söylecek aptal...       |OFF|
 - 4958  Ya seni yerim ben şapşal şey 🤗 | NOT|
 - 12966 Herkesin akıllı geçindiği bir sosyal medyamız var ...   |NOT|
 - 5788  Maçın özetlerini izleyenler futbolcular gidiyo...       |NOT|

|OFFENSIVE	|RESULT	|
|--|--|
|NOT	|    25231|
|OFF|6046|
dtype: int64

###	Validation
|epoch	|Training Loss	| Valid. Loss	| Valid.Accuracy	| Training Time	| 	Validation Time	|
|--|--|--|--|--|--|
|1	|	0.31|	0.28|	0.89|	0:07:14	|	0:00:13
|2	|	0.18|	0.29|	0.90|	0:07:18	|	0:00:13
|3	|	0.08|	0.40|	0.89|	0:07:16	|	0:00:13
|4	|	0.04|	0.59|	0.89|	0:07:13	|	0:00:13


**Matthews Corr. Coef. (-1 : +1):**
Total MCC Score: 0.633
