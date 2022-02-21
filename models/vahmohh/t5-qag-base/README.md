[www.github.com/vahmohh/masters-thesis](https://www.github.com/vahmohh/masters-thesis)

The model has been built upon the pre-trained T5 model by fine-tuning it on SQuAD dataset for the porpuse of automatic question and answer generation.

The following format should be used for generating questions.
  ```sh
  generate question: domain_specific_text </sep> answer_1 </sep> answer_2 </sep> ... </sep> answer_n </end>
  ```
  Output:
  ```sh
  question_1 </sep> question_2 </sep> ... </sep> question_n </end>
  ```
The following format should be used for generating answers.
  ```sh
  generate answer: domain_specific_text </end>
  ```
  Output:
  ```sh
  answer_1 </sep> answer_2 </sep> ... </sep> answer_n </end>
  ```