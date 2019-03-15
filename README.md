# ChCNN
A convolutional neural network approach to classify web requests. 
In [Character-level Convolutional Networks for Text Classification (NIPS 2015)](http://arxiv.org/abs/1509.01626)  Xiang Zhang, Junbo Zhao and Yann LeCun showed that Character-level CNN's can be used for text classifications. Since HTTP is a text-based protocol, why not use  this approach to identify malicious requests?


## Requirements
Tensorflow, Keras, Jupyter Notebook, Pandas, Nvidia GPU and drivers...
The best approach is to install conda. [A good resource to get started](https://medium.com/datadriveninvestor/install-tensorflow-gpu-to-use-nvidia-gpu-on-ubuntu-18-04-do-ai-71b0ce64ebc5)

## Dataset

* ECML/PKDD 2007 Challenge (downloaded from https://gitlab.fing.edu.uy/gsi/web-application-attacks-datasets)
* CSIC 2010 Dataset (downloaded from https://gitlab.fing.edu.uy/gsi/web-application-attacks-datasets)
* HttpParamsDataset (downloaded from https://github.com/Morzeux/HttpParamsDataset)

## Usage
1. Download datasets to corresponding directory
2. Run a transform from a chosen dataset in order to get train, test and validate samples. 
3. Adjust config.json to reflect the number of classes as follow:
  * ECML/PKDD 2007 (8 classes)
  * CSIC 2010 (2 classes)
  * HttpParamsDataset (5 classes)
4. Run char-cnn

## Code
Credits go to https://github.com/chaitjo/character-level-cnn. Some code was reused. 

## Similar work
https://github.com/faizann24/Fwaf-Machine-Learning-driven-Web-Application-Firewall




