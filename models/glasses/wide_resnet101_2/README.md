# wide_resnet101_2
Implementation of Wide ResNet proposed in [\"Wide Residual
Networks\"](https://arxiv.org/pdf/1605.07146.pdf)

 Create a default model

 ``` python
 WideResNet.wide_resnet50_2()
 WideResNet.wide_resnet101_2()
 # create a wide_resnet18_4
 WideResNet.resnet18(block=WideResNetBottleNeckBlock, width_factor=4)
 ```

 Examples:

  ``` python
  # change activation
  WideResNet.resnext50_32x4d(activation = nn.SELU)
  # change number of classes (default is 1000 )
  WideResNet.resnext50_32x4d(n_classes=100)
  # pass a different block
  WideResNet.resnext50_32x4d(block=SENetBasicBlock)
  # change the initial convolution
  model = WideResNet.resnext50_32x4d
  model.encoder.gate.conv1 = nn.Conv2d(3, 64, kernel_size=3)
  # store each feature
  x = torch.rand((1, 3, 224, 224))
  model = WideResNet.wide_resnet50_2()
  features = []
  x = model.encoder.gate(x)
  for block in model.encoder.layers:
      x = block(x)
      features.append(x)
  print([x.shape for x in features])
  # [torch.Size([1, 64, 56, 56]), torch.Size([1, 128, 28, 28]), torch.Size([1, 256, 14, 14]), torch.Size([1, 512, 7, 7])]
  ```

 