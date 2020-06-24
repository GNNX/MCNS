# MCNS

### __[Arxiv](https://arxiv.org/abs/2005.09863)__

Understanding Negative Sampling in Graph Representation Learning.

Zhen Yang*, Ming Ding*, Chang Zhou, Hongxia Yang, Jingren Zhou, Jie Tang. (*These authors contributed equally to this work.)

In KDD 2020 (Research Track)


## Introduction
We systematically analyze the role of negative sampling from the perspectives of both objective and risk, and quantify that the negative sampling distribution should be positively but sub-linearly correlated to their positive sampling distribution. With the guidance of the theory, we propose MCNS, approximating the positive distribution with self-contrast approximation and accelerating negative sampling by Metropolis-Hastings. 

## Preparation
* Python 3.7
* Tensorflow 1.14.0


## Training
### Training on the existing datasets
#### For GraphSAGE:
You can use ```$ ./experiments/graphsage/***.sh``` to train MCNS model on the recommendation task. For example, if you want to train on the Amazon dataset, you can run ```$ ./experiments/graphsage/amazon.sh``` or ```python main.py --input data/amazon/ --model graphsage_mean ``` to train MCNS model.

#### For DeepWalk:
You can use ```$ ./experiments/deepwalk/***.sh``` to train MCNS model on the recommendation task. For example, if you want to train on the ml-100k dataset, you can run ```$ ./experiments/deepwalk/ml.sh``` or ```python main.py --input data/ml-100k/ --model deepwalk ``` to train MCNS model.

#### For GCN:
You can use ```$ ./experiments/gcn.sh``` to train MCNS model on the ml-100k dataset for recommendation task. 


### Training on your own datasets
if you want to train MCNS on your own dataset, you should prepare the following four files:
* train.txt: Each line represents an edge ```<node1> <node2>```.
* valid.txt: the same format with train.txt
* test.txt: the same format with train.txt
* test_neg.txt: For each node, we select some unconnected nodes as negs for evaluation. For Amazon and Alibaba datasets, we select 500 negs, and all unconnected negs for ml-100k to evaluate hits@k and MRR. ```(generated by load_data.py/load_test_neg function).```  


## Dataset
* ml-100k contains 943 users, 1,682 items and 100,000 edges.
* Amazon contains 192,403 users, 63,001 items and 1,689,188 edges.
* Alibaba contains 106,042 users, 53591 items and 907,470 edges.

## Acknowledgement
The trainable encoder of our code is based on [GraphSAGE](https://github.com/williamleif/GraphSAGE).

## Cite

Please cite our paper if you find this code useful for your research:
```
@misc{2005.09863,
Author = {Zhen Yang and Ming Ding and Chang Zhou and Hongxia Yang and Jingren Zhou and Jie Tang},
Title = {Understanding Negative Sampling in Graph Representation Learning},
Year = {2020},
Eprint = {arXiv:2005.09863},
}
```
