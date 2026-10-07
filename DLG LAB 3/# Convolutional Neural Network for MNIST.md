# Convolutional Neural Network for MNIST Digit Classification

## Objective

This project implements a **Convolutional Neural Network (CNN)** using TensorFlow and Keras to classify handwritten digits from the **MNIST dataset**.

The model learns image features using convolutional and pooling layers and classifies each image into one of the 10 digit classes from 0 to 9.

## Dataset

The project uses the **MNIST handwritten digit dataset**.

- Image Size: 28 × 28 pixels
- Number of Classes: 10
- Classes: Digits 0–9
- Training Data: 60,000 images
- Testing Data: 10,000 images
- Image Type: Grayscale

The MNIST dataset is automatically downloaded using TensorFlow Keras.

## Technologies Used

- Python 3
- TensorFlow
- Keras
- Matplotlib

## CNN Architecture

The model uses the following architecture:

```text
Input Image
28 × 28 × 1
     ↓
Conv2D
32 filters, 3 × 3
ReLU
     ↓
MaxPooling2D
2 × 2
     ↓
Conv2D
64 filters, 3 × 3
ReLU
     ↓
MaxPooling2D
2 × 2
     ↓
Conv2D
64 filters, 3 × 3
ReLU
     ↓
Flatten
     ↓
Dense
64 neurons, ReLU
     ↓
Dense
10 neurons, Softmax
```

## Data Preprocessing

The following preprocessing steps are performed:

1. Load the MNIST dataset.
2. Reshape the images to include the channel dimension.
3. Convert the image shape from `28 × 28` to `28 × 28 × 1`.
4. Normalize pixel values by dividing them by `255.0`.

This converts pixel values from the range:

```text
0–255
```

to:

```text
0–1
```

## Convolutional Layers

The model uses three convolutional layers:

```text
Conv2D(32, 3 × 3)
Conv2D(64, 3 × 3)
Conv2D(64, 3 × 3)
```

The convolutional layers extract important features from the handwritten digit images.

ReLU activation is used in the convolutional and dense hidden layers.

## Pooling Layers

Two `MaxPooling2D` layers are used with a pool size of:

```text
2 × 2
```

Pooling reduces the spatial dimensions of the feature maps while retaining important features.

## Output Layer

The final layer contains 10 neurons:

```text
Dense(10, activation='softmax')
```

Each neuron represents one digit:

```text
0 1 2 3 4 5 6 7 8 9
```

Softmax produces the probability of each digit class.

The class with the highest probability is selected as the predicted digit.

## Model Compilation

The model uses:

```text
Optimizer: Adam
Loss Function: Sparse Categorical Cross-Entropy
Metric: Accuracy
```

The model is compiled using:

```python
model.compile(
    optimizer='adam',
    loss='sparse_categorical_crossentropy',
    metrics=['accuracy']
)
```

## Training

The model is trained using:

```text
Epochs: 5
```

Validation data is provided using the test dataset:

```python
validation_data=(test_images, test_labels)
```

## Evaluation

After training, the model is evaluated using the MNIST test dataset.

The program displays:

- Test loss
- Test accuracy

Example:

```text
Test accuracy 0.98
```

The exact accuracy may vary slightly between different runs.

## Visualization

The program generates two graphs.

### Training and Validation Accuracy

This graph shows how the training and validation accuracy change across epochs.

### Training and Validation Loss

This graph shows how the training and validation loss change across epochs.

Both graphs help analyze the training performance of the CNN.

## How to Run

Install the required libraries:

```bash
pip install tensorflow matplotlib
```

Run the program:

```bash
python CNN_MNIST.py
```

The MNIST dataset will be downloaded automatically when the program is executed.

## Project Structure

```text
MNIST-CNN/
│
├── CNN_MNIST.py
└── README.md
```

## Conclusion

This project demonstrates the use of a Convolutional Neural Network for handwritten digit classification. The CNN uses convolution, max pooling, flattening, and fully connected layers to learn features from MNIST images and classify them into 10 digit classes.

The use of ReLU activation, softmax output, Adam optimization, and sparse categorical cross-entropy provides an effective approach for MNIST digit classification.