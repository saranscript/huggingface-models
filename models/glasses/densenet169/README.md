# densenet169
Implementation of DenseNet proposed in [Densely Connected Convolutional
Networks](https://arxiv.org/abs/1608.06993)

 Create a default models

 ``` {.sourceCode .}
 DenseNet.densenet121()
 DenseNet.densenet161()
 DenseNet.densenet169()
 DenseNet.densenet201()
 ```

 Examples:

  ``` {.sourceCode .}
  # change activation
  DenseNet.densenet121(activation = nn.SELU)
  # change number of classes (default is 1000 )
  DenseNet.densenet121(n_classes=100)
  # pass a different block
  DenseNet.densenet121(block=...)
  # change the initial convolution
  model = DenseNet.densenet121()
  model.encoder.gate.conv1 = nn.Conv2d(3, 64, kernel_size=3)
  # store each feature
  x = torch.rand((1, 3, 224, 224))
  model = DenseNet.densenet121()
  # first call .features, this will activate the forward hooks and tells the model you'll like to get the features
  model.encoder.features
  model(torch.randn((1,3,224,224)))
  # get the features from the encoder
  features = model.encoder.features
  print([x.shape for x in features])
  # [torch.Size([1, 128, 28, 28]), torch.Size([1, 256, 14, 14]), torch.Size([1, 512, 7, 7]), torch.Size([1, 1024, 7, 7])]
  ```

 