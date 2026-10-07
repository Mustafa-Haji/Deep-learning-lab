# Deep Feed-Forward Neural Network for Multi-Class Classification

## Objective

This project implements a **Deep Feed-Forward Neural Network (DFNN)** for multi-class classification using the **Covertype (Forest Cover Type) dataset**.

The main objectives are to understand forward propagation, softmax output activation, categorical cross-entropy loss, backpropagation, class weighting, and evaluation of multi-class classification performance.

## Dataset

The project uses the **Covertype Dataset**.

- Samples: 581,012
- Features: 54
- Classes: 7
- Domain: Forest cover type classification
- Problem Type: Multi-Class Classification

The seven forest cover classes are:

1. Spruce/Fir
2. Lodgepole Pine
3. Ponderosa Pine
4. Cottonwood/Willow
5. Aspen
6. Douglas-fir
7. Krummholz

The dataset has significant class imbalance, with an approximate ratio of 100:1 between the most and least frequent classes.

## Technologies Used

- Python 3
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

## Neural Network Architecture

The DFNN uses the following architecture:

```text
Input Layer
54 neurons
     ↓
Hidden Layer 1
64 neurons - ReLU
     ↓
Hidden Layer 2
32 neurons - ReLU
     ↓
Hidden Layer 3
16 neurons - ReLU
     ↓
Output Layer
7 neurons - Softmax
```

Architecture:

```text
54 → 64 → 32 → 16 → 7
```

The architecture follows the specification given in the assignment PDF.

## Data Preprocessing

The following preprocessing steps are performed:

1. Load the Covertype dataset.
2. Extract the 54 input features.
3. Convert target classes from 1–7 to 0–6.
4. One-hot encode the target.
5. Split the data into:
   - 80% Training
   - 10% Validation
   - 10% Testing
6. Use stratified splitting to preserve class proportions.
7. Standardize the input features using `StandardScaler`.

These preprocessing steps follow the workflow specified in the PDF.

## Class Imbalance

Since the dataset contains significant class imbalance, class weights are calculated using:

```text
wc = N / (K × nc)
```

where:

- `N` = total number of training samples
- `K` = number of classes
- `nc` = number of samples belonging to class `c`

Class weighting gives greater importance to minority classes during training.

## Activation Functions

### ReLU

ReLU is used in all hidden layers.

```text
ReLU(z) = max(0, z)
```

### Softmax

Softmax is used in the output layer to generate probabilities for the seven classes.

The output probabilities sum to 1, allowing the outputs to be interpreted as class probabilities.

## Loss Function

The model uses **Weighted Categorical Cross-Entropy** to handle class imbalance.

The class weight corresponding to the actual class of each training sample is applied to its loss.

## Training

The model uses:

- Mini-batch Stochastic Gradient Descent
- Batch size: 128
- Learning rate: 0.01
- He initialization
- Backpropagation
- Early stopping
- Validation loss monitoring

Early stopping is applied when the validation loss does not improve for 15 epochs.

## Evaluation Metrics

The trained model is evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Macro Precision
- Macro Recall
- Macro F1-score
- Confusion Matrix

The project also generates:

- Training and validation loss curves
- Training and validation accuracy curves
- Per-class F1-score plot
- True vs predicted class distribution
- Precision vs recall plot
- 7 × 7 confusion matrix

These evaluation methods are specified in the assignment requirements.

## Expected Results

The PDF reports approximately:

- Test Accuracy: **70–75%**
- Macro F1-score: **0.65–0.70**
- Training convergence: approximately **40–50 epochs**

The exact results may vary depending on initialization and training conditions.

## How to Run

Install the required libraries:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
```

Run the