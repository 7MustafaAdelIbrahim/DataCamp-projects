## Project Description
American Sign Language (ASL) is the primary language used by many deaf individuals in North America, and it is also used by hard-of-hearing and hearing individuals.
The language is as rich as spoken languages and employs signs made with the hand, along with facial gestures and bodily postures.
In this project, you will train a convolutional neural network to classify images of ASL letters. After loading, examining, and preprocessing the data, you will train the network and test its performance.

American Sign Language (ASL) is the primary language used by many deaf individuals in North America, and it is also used by hard-of-hearing and hearing individuals. The language is as rich as spoken languages and employs signs made with the hand, along with facial gestures and bodily postures.

american sign language
![asl](https://user-images.githubusercontent.com/84151016/155030004-9bdaeffc-aec5-41c1-84a3-dd8b11345fde.png)


A lot of recent progress has been made towards developing computer vision systems that translate sign language to spoken language. This technology often relies on complex neural network architectures that can detect subtle patterns in streaming video. However, as a first step, towards understanding how to build a translation system, we can reduce the size of the problem by translating individual letters, instead of sentences.

In this notebook, we will train a convolutional neural network to classify images of American Sign Language (ASL) letters. After loading, examining, and preprocessing the data, we will train the network and test its performance.



#### Good to know
This project lets you practice the skills from Introduction to Deep Learning in Python and Image Processing with Keras in Python, including building convolutional neural networks to classify images. We recommend that you take those courses before starting this project.

## Project Tasks
#### 1. American Sign Language (ASL)

#### 2. Visualize the training data

Now we'll begin by creating a list of string-valued labels containing the letters that appear in the dataset. Then, we visualize the first several images in the training data, along with their corresponding labels.
![download](https://user-images.githubusercontent.com/84151016/155030106-36b4ebac-d41e-4e32-b1a5-85aff0689f0f.png)

#### 3. Examine the dataset

#### 4. One-hot encode the data

Currently, our labels for each of the letters are encoded as categorical integers, where 'A', 'B' and 'C' are encoded as 0, 1, and 2, respectively.
However, recall that Keras models do not accept labels in this format, and we must first one-hot encode the labels before supplying them to a Keras model.
This conversion will turn the one-dimensional array of labels into a two-dimensional array.

<img width="360" alt="onehot" src="https://user-images.githubusercontent.com/84151016/155030197-69780556-d9c7-486c-9e7d-55b6bb08a828.png">

Each row in the two-dimensional array of one-hot encoded labels corresponds to a different image. The row has a 1 in the column that corresponds to the correct label, and 0 elsewhere.
For instance,
0 is encoded as [1, 0, 0],
1 is encoded as [0, 1, 0], and
2 is encoded as [0, 0, 1].

#### 5. Define the model

Now it's time to define a convolutional neural network to classify the data.

This network accepts an image of an American Sign Language letter as input. The output layer returns the network's predicted probabilities that the image belongs in each category.

#### 6. Compile the model

After we have defined a neural network in Keras, the next step is to compile it!

#### 7. Train the model

Once we have compiled the model, we're ready to fit it to the training data.

#### 8. Test the model

To evaluate the model, we'll use the test dataset. This will tell us how the network performs when classifying images it has never seen before!
If the classification accuracy on the test dataset is similar to the training dataset, this is a good sign that the model did not overfit to the training data.

#### 9. Visualize mistakes

Hooray! Our network gets very high accuracy on the test set!
The final step is to take a look at the images that were incorrectly classified by the model.
Do any of the mislabeled images look relatively difficult to classify, even to the human eye?
Sometimes, it's possible to review the images to discover special characteristics that are confusing to the model. However, it is also often the case that it's hard to interpret what the model had in mind!

![download](https://user-images.githubusercontent.com/84151016/155030539-903a4899-423a-4c6b-ae6a-659d9d06efb8.png)

