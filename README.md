# deep-learning-challenge

### Overview
The goal of this project was to develop and optimize a deep learning model to predict 

Results:
### Data Preprocessing
- **Target:** `IS_SUCCESSFUL` 
- **Features:** All other variables after preprocessing
- **Dropped:** `EIN`, `NAME` (only in initial model and test)

### Compiling, Training, and Evaluating the Model
- **Layers:** 5 hidden layers and 1 output layer
- **Neurons:** 65, 60, 28, 44, 36 neurons for the hidden layers; 1 neuron in the output layer
- **Activations:** 
    - **Test 1:** Used `keras_tuner` to test activation functions (`relu` vs `selu`) and determine the best layer and neuron configuration. `relue` was selected as the best performing activiation.
     - **Test 2:** Built a model with all hidden layers using `relu` and output layer using `sigmoid`.
     - **Test 3:** Replaced all `relu` activations with `LeakyReLU`.
- **Performance:**  The best performing model used `LeakyReLU` in the hidden layers and `sigmoid` in the output layer,  achieving a performance of 79% accuracy and the lowest loss of 47%. This model exceeded the target model performance of 75%, demonstrating strong predictive accuracy and generalization. 


