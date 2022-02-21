Convert from model .pt to transformer
Link: https://huggingface.co/tommy19970714/wav2vec2-base-960h
Bash:
```bash
pip install transformers[sentencepiece]
pip install fairseq -U

git clone https://github.com/huggingface/transformers.git
cp transformers/src/transformers/models/wav2vec2/convert_wav2vec2_original_pytorch_checkpoint_to_pytorch.py .

wget https://dl.fbaipublicfiles.com/fairseq/wav2vec/wav2vec_small.pt -O ./wav2vec_small.pt
mkdir dict
wget https://dl.fbaipublicfiles.com/fairseq/wav2vec/dict.ltr.txt

mkdir outputs
python convert_wav2vec2_original_pytorch_checkpoint_to_pytorch.py 
--pytorch_dump_folder_path ./outputs --checkpoint_path ./finetuned/wav2vec_small.pt
 --dict_path ./dict/dict.ltr.txt --not_finetuned
```
# install and upload model
```
curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
git lfs install
sudo apt-get install git-lfs
git lfs install
git clone https://huggingface.co/hoangbinhmta99/wav2vec-demo
ls
cd wav2vec-demo/
git status
git add .
git commit -m "First model version"
git config --global user.email [yourname]
git config --global user.name [yourpass]
git commit -m "First model version"
git push
```

