# resnext50_32x4d
Implementation of ResNetXt proposed in [\"Aggregated Residual
Transformation for Deep Neural
Networks\"](https://arxiv.org/pdf/1611.05431.pdf)

 Create a default model

 ``` python
 ResNetXt.resnext50_32x4d()
 ResNetXt.resnext101_32x8d()
 # create a resnetxt18_32x4d
 ResNetXt.resnet18(block=ResNetXtBottleNeckBlock, groups=32, base_width=4)
 ```

 Examples:

 :   ``` python
     # change activation
     ResNetXt.resnext50_32x4d(activation = nn.SELU)
     # change number of classes (default is 1000 )
     ResNetXt.resnext50_32x4d(n_classes=100)
     # pass a different block
     ResNetXt.resnext50_32x4d(block=SENetBasicBlock)
     # change the initial convolution
     model = ResNetXt.resnext50_32x4d
     model.encoder.gate.conv1 = nn.Conv2d(3, 64, kernel_size=3)
     # store each feature
     x = torch.rand((1, 3, 224, 224))
     model = ResNetXt.resnext50_32x4d()
     # first call .features, this will activate the forward hooks and tells the model you'll like to get the features
     model.encoder.features
     model(torch.randn((1,3,224,224)))
     # get the features from the encoder
     features = model.encoder.features
     print([x.shape for x in features])
     #[torch.Size([1, 64, 112, 112]), torch.Size([1, 64, 56, 56]), torch.Size([1, 128, 28, 28]), torch.Size([1, 256, 14, 14])]
     ```

 