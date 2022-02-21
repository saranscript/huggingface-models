---
language: 
  - en
  - ta
  - hi
datasets:
- squad
- chaii
widget:
- text: "அலுமினியத்தின் அணு எண் என்ன?"
  context: "அலுமினியம் (ஆங்கிலம்: அலுமினியம்; வட அமெரிக்க ஆங்கிலம்: Aluminum) ஒரு வேதியியல் தனிமம் ஆகும். இதனுடைய அணு எண் 13 ஆகும். இது பூமியில் அதிகம் கிடைக்கும் உலோகங்களுள் ஒன்று. இது மின்சாரத்தையும் வெப்பத்தையும் கடத்த வல்லது. பாக்ஸைட் என்ற தாதுவில் இருந்து அலுமினியம் தயாரிக்கப்படுகிறது. இதன் வேதிக்குறியீடு Al ஆகும்."
- text: "ज्वाला गुट्टा की माँ का नाम क्या है?"
  context: "ज्वाला गुट्टा (जन्म: 7 सितंबर 1983; वर्धा, महाराष्ट्र) एक भारतीय बैडमिंटन खिलाडी हैं। प्रारंभिक जीवन ज्वाला गुट्टा का जन्म 7 सितंबर 1983 को वर्धा, महाराष्ट्र में हुआ था। उनके पिता एम. क्रांति तेलुगु और मां येलन चीन से हैं। उनकी मां येलन गुट्टा पहली बार 1977 में अपने दादा जी के साथ भारत आई थीं। ज्वाला गुट्टा की प्रारंभिक पढ़ाई हैदराबाद से हुई और यहीं से उन्होंने बैडमिंटन खेलना भी शुरू किया। कॅरियर 10 साल की उम्र से ही ज्वाला गुट्टा ने एस.एम. आरिफ से ट्रेनिंग लेना शुरू कर दिया था। एस.एम. आरिफ भारत के जाने माने खेल प्रशिक्षक हैं जिन्हें द्रोणाचार्य अवार्ड से सम्मानित किया गया है। पहली बार 13 साल की उम्र में उन्होंने मिनी नेशनल बैडमिंटन चैंपियनशिप जीती थी। साल 2000 में ज्वाला गुट्टा ने 17 साल की उम्र में जूनियर नेशनल बैडमिंटन चैंपियनशिप जीती। इसी साल उन्होंने श्रुति कुरियन के साथ डबल्स में जोड़ी बनाते हुए महिलाओं के डबल्स जूनियर नेशनल बैडमिंटन चैंपियनशिप और सीनियर नेशनल बैडमिंटन चैंपियनशिप में जीत हासिल की। श्रुति कुरियन के साथ उनकी जोड़ी काफी लंबे समय तक चली। 2002 से 2008 तक लगातार सात बार ज्वाला गुट्टा ने महिलाओं के नेशनल युगल प्रतियोगिता में जीत हासिल की।"
- text: "How many bones do you have in your body?"
  context: "A normal adult human skeleton consists of the following 206 (208 if the breast is thought to be three parts). This number can vary depending on the physiological differences. For example, in a very small number of humans, an extra rib (neck) or an extra lower spinal cord is found. There are 22 bones in the human skull (excluding the ear tendons), which are divided into eight cranium bones and 14 facial bones. (Thick numbers indicate the numbers seen in the nearby picture.) Bones (8) 1 frontal bone (2) 3 temporal bone (2) 4 occipital bone (4) Sphinoid bone (14) 7 mandible (6) maxilla (2) palatine bone (2) 5 zygotic bone (9) 9 nasal bone (2) The sacral vertebrae (4 or 5), in adults, form the sacral vertebrae (3 to 5), in adults they form the valve."
---
# XLM-RoBERTa for question answering in Indian languages
pre-trained XLM-Roberta with intermediate pre-training on SQUAD dataset (English) and fine tuning on Chaii dataset (Tamil, Hindi)

# How to use from the 🤗/transformers library

```
from transformers import AutoTokenizer, AutoModelForQuestionAnswering
  
tokenizer = AutoTokenizer.from_pretrained("gokulkarthik/xlm-roberta-qa-chaii")

model = AutoModelForQuestionAnswering.from_pretrained("gokulkarthik/xlm-roberta-qa-chaii")
```