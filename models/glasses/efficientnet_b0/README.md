# efficientnet_b0
Implementation of EfficientNet proposed in [EfficientNet: Rethinking
Model Scaling for Convolutional Neural
Networks](https://arxiv.org/abs/1905.11946)

 ![image](https://github.com/FrancescoSaverioZuppichini/glasses/blob/develop/docs/_static/images/EfficientNet.png?raw=true)

 The basic architecture is similar to MobileNetV2 as was computed by
 using [Progressive Neural Architecture
 Search](https://arxiv.org/abs/1905.11946) .

 The following table shows the basic architecture
 (EfficientNet-efficientnet\_b0):

 ![image](https://github.com/FrancescoSaverioZuppichini/glasses/blob/develop/docs/_static/images/EfficientNetModelsTable.jpeg?raw=true)

 Then, the architecture is scaled up from
 [-efficientnet\_b0]{.title-ref} to [-efficientnet\_b7]{.title-ref}
 using compound scaling.

 ![image](https://github.com/FrancescoSaverioZuppichini/glasses/blob/develop/docs/_static/images/EfficientNetScaling.jpg?raw=true)

 ``` python
 EfficientNet.efficientnet_b0()
 EfficientNet.efficientnet_b1()
 EfficientNet.efficientnet_b2()
 EfficientNet.efficientnet_b3()
 EfficientNet.efficientnet_b4()
 EfficientNet.efficientnet_b5()
 EfficientNet.efficientnet_b6()
 EfficientNet.efficientnet_b7()
 EfficientNet.efficientnet_b8()
 EfficientNet.efficientnet_l2()
 ```

 Examples:

  ``` python
  EfficientNet.efficientnet_b0(activation = nn.SELU)
  # change number of classes (default is 1000 )
  EfficientNet.efficientnet_b0(n_classes=100)
  # pass a different block
  EfficientNet.efficientnet_b0(block=...)
  # store each feature
  x = torch.rand((1, 3, 224, 224))
  model = EfficientNet.efficientnet_b0()
  # first call .features, this will activate the forward hooks and tells the model you'll like to get the features
  model.encoder.features
  model(torch.randn((1,3,224,224)))
  # get the features from the encoder
  features = model.encoder.features
  print([x.shape for x in features])
  # [torch.Size([1, 32, 112, 112]), torch.Size([1, 24, 56, 56]), torch.Size([1, 40, 28, 28]), torch.Size([1, 80, 14, 14])]
  ```

 