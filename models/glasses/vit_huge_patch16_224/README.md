# vit_huge_patch16_224
 Implementation of Vision Transformer (ViT) proposed in [An Image Is
 Worth 16x16 Words: Transformers For Image Recognition At
 Scale](https://arxiv.org/pdf/2010.11929.pdf)

 The following image from the authors shows the architecture.

 ![image](https://github.com/FrancescoSaverioZuppichini/glasses/blob/develop/docs/_static/images/ViT.png?raw=true)

 ``` python
 ViT.vit_small_patch16_224()
 ViT.vit_base_patch16_224()
 ViT.vit_base_patch16_384()
 ViT.vit_base_patch32_384()
 ViT.vit_huge_patch16_224()
 ViT.vit_huge_patch32_384()
 ViT.vit_large_patch16_224()
 ViT.vit_large_patch16_384()
 ViT.vit_large_patch32_384()
 ```

 Examples:

  ``` python
  # change activation
  ViT.vit_base_patch16_224(activation = nn.SELU)
  # change number of classes (default is 1000 )
  ViT.vit_base_patch16_224(n_classes=100)
  # pass a different block, default is TransformerEncoderBlock
  ViT.vit_base_patch16_224(block=MyCoolTransformerBlock)
  # get features
  model = ViT.vit_base_patch16_224
  # first call .features, this will activate the forward hooks and tells the model you'll like to get the features
  model.encoder.features
  model(torch.randn((1,3,224,224)))
  # get the features from the encoder
  features = model.encoder.features
  print([x.shape for x in features])
  #[[torch.Size([1, 197, 768]),  torch.Size([1, 197, 768]), ...]
  # change the tokens, you have to subclass ViTTokens
  class MyTokens(ViTTokens):
      def __init__(self, emb_size: int):
          super().__init__(emb_size)
          self.my_new_token = nn.Parameter(torch.randn(1, 1, emb_size))
  ViT(tokens=MyTokens)
  ```

 