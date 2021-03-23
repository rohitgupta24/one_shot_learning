# one_shot_learning

Hands-On for Siamese Network.


One Shot Learning : Humans learn new concepts with very little supervision. This principle behind one-shot learning is what we need to recreate in our model. Hence, we use a siamese network, which does not require extensive training samples for recognition tasks.

One Shot Learning Problem has various solution like :

1. Siamese network for one-shot learning:

In particular, what we want is a neural network to learn a function(d) that takes input two images—one being the actual image and other the candidate image—and outputs the similarity between the two.


The two input images, if very similar, should output a lower value, and vice-versa. When a prediction is made, if the degree of difference between the two images is less than a threshold value(𝜏) (which is a hyperparameter), the prediction states that the input two images are of the same person. And if it’s greater than 𝜏, the prediction states the image is of two different people.



Both the images to be compared are passed through the same networks, called sister networks, having the same parameters and shared weights.
Specifically, the images are passed through a sequence of convolutional, pooling, and fully connected layers, and end up with a feature vector of a fixed size, say, 128 denoted by f(x1) as an encoding of the input image x1.

The distance between x1 and x2 is the norm of the difference d between the encodings of these two images. So more formally, what we want to do is learn parameters of this network so that if two pictures (xi and xj) are of the same person, then the distance between their encodings is small.




2. Triplet loss integration:

For triplet loss, we need to compare pairs of images and learn the parameters of the neural network accordingly. To do this, we look at one “anchor” image and get the distance between it and the “positive” (matching) image. Similarly, we get the distance of the anchor image with a “negative” (non-matching) example as well. The anchor image and the negative image should be further apart.

We want the parameters of neural network to be such that the encoding between the anchor minus the encoding of the positive example is small—and in particular, less than or equal to the distance of the squared norm between the encoding of the anchor and the encoding of the negative example.