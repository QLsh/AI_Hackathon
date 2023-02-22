# Prediction of Drop Trajectories using VAE Model
## Introduction
Droplet based microfluidics is an important and rapidly growing interdisciplinary field of research which combines soft matter physics, biochemistry and microsystems engineering. The applications of microfluidics droplet include fast analytical systems, the synthesis of advanced materials, protein crystallization and biological assays for living cells. Precise control of droplet volumes and reliable manipulation of individual droplets such as coalescence, mixing of their contents, and sorting in combination with fast analysis tools allow us to perform chemical reactions inside the droplets under defined conditions.

However, the presence of nodes and often loops in the microfluidic network notably affect the complexity of the flow behavior of droplets, which means it is not that easy to control and estimate the behavior of microfluidics droplets. In our report, with the help of machine learning technology, we analysis a dataset of microfluidics drop dynamics to build a model which can be used to estimate drop dynamics and evaluate the average mean squared error of all the test dataset.

## Method
The dataset we are using has 48 trajectories in total, each containing hundreds of time frames. Trajectories 1-23 represents the tracks of particles with coalescence, while trajectories 24-48 are for those without coalescence. Among all the trajectories, 1-15 and 24-39 with first 100 frames are utilized as training input and their last 15 frames as training outputs to train the model established. The first 100 frames of trajectories 16-23 and 40-48 are taken as testing inputs and the accuracy of our model could be illustrated from the mean square root of true values and prediction using the model. The Variable Encoder is an upgraded version of the autoencoder and is similar to the autoencoder in structure, also consisting of an encoder and a decoder. For an autoencoder, it is not possible to generate the arbitrary data because there is no way to construct the hidden vector, so we need to encode some data to know what the hidden vector is, and this can be solved by a variational autoencoder. The principle is simple, just adding some restrictions to the encoding process that force the resulting latent vector to roughly follow a standard normal distribution. Therefore, choosing VAE is very convenient for us to generate other drop trajectories since we could get a distribution for latent space. The latent space sampled from the trained model can then generate any desired moving trajectories. 

## Result
The loss function for VAE consists of two parts: one is MSE loss, calculating the distance between true and predicted trajectories; the other is KL divergence, representing the loss of the difference between the latent vector and the standard normal distribution. Combining these two losses, we can train our model very effectively. As shown in picture above, we got a plot of the variation of loss with epoch.
