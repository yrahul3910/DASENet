# DASENet
This is an official implementation of the model described in:

Yongseok Lee, Suin Lee, Chan-Gun Lee, Ikjun Yeom and Honguk Woo, **"Continual Prediction of Bug-Fix Time Using Deep Learning-Based Activity Stream Embedding"** [[PDF]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8955829)

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<img src="https://github.com/dooinee/DASENet/blob/master/model.PNG" width="300" height="800"/>


## Requirements
- python3
- nltk
- tensorflow-gpu 1.14.0
- keras 2.2.4
- scikit-learn 0.21.3
- numpy 1.16.4
- pandas 0.25.1
- gensim Word2vec


## Dataset

#### Download our preprocessed dataset with following link 
https://github.com/mkris0714/Bug-Related-Activity-Logs

- `input_data/projects/{hadoop-code.json, elasticsearch-code.json, springframework-code.json}`

  These are json files with a format of
  
  {'id':id, 'sentence': source code, 'isLogged': 0 or 1, 'path': source code file name, 'method': function name}

- `input_data/projects/{hadoop-c2s.json, elasticsearch-c2s.json, springframework-c2s.json}`

  These are json files with a format of
  
  {'id': id, 'code_id': code.json id, 'sentence': combinational AST paths, 'path': code file name, 'method':function name, 'isLogged': 0 or 1}

- `input_data/npy/{hadoop.npy, elasticsearch.npy, springframework.npy}`

  These are code2seq embedding outputs as vectors from java source code except for label code lines (i.e. .log(), .write())


## Description

