---
language:
- ru
tags:
- PyTorch
- Transformers
widget:
- text: "Батя возвращается трезвый, в руке буханка"
  example_title: "Example 1"
- text: "Как дела? Как дела? Это новый кадиллак"
  example_title: "Example 2"
- text: "4:20 на часах и я дрочу на твоё фото"
  example_title: "Example 3" 
inference:
 parameters:
   temperature: 0.9
   k: 50
   p: 0.95
   length: 1500
---
Model based on [ruGPT-3](https://huggingface.co/sberbank-ai/rugpt3small_based_on_gpt2) for generating songs.
Tuned on lyrics collected from [genius](https://genius.com/).
Examples of used artists:
* [Oxxxymiron](https://genius.com/artists/Oxxxymiron)
* [Моргенштерн](https://genius.com/artists/Morgenshtern)
* [ЛСП](https://genius.com/artists/Lsp)
* [Гражданская оборона](https://genius.com/artists/Civil-defense)
* [Король и Шут](https://genius.com/artists/The-king-and-the-jester)
* etc