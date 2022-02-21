# regnetx_002
Implementation of RegNet proposed in [Designing Network Design
Spaces](https://arxiv.org/abs/2003.13678)

 The main idea is to start with a high dimensional search space and
 iteratively reduce the search space by empirically apply constrains
 based on the best performing models sampled by the current search
 space.

 The resulting models are light, accurate, and faster than
 EfficientNets (up to 5x times!)

 For example, to go from $AnyNet_A$ to $AnyNet_B$ they fixed the
 bottleneck ratio $b_i$ for all stage $i$. The following table shows
 all the restrictions applied from one search space to the next one.

 ![image](https://github.com/FrancescoSaverioZuppichini/glasses/blob/develop/docs/_static/images/RegNetDesignSpaceTable.png?raw=true)

 The paper is really well written and very interesting, I highly
 recommended read it.

 ``` python
 ResNet.regnetx_002()
 ResNet.regnetx_004()
 ResNet.regnetx_006()
 ResNet.regnetx_008()
 ResNet.regnetx_016()
 ResNet.regnetx_040()
 ResNet.regnetx_064()
 ResNet.regnetx_080()
 ResNet.regnetx_120()
 ResNet.regnetx_160()
 ResNet.regnetx_320()
 # Y variants (with SE)
 ResNet.regnety_002()
 # ...
 ResNet.regnetx_320()

 You can easily customize your model
 ```

 Examples:

  ``` python
  # change activation
  RegNet.regnetx_004(activation = nn.SELU)
  # change number of classes (default is 1000 )
  RegNet.regnetx_004(n_classes=100)
  # pass a different block
  RegNet.regnetx_004(block=RegNetYBotteneckBlock)
  # change the steam
  model = RegNet.regnetx_004(stem=ResNetStemC)
  change shortcut
  model = RegNet.regnetx_004(block=partial(RegNetYBotteneckBlock, shortcut=ResNetShorcutD))
  # store each feature
  x = torch.rand((1, 3, 224, 224))
  # get features
  model = RegNet.regnetx_004()
  # first call .features, this will activate the forward hooks and tells the model you'll like to get the features
  model.encoder.features
  model(torch.randn((1,3,224,224)))
  # get the features from the encoder
  features = model.encoder.features
  print([x.shape for x in features])
  #[torch.Size([1, 32, 112, 112]), torch.Size([1, 32, 56, 56]), torch.Size([1, 64, 28, 28]), torch.Size([1, 160, 14, 14])]
  ```

 