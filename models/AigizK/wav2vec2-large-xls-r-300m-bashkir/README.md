# requirements.txt
# torch
# torchvision
# transformers
# numpy
# scipy
# matplotlib
# pandas
# sympy
# nose


import scipy.signal as sps
import torch
from scipy.io import wavfile
from transformers import AutoModelForCTC, Wav2Vec2Processor

repo_name = "AigizK/wav2vec2-large-xls-r-300m-bashkir"
model = AutoModelForCTC.from_pretrained(repo_name,
                                        cache_dir='./model')

processor = Wav2Vec2Processor.from_pretrained(repo_name)

sampling_rate, data = wavfile.read("your_audio.wav")

new_rate = 16000
number_of_samples = round(len(data) * float(new_rate) / sampling_rate)
data = sps.resample(data, number_of_samples)

input_values = processor(data,
                         sampling_rate=16000).input_values[0]

input_dict = processor(input_values,
                       return_tensors="pt", padding=True)

print(input_values)

logits = model(input_dict.input_values)
logits=logits.logits
pred_ids = torch.argmax(logits, dim=-1)[0]
print(processor.decode(pred_ids))
