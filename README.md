# Satellite-Imagery-to-Map Translation using Pix2Pix GAN framework
This repository contains a PyTorch implementation of the Pix2Pix framework from scratch, aimed at training a U-Net with a Generative Adversarial Network (GAN) for translating Satellite Imagery to an equivalent Map representation.

# Trained Generator and Discriminator
You can download the trained weights for the Sat2Map Generator and Discriminator from this link
https://drive.google.com/file/d/1fx4H4rW5h1ZvASzdVjBeJzoI_-KSLOUo/view?usp=drive_link

# Dataset
The Sat2Map Dataset used for training can be downloaded from this link.
https://drive.google.com/file/d/1mhfFZmsNt-jB-xvDDCYmS89IlXYFWxjt/view?usp=drive_link

# Hyper-parameters
The hyper-parameter values used for training the Sat2Map model are as follows:

Batch size: 1
Input and Output image size: 256 x 256
Learning rate: 0.0002
Momentum: [β1, β2] = [0.5, 0.999]
λ_L1 = 100
Ideas and Intuition of cGAN (conditional GAN)
Conditional GAN solves the problem of controlling the output of the Generator by taking both a random noise z and the input image x to produce an output image G(z|x) that looks realistic and corresponds to x.

# Generator Architecture - U-Net
The Generator architecture is based on the U-Net, which is an Encoder-Decoder with skip connections between layers. The Encoder extracts core features of the image, while the Decoder maps those features back to a full-size image.

# Discriminator Architecture - Convolutional Neural Network
The Discriminator in Pix2Pix is a binary Convolutional Neural Network that takes both the examined image y and the conditional image x as inputs.

Loss Function
The Objective for the training process includes GAN Loss and L1 Loss, which are combined to form the final Loss for the entire algorithm.

# Results
The trained Generator successfully learned to capture main structures in satellite imagery and map those structures to an encoded vector, producing a map representation as output.
![image](https://github.com/kartikagg05/gan_satellite-image-to-map-image/assets/112509448/b21e3f31-d98d-41f0-a542-183aae1c4d76)
![image](https://github.com/kartikagg05/gan_satellite-image-to-map-image/assets/112509448/f2d3fe95-bde3-444b-b470-b763c6d4591f)



# Other Applications
Pix2Pix GAN framework can be applied to various image translation tasks, such as Photos to Drawings, Drawings to Photos, B&W images to Colored Images, Photos to Cartoon, Photos to Anime, etc.

For more details on the implementation and usage, please refer to the documentation provided in the repository.
