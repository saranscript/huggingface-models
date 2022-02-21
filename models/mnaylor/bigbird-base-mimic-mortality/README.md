# BigBird for Mortality Prediction

Starting with Google's base BigBird model, we fine-tuned on binary mortality prediction in MIMIC admission notes. This 
model seeks to predict whether a certain patient will expire within a given ICU stay, based on the text available upon 
admission. Data prepared for this task as described in [this project](https://github.com/bvanaken/clinical-outcome-prediction), 
using the simulated admission notes (taken from discharge summaries). This model will be used in an upcoming submission for 
IMLH at ICML 2021.

### References
* Van Aken, et al., 2021: [Clinical Outcome Prediction from Admission Notes using Self-Supervised Knowledge Integration](https://www.aclweb.org/anthology/2021.eacl-main.75/)
* Zaheer, et al., 2020: [Big Bird: Transformers for Longer Sequences](https://papers.nips.cc/paper/2020/hash/c8512d142a2d849725f31a9a7a361ab9-Abstract.html)