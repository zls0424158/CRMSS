# License

Copyright (C) 2020 Jianxin Wang(jxwang@mail.csu.edu.cn), Chengqian Lu(chengqlu@csu.edu.cn)

This program is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation; either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program; if not, see <http://www.gnu.org/licenses/>.

Jianxin Wang(jxwang@mail.csu.edu.cn), School of Information Science and Engineering, Central South University, ChangSha, CHINA, 410083

Type: Package

# Title: CRMSS: Predicting circRNA-RBP binding sites based on multi-scale characterizing sequence and structural features

## Description: 
This package implements the CRMSS algorithm based on multi-scale characterizing sequence and structural features for predicting circRNA-RBP binding sites.

## Files annotation:
### 1.data/data.zip 
This compressed file includes:
1) positive.out 
2) negative.out 

These two files are sequence inputs of CRMSS. File positive.out contains sequences of all positive samples. These data are generated by crosslinking immunoprecipitation and high-throughput sequencing (CLIP-seq). Referring to previous research, we extend 50 nucleotides (nt) upstream and 50 nt downstream around CLIP-seq peak summits of each binding site, obtaining sequence segments of 101 nt lengths as positive samples. File negative.out contains sequences of all negative samples. We randomly separate sequences with the same length from the remaining regions of the circRNA as negative samples. 

### 2.code
1) model.py

This script contains the main content of the CRMSS model. 

2) main.py

This script contains a training process which trains models for each RBP and finds the best set of hyperparameters. 

3) utils.py

This script contains functions for data reading and feature generation. 


## Requirements
- keras
- sklearn
- scipy
- argparse
- time
- math
- sys
- os
- numpy
- logging
- tensorflow
- keras_self_attention

##  How to train the CRMSS model
You can train the model of 5-fold cross-validation in a very simple way by the command below: 

*Python main.py* 
There are two parsers you can set as you need:

*--proteinID*	

Select the RBP you want to train a model for. By default, CRMSS will train a model for all 37 RBPs.

*--storage*	

Select the paths you want to store the training results.

##  How to predict binding sites from new data
You can predict new binding sites in a very simple way: 

Prepare your own input file referring to our paper. 

Save the model generated from CRMSS training, and use the model to predict binding sites for the corresponding RBP.

Thank you and enjoy the tool!
