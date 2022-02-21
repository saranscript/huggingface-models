# WudaoSailing

WudaoSailing is a package for pretraining chinese Language Model and finetune tasks. Now it supports GLM, Bert, T5, Cogview and Roberta models.




## Get Started
### Docker Image
We prepare two docker images based on CUDA 10.2 and CUDA 11.2. You can build images from the docker file [docs/docker/cuda102.dockerfile](docs/docker/cuda102.dcokerfile) or pull the pre-built images from Docker Hub and run with docker v19.03+
  ```shell
  nvidia-docker run -id  --hostname=V100  --network=host\
  --ipc=host --shm-size=16gb --name=deepspeed-cuda \  
  -e NVIDIA_VISIBLE_DEVICES=0,1,2,3 \
  -v /DATA/disk1/docker/containers/:/data deepspeed/cuda102:lastest
  ```
  or replace `cuda102` with `cuda112`.

  ```shell
    docker build -f cuda102.dockerfile  -t deepspeed/cuda102 .
  ```

### Clone this repo
  ```shell
  git clone https://github.com/wangguojim/WudaoSailing.git
  cd WudaoSailing
  pip install -r requirements.txt
  ```

## GLM

We show some examples based on GLM model.

### finetuene
We provide scripts for finetuning GLM on some downstream tasks.

#### SuperGLUE

- Download the [SuperGlue](https://super.gluebenchmark.com/tasks) data and check the experiment setup in 
  [examples/glm/scripts/ds_finetune_superglue.sh](xamples/glm/scripts/ds_finetune_superglue.sh). Note that `DATA_ROOT, CHECKPOINT_PATH, SAVE_PATH` 
  need to be changed to your local path. You may also change the `batch-size` and `nproc_per_node` according to your 
  available hardware.

- Run the following script for text similarity finetune task (use the afqmc dataset as an example)

```
cd examples/glm/ 
bash scripts/ds_finetune_superglue.sh\
     config/model_blocklm_large_chinese.sh\
     config_tasks/task_afqmc.sh
```


- Run the following script for text classification finetune task  (use the thunews and thunews dataset as an example)

```
cd examples/glm/ 
bash scripts/ds_finetune_superglue.sh\
     config/model_blocklm_large_chinese.sh\
     config_tasks/task_tnews.sh
```

- Run the following script  for causal inference finetune task (use the COPA dataset as an example)

```
cd examples/glm/ 
bash scripts/ds_finetune_superglue.sh\
     config/model_blocklm_large_chinese.sh\
     config_tasks/task_copa.sh
```
  
- To apply GLM to a new NLU dataset with cloze-filling finetuning, implement a `DataProcessor` in
  [examples/glm/tasks/superglue/dataset.py](examples/glm/tasks/superglue/dataset.py) for data loading and add a `PVP` in 
  [examples/glm/tasks/superglue/pvp.py](examples/glm/tasks/superglue/pvp.py) for the cloze question. More details can be found 
  [here](examples/glm/tasks/superglue/README.md).



#### Blank Filling (Interactive)
* Change `CHECKPOINT_PATH` to your local path. Run the following script
```
bash config/generate_block.sh\
     config/model_blocklm_large_chinese.sh
```
##### Example1 (Entity Prediction):

Context: 凯旋门位于意大利米兰市古城堡旁。1807年为纪念[MASK]而建，门高25米，顶上矗立两武士青铜古兵车铸像。

GLM:拿破仑军队攻克米兰城

##### Example2 (Sentence Prediction)
Context: 工业互联网（Industrial Internet）是新一代信息通信技术与工业经济深度融合的新型基础设施、应用模式和工业生态，通过对人、机、物、系统等的全面连接，构建起覆盖全产业链、全价值链的全新制造和服务体系，为工业乃至产业数字化、网络化、智能化发展提供了实现途径，是第四次工业革命的重要基石。[sMASK]它以网络为基础、平台为中枢、数据为要素、安全为保障，既是工业数字化、网络化、智能化转型的基础设施，也是互联网、大数据、人工智能与实体经济深度融合的应用模式，同时也是一种新业态、新产业，将重塑企业形态、供应链和产业链。当前，工业互联网融合应用向国民经济重点行业广泛拓展，形成平台化设计、智能化制造、网络化协同、个性化定制、服务化延伸、数字化管理六大新模式，赋能、赋智、赋值作用不断显现，有力的促进了实体经济提质、增效、降本、绿色、安全发展。

GLM: 工业互联网是制造业技术、管理、模式的重大变革,是推动互联网、大数据、人工智能和实体经济深度融合的重要载体,是建设制造强国和网络强国的重要基础。

##### Example3 (Long Text Generation)
Context: 问题:高斯所在的国家有什么汽车品牌?答案:[gMASK]

GLM:答案:[gMASK]<|startofpiece|>德国奔驰、德国大众、别克、沃尔沃、斯柯达、本田、雪铁龙.


### Ptuning
Run the following script to integrate p-tuning with GLM:
```shell
cd algutils/ptuning/ 
bash finetune_zy.sh
```

### Pretrain
Run the following script to pre-train the GLM-Large model
```shell
cd examples/glm/ 
bash scripts/ds_pretrain_nvidia.sh config/ds_block_large.sh
```

The script [examples/glm/config/ds_pretrain_nvidia.sh](examples/glm/config/ds_pretrain_nvidia.sh) launches the training program with DeepSpeed. You should change `NUM_WORKERS` and `NUM_GPUS_PER_WORKER` to the number of workers and the number of gpus per worker. Also change `HOST_FILE_PATH` to the path to an OpenMPI-style hostfile. More details about DeepSpeed launcher can be found [here](https://www.deepspeed.ai/getting-started/#resource-configuration-multi-node).

The file [examples/glm/config/ds_block_large.sh](examples/glm/config/ds_block_large.sh) defines the hyperparameters for pretraining. Most of the arguments are fairly self-explanatory. Specifically, `--train-data` can be multiple keywords defined in `NAMED_CORPORA` in [data_utils/corpora.py](data_utils/corpora.py). The hyperparameters of the optimizer are defined in the corresponding json file under `config`. The semantics of the json file can be found [here](https://www.deepspeed.ai/docs/config-json).



## Bert

We show some examples based on GLM model.

### Pretrain
Run the following script to pre-train the Bert model
```shell
cd examples/bert/ 
python quick_start.py
```

## CogView
### Pretrain
Run the following script to pre-train the cogview model
```shell
cd examples/cogview/ 
bash config/pretrain_multiple_nodes.sh
```

### inference
Run the following script to test the ability of  text2image
```shell
cd examples/cogview/ 
bash config/text2image_cogview.sh
```
