# deep-learning-challenge

### Overview
The goal of this project was to build and improve a deep learning model that could predict whether applicants to Alphabet Soup’s funding program would be successful. By analyzing the application data, I looked for patterns that might help the organization make better decisions about which applicants to support.

To complete this project, I cleaned and preprocessed the dataset, then built and trained several neural network models to see what worked best. I applied optimization techniques such as hyperparameter tuning, testing different activation functions, and experimented with adding and removing features to improve the model’s performance. In the end, I evaluated the final model against a target accuracy of 75% to see how well it could predict application success.

### Data Preprocessing
- **Target:** `IS_SUCCESSFUL` 
- **Features:** `APPLICATION_TYPE`,	`AFFILIATION`, `CLASSIFICATION`, `USE_CASE`, `ORGANIZATION`, `STATUS`, `INCOME_AMT`, `SPECIAL_CONSIDERATIONS`, `ASK_AMT`	
- **Dropped:** `EIN`, `NAME` (only in initial model and test)

### Compiling, Training, and Evaluating the Model
- **Layers:** 5 hidden layers and 1 output layer
- **Neurons:** 65, 60, 28, 44, 36 neurons for the hidden layers; 1 neuron in the output layer
- **Activations:** 
    - **Test 1:** Used `keras_tuner` to test activation functions (`relu` vs `selu`) and determine the best layer and neuron configuration. `relue` was selected as the best performing activiation.
     - **Test 2:** Built a model with all hidden layers using `relu` and output layer using `sigmoid`.
     - **Test 3:** Replaced all `relu` activations with `LeakyReLU`.
     - **Performance:**  The best performing model used `LeakyReLU` in the hidden layers and `sigmoid` in the output layer,  achieving a performance of **79% accuracy** and the lowest **loss of 0.47**. This model exceeded the target model performance of 75%, demonstrating strong predictive accuracy and generalization. 

### Model Comparison:

| Model       | Key Changes Tested                                 | Accuracy | Loss |
|---------------|----------------------------------------------------|----------|------|
| # 1        | Tuned layers, neurons, and activation using `keras_tuner` (`relu` vs. `selu`) | 73%  | 0.55 |
| # 2        | Added `NAME` feature and used optimized layers, neurons, and `relu` activation | 79% | 0.50 |
| # 3 **(Best)** | Replaced `relu` with `LeakyReLU` in all hidden layers | **79%** | **0.47** |

### Summary
After testing three neural network models with different configurations, the final model using `LeakyReLU` activation in the hidden layers achieved the best results with **79% accuracy** and the lowest loss of **0.47**. This exceeded the target model performance of 75%, indicating that the deep learning approach was effective.

That said, since the dataset is made up of structured, tabular data with a mix of numeric and categorical features, I think it would be worth trying a different type of model next time. A **Random Forest** or **Gradient Boosting model** (like XGBoost) might be a better fit. These models usually handle this kind of data well, are easier to set up, and don’t require as much tuning. They could potentially train faster, offer better insights into which features matter most, and possibly improve accuracy even more.
