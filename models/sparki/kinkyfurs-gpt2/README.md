---

language: en

license: mit


---

Import it using pipeline

    from transformers import pipeline
    text_generation = pipeline('text-generation' , model='sparki/kinkyfurs-gpt2')
    
Then use it
 
    prefix_text = input()
    text_generation(prefix_text, max_length=50, num_beams=5,no_repeat_ngram_size=2,early_stopping=True)
    