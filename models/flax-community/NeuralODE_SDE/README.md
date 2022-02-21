# Neural ODE with Flax
This is the result of project ["Reproduce Neural ODE and SDE"][projectlink] in [HuggingFace Flax/JAX community week][comweeklink].

<code>main.py</code> will execute training of ResNet or OdeNet for MNIST dataset.

[projectlink]: https://discuss.huggingface.co/t/reproduce-neural-ode-and-neural-sde/7590

[comweeklink]: https://github.com/huggingface/transformers/tree/master/examples/research_projects/jax-projects#projects

## Dependency

### JAX and Flax

For JAX installation, please follow [here][jaxinstalllink].

or simply, type
```bash 
pip install jax jaxlib
```

For Flax installation,
```bash
pip install flax
```

[jaxinstalllink]: https://github.com/google/jax#installation


Tensorflow-datasets will download MNIST dataset to environment.

## How to run training

For (small) ResNet training,
```bash
python main.py --model=resnet --lr=1e-4 --n_epoch=20 --batch_size=64 
```

For Neural ODE training, 
```bash
python main.py --model=odenet --lr=1e-4 --n_epoch=20 --batch_size=64
```

For Continuous Normalizing Flow,
```bash
python main.py --model=cnf --sample_dataset=circles
```
Sample datasets can be chosen as circles, moons, or scurve.

# Sample Results

![cnf-viz](https://user-images.githubusercontent.com/72425253/126124351-44e00438-055e-4b1c-90ee-758a545dd602.gif)
![cnf-viz](https://user-images.githubusercontent.com/72425253/126124648-dcb3f8f4-396a-447c-96cf-f9304377fa48.gif)
![cnf-viz](https://user-images.githubusercontent.com/72425253/126127269-4c02ee6a-a9a3-4b9f-b380-f8669f58872b.gif)

# Bird Call generation Score SDE 

These are the codes for the bird call generation score sde model. 

<code>core-sde-sampler.py</code> will execute the sampler. The sampler uses pretrained weight to generate bird calls. The weight can be found [here](https://github.com/mandelbrot-walker/Birdcall-score-sde/blob/main/ckpt.flax)

For using different sample generation parameters change the argument values. For example,
```bash
python main.py --sigma=25 --num_steps=500 --signal_to_noise_ratio=0.10 --etol=1e-5 --sample_batch_size = 128 --sample_no = 47
``` 
In order to generate the audios, these dependencies are required,

```bash 
pip install librosa
pip install soundfile
```
In order to train the model from scratch, please generate the dataset using this [link](www.kaggle.com/ibraheemmoosa/birdsong-spectogram-generation). The dataset is generated in kaggle. Therefore, during training your username and api key is required in the specified section inside the script. 
```bash
python main.py --sigma=35 --n_epochs=1000 --batch_size=512 --lr=1e-3 --num_steps=500 --signal_to_noise_ratio=0.15 --etol=1e-5 --sample_batch_size = 64 --sample_no = 23
``` 
Generated samples can be found [here](https://github.com/mandelbrot-walker/Birdcall-score-sde/tree/main/generated_samples)
and [here](https://colab.research.google.com/drive/1AbF4aIMkSfNs-G__MXzqY7JSrz6qvLYN)