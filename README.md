# BERT-toxicity-classification
This repo show how to train bert model on [Jigsaw Unintended Bias in Toxicity Classification](https://www.kaggle.com/c/jigsaw-unintended-bias-in-toxicity-classification )  
**star me and i will keep update the code**

### LB Score 
1. 2019-04-06: 0.91216

### How to output the prediction on test data by finetuning bert model
#### 1.prepare
1.1 download the pretrain model
1.2 download the data and unzip to input folder
1.3 split the train and dev data(for convenience, i just tyde this command and not recommanded)
```
cat train.csv | tail -n 1000 > dev_1000.csv
```

#### 2.train model
2.1 run run_classifier.py
```
python run_classifier.py \
  --data_dir=input/ --vocab_file=uncased_L-12_H-768_A-12/vocab.txt \
  --bert_config_file=uncased_L-12_H-768_A-12/bert_config.json \
  --init_checkpoint=uncased_L-12_H-768_A-12/bert_model.ckpt \
  --task_name=toxic \
  --do_train=True \
  --do_eval=True \
  --do_predict=True \
  --output_dir=model_output/
```
2.2 the model will train 10 epochs, but you can stop it depend on your time
2.3 the checkpoint will be saved on the model_output, also the prediton on the test data(see model_output/test_result.tsv)

#### 3.generate the submission
3.1 run encode.py
3.2 upload the output/sub.csv to kaggle

### What is the different with official code**
1. add csv handler(line 243 in run_classifier.py)
2. add ToxicProcessor(line 264 in run_classifier.py)

### To do
1. text clean and OOV
2. CV
3. average different checkpoint prediction

**like this repo? you can buy me a cup of coffee**