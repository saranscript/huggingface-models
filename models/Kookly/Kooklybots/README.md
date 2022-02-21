from transformers import AutoTokenizer, AutoModelForCausalLM

tokenizer = AutoTokenizer.from_pretrained("r3dhummingbird/DialoGPT-medium-joshua")

model = AutoModelForCausalLM.from_pretrained("r3dhummingbird/DialoGPT-medium-joshua")