### Reproducibility
```bash
# 1. install nncf
# checkout nncf 9c2845eeb38b4ab1b6d4ca19e31a1886e5bdf17c
# patch b/nncf/torch/sparsity/magnitude/algo.py
 
    def sparsify_params(self):
        from collections import OrderedDict
        sparse_sd = OrderedDict()
        with torch.no_grad():    
            for sparse_info in self.sparsified_module_info:
                for n, m in self.model.named_modules():
                    if m == sparse_info.module:
                        sparse_sd[n+'.weight'] = m.weight*sparse_info.operand.binary_mask

        model_sd = self.model.state_dict()
        for k, v in sparse_sd.items():
            assert k in model_sd, "key not exists!"
            model_sd[k] = sparse_sd[k]
        self.model.load_state_dict(model_sd)


# 2. transformers fork
git clone https://github.com/vuiseng9/transformers
cd transformers && git checkout gen-hybrid-sparse

# 3. follow 
# transformers/examples/pytorch/question-answering/gen-hybrid-sparse/vscode-launch.json
```

### Key Content
```
gen_hybrid_sparse
├── 90pc_sparse-02_head-0512_ffnn
│   ├── 90pc_sparse-02_head-0512_ffnn-8bit.onnx
│   ├── ir
│   │   ├── 90pc_sparse-02_head-0512_ffnn-8bit.bin
│   │   ├── 90pc_sparse-02_head-0512_ffnn-8bit.mapping
│   │   ├── 90pc_sparse-02_head-0512_ffnn-8bit.xml
├── 90pc_sparse-04_head-1024_ffnn
│   ├── 90pc_sparse-04_head-1024_ffnn-8bit.onnx
│   ├── ir
│   │   ├── 90pc_sparse-04_head-1024_ffnn-8bit.bin
│   │   ├── 90pc_sparse-04_head-1024_ffnn-8bit.mapping
│   │   ├── 90pc_sparse-04_head-1024_ffnn-8bit.xml
├── 90pc_sparse-06_head-1536_ffnn
│   ├── 90pc_sparse-06_head-1536_ffnn-8bit.onnx
│   ├── ir
│   │   ├── 90pc_sparse-06_head-1536_ffnn-8bit.bin
│   │   ├── 90pc_sparse-06_head-1536_ffnn-8bit.mapping
│   │   ├── 90pc_sparse-06_head-1536_ffnn-8bit.xml
├── 90pc_sparse-08_head-2048_ffnn
│   ├── 90pc_sparse-08_head-2048_ffnn-8bit.onnx
│   ├── ir
│   │   ├── 90pc_sparse-08_head-2048_ffnn-8bit.bin
│   │   ├── 90pc_sparse-08_head-2048_ffnn-8bit.mapping
│   │   ├── 90pc_sparse-08_head-2048_ffnn-8bit.xml
└── 90pc_unstructured_sparse
    ├── 90pc_unstructured_sparse-8bit.onnx
    └── ir
        ├── 90pc_unstructured_sparse-8bit.bin
        ├── 90pc_unstructured_sparse-8bit.mapping
        ├── 90pc_unstructured_sparse-8bit.xml
```

