Converted for Tensorflow
```
name = "xlm-roberta-large"
!rm -rf local
!git clone https://huggingface.co/kornesh/"$name" local
model = TFAutoModel.from_pretrained(name, from_pt=True)
tokenizer = AutoTokenizer.from_pretrained(name)
model.save_pretrained("local")
tokenizer.save_pretrained("local")
!cd local/ && git lfs install && git add . && git commit -m "Initial commit" && git push
```