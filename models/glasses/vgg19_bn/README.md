# vgg19_bn
Implementation of VGG proposed in [Very Deep Convolutional Networks For
Large-Scale Image Recognition](https://arxiv.org/pdf/1409.1556.pdf)

 ``` python
 VGG.vgg11()
 VGG.vgg13()
 VGG.vgg16()
 VGG.vgg19()
 VGG.vgg11_bn()
 VGG.vgg13_bn()
 VGG.vgg16_bn()
 VGG.vgg19_bn()
 ```

 Please be aware that the [bn]{.title-ref} models uses BatchNorm but
 they are very old and people back then don\'t know the bias is
 superfluous in a conv followed by a batchnorm.

 Examples:

  ``` python
  # change activation
  VGG.vgg11(activation = nn.SELU)
  # change number of classes (default is 1000 )
  VGG.vgg11(n_classes=100)
  # pass a different block
  from nn.models.classification.senet import SENetBasicBlock
  VGG.vgg11(block=SENetBasicBlock)
  # store the features tensor after every block
  ```

 