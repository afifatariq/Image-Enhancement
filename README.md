# Image-Enhancement
Converting images from low resolution to high resolution using GANs

**Abstract
**
Image enhancement is the technique used to construct a
high-resolution image from a low resolution image. This
paper aims to provide a review into what are the possible
techniques that can be used to construct the high
resolution images. I have used Generative Adversarial
Networks (GANs) for this task, mainly SRGAN (Super
Resolution Generative Adversarial Network) and DCGAN
(Deep Convolution Generative Adversarial Network).

**INTRODUCTION
**
As a classical task in computer vision, image enhancement

aims to restore a high-resolution image from a degraded low-
resolution one. There are several methods that are possible to

achieve this task. I have tried out 2 of these methods which
use GANs. Different techniques give us different types of
results.
Super-Resolution Generative Adversarial Network, or
SRGAN, is a Generative Adversarial Network (GAN) that can
generate super-resolution images from low-resolution images,
with finer details and higher quality. CNNs were earlier used
to produce high-resolution images that train quicker and
achieve high-level accuracy. However, in some cases, they are
incapable of recovering finer details and often generate blurry
images.
SRGAN has three neural networks, a generator, a
discriminator, and a pre-trained VGG19 network on the
Imagenet dataset. The first step in building a SRGAN is to
import the data and preprocess it. I have used the CelebFaces
Attributes Dataset (CelebA). We need to train on 2 sets of
images, low resolution images and high resolution images

because our goal is to go from the low resolution image to the
high resolution image. The CelebA dataset contains the high
resolution image. By resizing these images, we can get their
low resolution images as well.
The generator is fed the low resolution images and is tasked
to create high resolution images. The discriminator is fed both
the fake generated image from generator and high resolution
image from dataset for training. It is then taught to guess
which image is fake and which is real and that’s how it trains.
The GAN loss is sent back to the generator to train it. The
generator learns from the discriminators output.
The most important part of the architecture is the generator
loss function. Generator loss is actually the sum of the content
Loss and the adversarial loss. To calculate the content loss, the
generated images and HR images are passed through the
pretrained vgg19 (for matching the features) and then the
mean loss is calculated. This allows us to recover the photo
realistic textures/features which were lost when the image was
downsampled. This in turn gives us a result which is close to
the reality of a face.
After getting good results from implementing SRGAN, I
decided to try another method to enhance images as well
which is using Deep Convolution Generative Adversarial
Network. DCGANs are usually fed random noise vector and
then an image is generated. We need to modify that technique
for our system so that the input is the low resolution image
instead of the noise vector.
We also need to change the architecture a bit so that instead
of the normal DCGAN architecture, we need to add 5 residual
layers to it. The loss function for the generator composes of
the content loss and the adversarial loss. The content loss is
calculated by the difference in the generated image and the
original image calculated as l1 norm.
