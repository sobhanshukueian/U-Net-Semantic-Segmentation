# U-Net Semantic Segmentation

U-net is a semantic segmentation model architecture that developed by Olaf Ronneberger et al, for bio medical images like paper's name that mentioned this.
Below you can see the architecture of model, it contains two main parts encoder and decoder.


*   Encoder Extracts features from input data (images) and transfer it to a latent space which has lower dimensions than the inputs. It contains traditional convolutional and pooling layers.
*   Decoder performs reconstruction with the latent space representations 

The U-Net is an elegant architecture that solves most of the occurring issues. It uses the concept of fully convolutional networks for this approach. The intent of the U-Net is to capture both the features of the context as well as the localization. This process is completed successfully by the type of architecture built.


[Paper Link](https://arxiv.org/abs/1505.04597v1)


We notice skip-connections that connect the previous outputs with the layers in the decoder blocks. This skip connection is a vital concept to preserve the loss from the previous layers so that they reflect stronger on the overall values. They are also scientifically proven to produce better results and lead to faster model convergence. In the final convolution block, we have a couple of convolutional layers followed by the last convolution layer. This layer has a filter of 2 with the appropriate function to display the resulting output. This final layer can be changed according to the desired purpose of the project you are trying to perform.


# CamVid Dataset
CamVid (Cambridge-driving Labeled Video Database) is a road/driving scene understanding database which was originally captured as five video sequences with a 960×720 resolution camera mounted on the dashboard of a car. Those sequences were sampled (four of them at 1 fps and one at 15 fps) adding up to 701 frames. You Can Dowload dataset from kaggle:

[Download Dataset from Kaggle](https://www.kaggle.com/datasets/carlolepelaars/camvid)

![image](https://user-images.githubusercontent.com/47561760/192777912-5930383d-8ae8-4df3-8a89-dcfa2c93a03c.png)

## Some Configs for downloading from kaggle :
1. Go to your account, Scroll to API section and Click Expire API Token to remove previous tokens
2. Click on Create New API Token - It will download kaggle.json file on your machine.
3. Upload that file here in code.


# Train
Trainer class Does the main part of code which is training model, plot the training process and save model each n epochs.

I Defined `Adam` Optimizer with learning rate 0.0002.

Does Each training step in `train_step` function and validation step in `val_step` function and whole trining process in 
`train` function.
 
## Some Configurations
 
*   You can set epoch size : `EPOCHS` and batch size : `BATCH_SIZE`.
*   Set `device` that you want to train model on it : `device`(default runs on cuda if it's available)
*   You can set one of three `verboses` that prints info you want => 0 == nothing || 1 == model architecture || 2 == print optimizer || 3 == model parameters size.
*   Each time you train model weights and plot(if `save_plots` == True) will be saved in `save_dir`.
*   You can find a `configs` file in `save_dir` that contains some information about run. 


# Results

## Training Data
![Train predicted](https://user-images.githubusercontent.com/47561760/195614321-1ac08aa5-8076-41ac-8b72-035d42cb98e2.png)

## Validation Data
![Validation predicted](https://user-images.githubusercontent.com/47561760/195614378-2056d9c5-7d7c-4e02-be3e-3d87e4bde7ef.png)

