---
language: en
tags:
- math
- pegasus

datasets:
- competition_math
metrics:
- rouge
widget:
- text: "Michael scores a 95, 87, 85, 93, and a 94 on his first 5 math tests. If he wants a 90 average, what must he score on the final math test?"
  example_title: "averaging"
- text: "If the sum of the smallest and largest of three consecutive even numbers is 28, what is the value of the second largest number in the series?"
  example_title: "puzzle2"
- text: "Two inlet pipes lead into a large water tank. One pipe can fill the tank in 45 minutes; the other can fill it in 40 minutes. To the nearest tenth of a minute, how long would it take the two pipes together to fill the tank if both were opened at the same time?"
  example_title: "patek water"
- text: "A football team lost 5 yards and then gained 9. What is the team's progress?"
  example_title: "sportsball"
- text: "Half a number plus 5 is 11.What is the number?"
  example_title: "half"
  
inference:
  parameters:
    max_length: 128
    no_repeat_ngram_size: 4
    length_penalty: 0.7
    repetition_penalty: 3.1
    num_beams : 4
    early_stopping: True
---

# pegasus does math?
- testing to see how feasible seq2seq math problems are
- answer: at least with 2 epochs, it is uhhhh not super feasible.
