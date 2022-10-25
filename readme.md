# Neural_Network_Charity_Analysis
Use neural network to create a binary classifier that is capable of predicting applicant success if funded.


# Build The Neural Network Model

The model will start with 3 hidden layers and one known output layer. After some testing of the model, making adjustments 

The nodes on the hidden layers will be based on the number of inputs and all use the "tanh" activation equation.

*   Hidden Layer one: input*1.25
*   Hidden Layer two: input*1.75
*   Hidden Layer three: input/2

The goal at this point is to be at or above 75% accuracy, the model at this point provides 72.87% accuracy with the testing data. This will be attempted in a seperate ipynb notebook.



# Optimzation Results:

**Optimizing Attempt 1:** the model will be to use the Keras Tuner to find the best number of hidden layers and neurons.
*    Minimum number of hidden layers: 2
*    Maximum number of hidden layers: 6  
*    Minimum number of neurons per layer: 1
*    Maximum number of neurons per layer: input_dims * 1.75 
*    Test the top 3 models the Keras Tuner finds and train them again with 500 epochs before evaluating them with the test data.

**Optimizing Attempt 1:** the model will be to use the Keras Tuner to find the best number of hidden layers and neurons.
*    Minimum number of hidden layers: 2
*    Maximum number of hidden layers: 6  
*    Minimum number of neurons per layer: 1
*    Maximum number of neurons per layer: input_dims * 1.75 
*    Test the top 3 models the Keras Tuner finds and train them again with 500 epochs before evaluating them with the test data.

*  **Results:** This attempt boils down to changing the number of hidden layers and number of neurons within the model and using only one activation equation within the hidden layers. The Keras Tuner tested 180 different models, I chose the top 3 best performing ones and retrained them with 500 epochs. The results from those 3 models did not meet the required accuracy goal with the testing data.   

**Optimizing Attempt 2:** Run the same Keras Tuner with one change, allow it to pick multiple activation equations for the hidden layers every time it builds a new model. The Keras Tuner summary will only be able to show one of the activation equations for each model, not all of the ones contained within. The one activation equation for the most recently created hidden layer will be displayed.

*    **Results:** Ending results for the top 3 models of both Keras Tuners were very similar.  Having multiple activation equations in the hidden layers did not seem to help improve the model.

**Optimizing Attempt 3:** use the encoded_df instead of the std_scaled_df because only 1 of the 47 columns is not a true/false numerical value. Keep ASK_AMT column scaled with the standard scaler because it is not a true/false statement.    
    
*    **Results:** Ending results for the encoded True/False data did not do as well as the scaled version of the data. A range of 68% to 63% for the top Three instead of the ballpark 72% from the previous 2 attempts. The **Rabbit Hole** ending results are even worse without the ASK_AMT scaled. This did not work.

**Optimizing Attempt 4:** Add features, EIN and NAME columns to the X features, However i will add them seperately because they both have the same meaning as unique identifier columns. There will be 2 data sets, X_ein and X_name. 
*    **X_ein Results:** 
*    **X_name Results:**
        *   I do not have high hopes for the name column because it is not numbers, but I want to see the results.
