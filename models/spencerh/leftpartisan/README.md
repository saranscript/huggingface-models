# Text classifier using DistilBERT to determine Partisanship
## This is one of many single-class partisanship models

label_0 refers to "left" while label_1 refers to "other".  

This model was trained on 40,000 articles. 

### Best Practices
This model was optimized for 512 token-length text. Any text below 150 tokens will result in inaccurate results.  