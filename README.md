# ExMatchina
A Deep Neural Network explanation-by-example library for generating meaningful explanations. Used in our [Explainability Study](https://github.com/nesl/Explainability-Study).

## Prerequisites
Install the required Python packages.
```Python
pip3 install -r requirements.txt
```

## Usage
1. Import the ExMatchina class
```Python
from ExMatchina import ExMatchina
```
2. Load ExMatchina with a particular TensorFlow model + example prototypes (e.g. training data)

```Python
# X_train.npy: a numpy array of prototypes
# model: the model of interest
training_data = np.load('./X_train.npy')
model = load_model('./model')
# selected_layer: the layer to use in identifying examples.
# We recommend the layer immediately following the last convolution (e.g. flatten layer)
selected_layer = "Flatten_1"

exm = ExMatchina(model=model, layer=selected_layer, examples=training_data)
```

3. Fetch examples and corresponding indices for a given input

```Python
test_data = np.load('./X_test.npy')
test_input = test_data[0]
(examples, indices) = exm.return_nearest_examples(test_input)
```
