# DCGAN-Anime
# Description
The goal of my project is to train a GAN using a dataset consisting of anime pictures. The GAN is to learn 
how to produce anime characters from latent space representations that we create. Once we have a 
GAN that can produce anime characters from any latent space we then feed it custom latent space 
representations of data that we want the GAN to reproduce in the style of the anime. We use a trained 
encoder to turn images of real people to then be interpreted in the anime art stylw
# Network Architecture
For my project two different types of architectures were used. The first being a DCGAN or Deep 
convolutional GAN. This is a GAN that uses the theory behind a convolutional neural network in the 
discriminator to allow for more advanced feature detection making the discriminator a lot more 
accurate when it comes to images. For the discriminator network we start by image data of size 64*64*3 
into the network. We first apply convolutional layer of 3,3 and creating 128 feature maps. Then we 
apply leakyRELU and batch normalization. This is then repeated once more. We then pool the layers to 
extract empirical data from the feature maps. We then apply a dropout layer that should help with 
overfitting. Everything we did is applied once more. Then we flatten and pass to a dense layer of size 
128, apply LeakyRELu, another 128 dense with LeakyRELU. We then apply a sigmoid activation which 
gives output values of 0 to 1. For the generator we take a latent space vector of size 100 and we pass it 
through a dense layer of 4*4*512. We then apply a transpose layer; this is the opposite of a 
convolutional layer. We do 512 layers with size 4,4 and strides of 2,2. This is applied 4 more times with 
each time we halve the layers with the exception of the last layer which is 3. We then use tan activation 
to give an output of -1 to 1 which can be fed into our discriminator. For the discriminator the loss is the 
mean loss of real and fake validations. For the generator we use the validation accuracy of the 
discriminator on the fake batch. The VAE I use is from chapter 7 of our textbook. The encoder takes a 
input of size 784 and passes that though a dense layer of 256, a mean layer of 100, log variance of 100
and finally a latent space layer of size 100. The decoder then takes in the latent space of 100 and passes 
it to a dense layer of 256 and lastly back into the original size of 784. The loss function is calculated using 
binary cross entropy.
# Training 
For the training aspect I trained the DCGAN for 50000 iterations with batch size 64. From trial and error 
of multiple training I noticed after 50,000 the data would stop improving the model would start 
overfitting. I experimented with batch sizes and found the 64 was the best mix of training time and still 
creating good images
