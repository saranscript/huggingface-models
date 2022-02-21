# Text classifier using DistilBERT to determine Partisanship 
## This is one of the single-class partisan detecting models. (see leftpartisan/leftcenterpartisan/rightcenterpartisan/centerpartisan)


label_0 refers to "other" while label_1 refers to "right" (right as in right-leaning).

This was trained with 40,000 articles.

### Best Practices
This model was optimized for 512 token-length text. Any text below 150 tokens will result in inaccurate results.  