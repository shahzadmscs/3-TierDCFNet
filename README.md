# [Identification of Anemia and its severity level in a peripheral blood smear using 3-Tier Deep Neural Network]


------

# Introduction
This research aims to develop a CNN-based model for automatically identifying Anemic and healthy RBC elements in the microscopic image. This model will also find the severity level of Anemic RBC elements by targeting changes in shape and size of infected RBC.  We have developed a state-of-the-art anemic RBCs dataset named Anemic-RBC dataset. The proposed dataset comprises a total of 11,500 images with approximately 750,000 RBCs elements. Out of 11,500 images, 5,750 are normal, 5,750 anemic images with manually generated ground truth (binary and pixel-wise). The key contribution of the proposed research work are:-
•	A CNN-based 3-Tier deep convolutional fused neural network (3-TierDCFNet) architecture that performs two-stage classification of RBC images. 
•	Module-I classifies the input image into two classes, i.e., Healthy and Anemic image. Module-II detects anemic image severity levels and classifies them into mild or chronic.
•	 Module-II of 3-TierDCFNet also provides accurate detection of overlapped structures of Anemic RBCs.
•	We have developed a standalone RBC microscopic image dataset along with manually segmented ground truth images of both healthy and Anemic-RBCs under the supervision of a hematologist/pathologist for cross-match analysis.

<p align="center">
    <img src="3TDCFNet_Archetecture.png" width="90%"/> <br />
    <em> 
    Figure 2: Synaptic view of proposed 3-Tier CNN model. The 300x300x1 represents binary input while 300x300x3 represents RGB original image. Lable "Yes" means the training accuracy of the nth Tier is equal to the predefined threshold value. Then the output is given to the next Tier for further processing. The label "No" means the training accuracy of the nth Tier is not equal to the predefined threshold value. Then the output is given to the same Tier for more optimal feature selection. Tier-I includes the DenseNet model that receives input images of 300x300x3 and produces output 200x200x64. Tier-II is equipped with EfficeintNet to preserve semantic information and extract the features upto 100x100x128; Tier-III comprises ShuffleNet, which ensures high accuracy with less computational cost. 
    </em>
</p>

## Setup
```
    -Linux (Tested on Ubuntu 16.04)
    -NVIDIA GPU (GEFORCE RTX-3060 12 GB)
    -CUDA CuDNN (CPU mode and CUDA without CuDNN may work with minimal modification, but untested)
    -Pytorch>=1.10
    -torchvision>=0.2.1
    -dominate>=2.3.1
    -visdom>=0.1.8.3
    -keras>= 2.7
    -matplotlib>= 3.0
    -python=3.5.5
  - Pillow==5.0.0
  - numpy==1.14.1
```


# Results

<p align="center">
    <img src="confusion_matrix.png" width="80%"/> <br />
    <em> 
    Figure 2: Confusion matrix of training, validation, and testing accuracies of Module-I classification.
    </em>
</p>




# Training

To train a model:
```
python 3TDCFNet_train.py --dataroot <datapath> --name SEG  --gpu_ids 0 --display_id 0 
--lambda_L1 60 --niter 100 --niter_decay 150 --pool_size 32 --loadSize 300 --fineSize 300
```
# Testing
To test the model

```
python 3TDCFNet_test.py --dataroot <datapath> --name SEG --gpu_ids 0 --display_id 0 
--loadSize 300 --fineSize 300
```
The test results will be saved to a html file here: ./results/SEG/test_latest/index.html.
Pretrained models can be downloaded here. Place the pretrained model in ./checkpoints/SEG.

# Contact

Please feel free to drop an e-mail to mscs1122@gmail.com for any questions. 

------


