# Neural_Network_Charity_Analysis
Use neural network to create a binary classifier that is capable of predicting applicant success if funded.



# Ending Results:

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

4. Optimizing Attempt:

    *    **Results:** 

5. Optimizing Attempt:

    *    **Results:** 