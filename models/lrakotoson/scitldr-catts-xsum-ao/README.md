---
language:
- en
datasets:
- xsum
- scitldr
widget:
- text: "We introduce TLDR generation, a new form of extreme summarization, for scientific papers. TLDR generation involves high source compression and requires expert background knowledge and understanding of complex domain-specific language. To facilitate study on this task, we introduce SciTLDR, a new multi-target dataset of 5.4K TLDRs over 3.2K papers. SciTLDR contains both author-written and expert-derived TLDRs, where the latter are collected using a novel annotation protocol that produces high-quality summaries while minimizing annotation burden. We propose CATTS, a simple yet effective learning strategy for generating TLDRs that exploits titles as an auxiliary training signal. CATTS improves upon strong baselines under both automated metrics and human evaluations."
license: "apache-2.0"

---

# AI2 SciTLDR
Fairseq checkpoints from CATTS XSUM to Transformers BART (Abtract Only)

Original repository: [https://github.com/allenai/scitldr](https://github.com/allenai/scitldr)

## Demo
A running demo of AI2 model can be found [here](https://scitldr.apps.allenai.org).

### Citing
If you use code, dataset, or model weights in your research, please cite "TLDR: Extreme Summarization of Scientific Documents."

```
@article{cachola2020tldr,
  title={{TLDR}: Extreme Summarization of Scientific Documents},
  author={Isabel Cachola and Kyle Lo and Arman Cohan and Daniel S. Weld},
  journal={arXiv:2004.15011},
  year={2020},
}
```

SciTLDR is an open-source project developed by the Allen Institute for Artificial Intelligence (AI2). AI2 is a non-profit institute with the mission to contribute to humanity through high-impact AI research and engineering.