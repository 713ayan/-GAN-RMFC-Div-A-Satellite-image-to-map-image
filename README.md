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
![image](https://github.com/kartikagg05/-GAN-RMFC-Div-A-Satellite-image-to-map-image/assets/125241420/de93b45e-f8fa-4091-ac32-d63c6fd46fae)
The architecture above is the U-Net 572. What I used in this project is U-Net 256. The only difference is the input image size and the output image size.
# Function:
The Encoder is the convolutional layers to the left of the network. The role of those layers is to extract core features of the image and map those features to the bottlekneck latent space at the middle of the network (an 1024-D array). This latent space is the encoded form which contains the most important information of the input image.

The Decoder is the transpose convolutional layers to the right of the network. Those layers map encoded latent space of the image back to a full-size image. Those layers do not simply output the same input image, but they are trained to map the encoded features to an image with another representation. For instance, the Encoder encodes the information of a Dog photo, and then the Decoder maps the encoded information of the dog to a drawing of the same dog. Both input and output have the same information: a dog, but they have different representation: a photo and a drawing.

To make training more stable, extracted information from the Encoder network was concantenated to corresponding layers in the Decoder network. This ensures that the Decoder has sufficient information to map the latent space to a realistic image.

Since the Encoder and Decoder was in the same network, we can train U-Net end-to-end.

# Discriminator Architecture - Convolutional Neural Network
The Discriminator in Pix2Pix is a binary Convolutional Neural Network that takes both the examined image y and the conditional image x as inputs.

Loss Function
The Objective for the training process includes GAN Loss and L1 Loss, which are combined to form the final Loss for the entire algorithm.

# Results
The trained Generator successfully learned to capture main structures in satellite imagery and map those structures to an encoded vector, producing a map representation as output.
Satellite Image(Input)
![image](https://github.com/kartikagg05/gan_satellite-image-to-map-image/assets/112509448/b21e3f31-d98d-41f0-a542-183aae1c4d76)
Map Image (Output)
![image](https://github.com/kartikagg05/gan_satellite-image-to-map-image/assets/112509448/f2d3fe95-bde3-444b-b470-b763c6d4591f)



# Other Applications
Pix2Pix GAN framework can be applied to various image translation tasks, such as Photos to Drawings, Drawings to Photos, B&W images to Colored Images, Photos to Cartoon, Photos to Anime, etc.

For more details on the implementation and usage, please refer to the documentation provided in the repository.
