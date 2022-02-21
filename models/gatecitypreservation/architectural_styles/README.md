---
tags:
- image-classification
- pytorch
- huggingpics
metrics:
- accuracy

model-index:
- name: architectural_styles
  results:
  - task:
      name: Image Classification
      type: image-classification
    metrics:
      - name: Accuracy
        type: accuracy
        value: 0.7796609997749329
---

### What style is that?

This model can help identify five architectural styles that were prominent in the early to mid 20th century. Check back for updates including more architectural styles and more accurate predictions as this model diversifies and improves its training. 

Upload a photograph of a building to the File Uploader on the right. The Image Classifier will predict its architectural style using a database of over 700 images. Scroll down to read more about each style. 

### Classical Revival (1895 - 1950)

The Classical Revival or Neoclassical style is one of the most commonly seen across the state and the country. This style was inspired by the World's Columbian Exposition in Chicago held in 1893 which promoted a renewed interest in the classical forms. This style encompasses many different styles, including Colonial Revival, Greek Revival, Neoclassical Revival and Mediterranean Revival. Colonial Revival is most commonly used in residential dwellings, while Greek and Neoclassical Revival styles are commonly used in commercial buildings like banks, post offices, and municipal buildings. 

![classical revival architecture](images/ex_classical_revival_architecture.jpg)

#### Queen Anne (1880-1910)

The Queen Anne style was one of a number of popular  architectural styles that emerged in the United States during the Victorian Period. It ranges from high style, like the image pictured here, to more vernacular styles that exhibit the Queen Anne form without its high style architectural details.

![queen anne architecture](images/ex_queen_anne_architecture.jpg)

#### Craftsman Bungalow (1900-1930)

The terms “craftsman” and “bungalow” are often used interchangably, however, “craftsman” refers to the Arts and Crafts movement and is considered an architectural style, whereas “bungalow” is the form of house. Bungalows often exhibit a craftsman style.

![craftsman bungalow architecture](images/ex_craftsman_bungalow_architecture.jpg)

#### Tudor Cottage (1910-1950)

Tudor homes are inspired by the Medieval period and can range is size and style. In general, the Tudor style features steeply pitched roofs, often with a cat-slide roof line, predominately brick construction, sometimes accented with half-timber framing, front-facing, prominently placed brick or stone chimneys, and tall windows with rectangular or diamond-shaped panes. Front doors are typically off-center with a round arch at the top of the door or doorway. 

![tudor cottage architecture](images/ex_tudor_cottage_architecture.jpg)

#### Mid-Century Modern Ranch (1930-1970)

The Ranch style originated in southern California in the mid-1930s. In the 1940s, the Ranch was one of the small house types financed by the Federal Housing Administration (FHA), along with Minimal Traditional and other small house styles. The Ranch house began to pick up popularity as the financial controls that encouraged small house building lifted following WWII; by the 1950s it was the most predominant residential style in the country.

![mid-century modern ranch](images/ex_mid-century_modern_ranch.jpg)

This model was created with HuggingPics🤗🖼️ Image Classifier! 
Make your own!: [the demo on Google Colab](https://colab.research.google.com/github/nateraw/huggingpics/blob/main/HuggingPics.ipynb).