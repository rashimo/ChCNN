# ChCNN
A convolutional neural network approach to classify web requests. 
In [Character-level Convolutional Networks for Text Classification (NIPS 2015)](http://arxiv.org/abs/1509.01626)  Xiang Zhang, Junbo Zhao and Yann LeCun showed that Character-level CNN's can be used for text classifications. Since HTTP is a text-based protocol and single characters play a significant role in malicious payloads, why not use  this approach to identify malicious requests? Moreover it can ben applied anywhere in a request where is some text.  For example in Morzeux_HttpParamsDataset only payloads are considered and in  ISCX-URL-2016 classification is applied  to URLs. 

## Requirements
Tensorflow, Keras, Jupyter Notebook, Pandas, Nvidia GPU and drivers...
The best approach is to install conda. [A good resource to get started](https://medium.com/datadriveninvestor/install-tensorflow-gpu-to-use-nvidia-gpu-on-ubuntu-18-04-do-ai-71b0ce64ebc5)

## Dataset

ECML/PKDD 2007 and CSIC 2010 Datasets contain whole requests. HttpParamsDataset contains payloads. ISCX-URL-2016 contains only URLs. 

* ECML/PKDD 2007 Challenge (downloaded from https://gitlab.fing.edu.uy/gsi/web-application-attacks-datasets)
* CSIC 2010 Dataset (downloaded from https://gitlab.fing.edu.uy/gsi/web-application-attacks-datasets)
* HttpParamsDataset (downloaded from https://github.com/Morzeux/HttpParamsDataset)
* ISCX-URL-2016 (downloaded from https://www.unb.ca/cic/datasets/url-2016.html)

## Usage
1. Download datasets to corresponding directory
2. Run a transform from a chosen dataset in order to get train, test and validate samples. 
3. Adjust config.json to reflect the number of classes and input characters size as follow:
  * ECML/PKDD 2007 (8 classes, approx. 2500 characters)
  * CSIC 2010 (2 classes, approx. 1400 characters)
  * HttpParamsDataset (5 classes, approx. 500 characters)
4. Run char-cnn


## Results

Data is split into train, validate and test. Results below are for test samples after training and validating on train and validation samples. Cross-validation is in consideration. The performance could be affected since the model will not receive large batches of all classes. While training it can happen that loss suddenly starts to increase and explodes (especially for Morzeux_HttpParamsDataset). As far as I tested, lowering the learning rate in the Adam optimizer stabilizes the loss and even better results can be achieved (eg. optimizer=Adam(lr=0.0005) )    


**Results for ECML_PKDD after training for 30 Epochs with input_size of 2500 characters**

Labels:

 * valid = 0
 * xss =  1
 * sqlinjection = 2
 * ldapinjection  = 3
 * xpathinjection  = 4
 * pathtransversal = 5
 * oscommanding  = 6
 * ssi = 7

              precision    recall  f1-score   support

           0       1.00      1.00      1.00      6959
           1       0.99      1.00      1.00       371
           2       0.99      0.99      0.99       466
           3       1.00      1.00      1.00       445
           4       1.00      0.99      1.00       440
           5       0.99      0.99      0.99       494
           6       0.99      0.98      0.99       477
           7       0.99      0.99      0.99       372

**Results for CSIC2010 after training for 30 Epochs with input_size of 1400 characters**

Labels:

* valid = 0
* malicious = 1

              precision    recall  f1-score   support

           0       1.00      1.00      1.00     14404
           1       0.99      0.99      0.99      5009

**Results for Morzeux_HttpParamsDataset  after training for 10 Epochs with input_size of 500 characters**

Labels:

* valid = 0
* sqli  = 1
* xss   = 2
* path-traversal = 3
* cmdi = 4

              precision    recall  f1-score   support

           0       1.00      1.00      1.00      3803
           1       1.00      1.00      1.00      2219
           2       1.00      0.93      0.97       105
           3       0.93      0.96      0.95        74
           4       0.44      0.62      0.52        13

**Results for ISCX-URL-2016 after training for 50 Epochs with input_size of 1500 characters**

Labels:

* benign = 0
* defacement  = 1
* malware   = 2
* phishing = 3
* spam = 4

              precision    recall  f1-score   support

           0       1.00      1.00      1.00      7081
           1       0.99      1.00      1.00     19264
           2       0.99      0.98      0.99      2282
           3       0.97      0.94      0.96      2040
           4       1.00      1.00      1.00      2407

## Similar work
https://github.com/faizann24/Fwaf-Machine-Learning-driven-Web-Application-Firewall
https://www.researchgate.net/publication/329115783_Malicious_Web_Request_Detection_Using_Character-level_CNN

## Credits
Credits go to:
* https://github.com/chaitjo/character-level-cnn (some code was reused) 
* https://gitlab.fing.edu.uy/gsi/web-application-attacks-datasets (for the dataset)
* https://github.com/Morzeux/HttpParamsDataset (for the dataset)
* https://www.unb.ca/cic/datasets/url-2016.html (for the dataset)

