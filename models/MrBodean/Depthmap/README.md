1
import cv2
2
import torch
3
import gradio as gr
4
import numpy as np
5
from PIL import Image
6
7
torch.hub.download_url_to_file('https://images.unsplash.com/photo-1437622368342-7a3d73a34c8f', 'turtle.jpg')
8
torch.hub.download_url_to_file('https://images.unsplash.com/photo-1519066629447-267fffa62d4b', 'lions.jpg')
9
10
midas = torch.hub.load("intel-isl/MiDaS", "MiDaS")
11
12
use_large_model = True
13
14
if use_large_model:
15
    midas = torch.hub.load("intel-isl/MiDaS", "MiDaS")
16
else:
17
    midas = torch.hub.load("intel-isl/MiDaS", "MiDaS_small")
18
19
device = "cpu"
20
midas.to(device)
21
22
midas_transforms = torch.hub.load("intel-isl/MiDaS", "transforms")
23
24
if use_large_model:
25
    transform = midas_transforms.default_transform
26
else:
27
    transform = midas_transforms.small_transform
28
29
30
def depth(img):
31
  cv_image = np.array(img) 
32
  img = cv2.cvtColor(cv_image, cv2.COLOR_BGR2RGB)
33
34
  input_batch = transform(img).to(device)
35
  with torch.no_grad():
36
    prediction = midas(input_batch)
37
38
    prediction = torch.nn.functional.interpolate(
39
        prediction.unsqueeze(1),
40
        size=img.shape[:2],
41
        mode="bicubic",
42
        align_corners=False,
43
    ).squeeze()
44
    
45
  output = prediction.cpu().numpy()
46
  formatted = (output * 255 / np.max(output)).astype('uint8')
47
  img = Image.fromarray(formatted)
48
  return img
49
    
50
51
inputs =  gr.inputs.Image(type='pil', label="Original Image")
52
outputs = gr.outputs.Image(type="pil",label="Output Image")
53
54
title = "MiDaS"
55
description = "Gradio demo for MiDaS v2.1 which takes in a single image for computing relative depth. To use it, simply upload your image, or click one of the examples to load them. Read more at the links below."
56
article = "<p style='text-align: center'><a href='https://arxiv.org/abs/1907.01341v3'>Towards Robust Monocular Depth Estimation: Mixing Datasets for Zero-shot Cross-dataset Transfer</a> | <a href='https://github.com/intel-isl/MiDaS'>Github Repo</a></p>"
57
58
examples = [
59
    ["turtle.jpg"],
60
    ["lions.jpg"]
61
]
62
63
gr.Interface(depth, inputs, outputs, title=title, description=description, article=article, examples=examples, analytics_enabled=False).launch(debug=True)
