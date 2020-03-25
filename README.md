# DASENet
This is an official implementation of the model described in:

Yongseok Lee, Suin Lee, Chan-Gun Lee, Ikjun Yeom and Honguk Woo, "Continual Prediction of Bug-Fix Time Using Deep Learning-Based Activity Stream Embedding" [[PDF]](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8955829)

<center style="padding: 40px"><img width="70%" src="https://github.com/dooinee/DASENet/blob/master/model.PNG" /></center>


## Requirements
- python3
- tensorflow-gpu 1.14.0
- keras 2.2.4
- scikit-learn 0.21.3
- numpy 1.16.4
- pandas 0.25.1
- nltk
- gensim Word2vec


## Dataset

#### Download our preprocessed dataset with following a google drive link (compressed: 11G, extracted ??GB)
https://drive.google.com/open?id=1nuBghuV_FKAyKTtpIVKp6OJset8PB3eq

- `input_data/projects/{hadoop-code.json, elasticsearch-code.json, springframework-code.json}`

  These are json files with a format of
  
  {'id':id, 'sentence': source code, 'isLogged': 0 or 1, 'path': source code file name, 'method': function name}

- `input_data/projects/{hadoop-c2s.json, elasticsearch-c2s.json, springframework-c2s.json}`

  These are json files with a format of
  
  {'id': id, 'code_id': code.json id, 'sentence': combinational AST paths, 'path': code file name, 'method':function name, 'isLogged': 0 or 1}

- `input_data/npy/{hadoop.npy, elasticsearch.npy, springframework.npy}`

  These are code2seq embedding outputs as vectors from java source code except for label code lines (i.e. .log(), .write())


## Description

There are three models in our experience, 
- The model using **Text-based embedding (word2vec)**
- The model using **Path-based embedding (code2seq)**
- The model using **Merged embedding (word2vec + code2seq)**


`main_word2vec.ipynb`
contains a-RNN, CNN using Text-based embedding.

`main_mergeNet.ipynb`
contains a-RNN, CNN using only Path-based embedding and Merged embedding implementation is also here. 
(Cause code2seq has complicated preprocessing steps, the implementation of both models are in the same file.)


Although the results of visualization is not in the paper, I was tried to interpretation of the trained model by visualizing attention score over source code texts with Text-based embedding in `visualize_attention.ipynb`. You can check the results in `tex_file/` directory along each class as latex or pdf file.  
