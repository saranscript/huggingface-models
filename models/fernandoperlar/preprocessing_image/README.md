<br />
<p align="center">
  <a href="https://github.com/FernandoPerezLara/image-preprocessing-layer">
    <img src="https://huggingface.co/fernandoperlar/preprocessing_image/resolve/main/duck.png" alt="Logo" width="100" height="146">
  </a>

  <h3 align="center">Image Preprocessing Model</h3>

  <p align="center">
    Image preprocessing in a convolutional model
    <br />
    <a href="https://github.com/FernandoPerezLara/image-preprocessing-layer"><strong>Read more about the model »</strong></a>
    <br />
    <br />
    <a href="https://github.com/FernandoPerezLara/image-preprocessing-layer">View Code</a>
    ·
    <a href="https://github.com/FernandoPerezLara/image-preprocessing-layer/issues">Report Bug</a>
    ·
    <a href="https://github.com/FernandoPerezLara/image-preprocessing-layer/discussions">Start a discussion</a>
  </p>
</p>
<br />

The main objective of this project is to apply preprocessing to an image dataset while the model is being trained.

The solution has been taken because we do not want to apply preprocessing to the data before training (i.e. create a copy of the data but already preprocessed) because we want to apply data augmentation while the model trains.

The use of `Lambda` layers has been discarded because they do not allow the use of external libraries that do not work with tensors, since we want to use the functions provided by *OpenCV* and *NumPy*.

## Preprocessing
In this example found in this repository we wanted to divide the images from HSV color masks, where it is divided into:
* **Warm zones**: red and white colors are obtained.
* **Warm zones**: The green color is obtained.
* **Cold zones**: The color blue is obtained.

Within the code you can find the declaration of these filters as:
```python
filters = {
	"original": lambda x: x,
	"red": lambda x: data.getImageTensor(x, (330, 0, 0), (360, 255, 255)) + data.getImageTensor(x, (0, 0, 0), (50, 255, 255)),
	"green": lambda x: data.getImageTensor(x, (60, 0, 0), (130, 255, 255)),
	"blue": lambda x: data.getImageTensor(x, (180, 0, 0), (270, 255, 255)),
}
```

On the other hand, the preprocessing functions are located inside `scripts/Data.py` file as follows:
```python
def detectColor(self, image, lower, upper):
	if tf.is_tensor(image):
		temp_image = image.numpy().copy() # Used for training
	else:
		temp_image = image.copy() # Used for displaying the image

	hsv_image = temp_image.copy()
	hsv_image = cv.cvtColor(hsv_image, cv.COLOR_RGB2HSV)
	mask = cv.inRange(hsv_image, lower, upper)

	result = temp_image.copy()
	result[np.where(mask == 0)] = 0
	
	return result

def getImageTensor(self, images, lower, upper):
	results = []

	for img in images:
		results.append(np.expand_dims(self.detectColor(img, lower, upper), axis=0))

	return np.concatenate(results, axis=0)
```

## Model
The model used to solve our problem was a *CNN* with a preprocessing layer:

![Model](./model.png "Model")

This model can be found in the `scripts/Model.py` file in the following function:
```python
def create_model():
	class FilterLayer(layers.Layer):
		def __init__(self, filter, **kwargs):
			self.filter = filter

			super(FilterLayer, self).__init__(name="filter_layer", **kwargs)

		def call(self, image):
			shape = image.shape
			[image, ] = tf.py_function(self.filter, [image], [tf.float32])
			image = backend.stop_gradient(image)
			image.set_shape(shape)
			
			return image

		def get_config(self):
			return super().get_config()

	model = models.Sequential()

	model.add(layers.Input(shape=(215, 538, 3)))
	model.add(FilterLayer(filter=self.filter))

	model.add(layers.Conv2D(32, (3, 3), activation="relu"))
	model.add(layers.MaxPooling2D(pool_size=(2, 2)))

	model.add(layers.Conv2D(32, (3, 3), activation="relu"))
	model.add(layers.GlobalAveragePooling2D())

	model.add(layers.Dropout(rate=0.4))
	model.add(layers.Dense(32, activation="relu"))
	model.add(layers.Dropout(rate=0.4))
	model.add(layers.Dense(2, activation="softmax"))

	return model
```

## Contributors
This work has been possible thanks to:
- [Fernando Pérez Lara](https://www.linkedin.com/in/fernandoperezlara/) ([**@FernandoPerezLara**](https://github.com/FernandoPerezLara)) for having developed the model to make this idea come true.

## License
Copyright (c) 2021 Fernando Pérez Lara.

Licensed and distributed under the [MIT](LICENSE.txt) license.
