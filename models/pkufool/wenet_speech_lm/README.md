* Install requirements
```
pip install jieba
```

* Generate words.txt
```bash
data_dir=/path/to/wenetspeech
# the data_dir contains:
# tree -L 2 .
# .
# |-- TERMS_OF_ACCESS
# |-- WenetSpeech.json
# |-- audio
#    |-- dev
#    |-- test_meeting
#    |-- test_net
#    `-- train
grep "\"text\":" $data_dir/WenetSpeech.json | sed -e 's/["text: ]*//g' > text.txt
python -m jieba -d " " text.txt > tokenized.txt
cat tokenized.txt | awk '{for(i=1;i<=NF;i++)print $i}' | sort | uniq > words.txt
```
* Generate N-gram model
```
```