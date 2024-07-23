# Implementation of a character-level language model using PyTorch. 
### It builds a model that predicts the next character in a sequence based on the previous characters.

## 1. Data Preparation:

Reads a list of words (likely names) from a text file.
Creates a unique vocabulary of all characters used in the words.
Assigns a unique integer ID to each character.
Builds the dataset by splitting each word into character sequences of a fixed length (block_size).
Splits the data into training, validation, and test sets.

## 2. Model Definition:

Defines custom classes for three types of layers: Linear, BatchNorm1d, and Tanh. These layers perform matrix multiplication, batch normalization (improves training stability), and Tanh activation (non-linearity) respectively.
Sets hyperparameters like embedding size (n_embd), hidden layer size (n_hidden), and the number of hidden layers.
Defines the model architecture using a list of these layers.

## 3. Training Setup:

Initializes embedding matrix (C) which maps characters to embedding vectors.
Creates optimizer parameters including the embedding matrix and all weights/biases in the layers.
Sets up manual backpropagation using additional parameters (W1, b1, W2, b2, etc.) to compare with automatic backpropagation.
Defines training hyperparameters like maximum training steps, batch size, and learning rate schedule (decays over time).

## 4. Training Loop:

Iterates for a specified number of steps.
Within each iteration:
Samples a minibatch of training data (Xb, Yb).
Performs a forward pass through the model layers using both automatic and manual calculations.
Calculates the loss using cross-entropy between predicted and actual character labels.
Updates weights and biases in both automatic and manual backpropagation routines using gradient descent.
Tracks training loss every 10,000 steps.
### Manual backpropagation: 
Implementing the backpropagation algorithm from scratch to compute gradients and update model parameters.

## 5. Evaluation and Sampling:

Calculates the loss on the validation and test sets using the trained model.
Generates random name samples by starting with a sequence of dots (...) and predicting the next character iteratively until a period (.) is generated.

## 6. Additional Functions:

split_loss: This function calculates and prints the loss on a specified dataset split (train, validation, or test).
Overall, this code demonstrates a custom implementation of a character-level language model with manual backpropagation for comparison purposes.

## 7. Loss

### Batch Size: 64
train 2.0156145095825195
val 2.0991787910461426

### Batch Size: 32
train 2.060652017593384
val 2.117051362991333
