# Unreliable News Classifier (English)
Trained, validate, and tested using a subset of the NELA-GT-2018 dataset. The dataset is split such that there was no overlap in of news sources between the three sets.
This model used the pre-trained weights of `distilbert-base-cased` as starting point (only 4 layers) and was able to achieve 84% accuracy on the test set. It has less than 1% difference in performance compared to the BERT based model while having **2.0x** the speed.

For more details: [Github](https://github.com/khizon/CS284_final_project)