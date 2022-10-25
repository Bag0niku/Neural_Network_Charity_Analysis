# Neural_Network_Charity_Analysis
Use neural network to create a binary classifier that is capable of predicting applicant success if funded.

## Data
- data/charity data.csv


## Build The Neural Network Model

The model will start with 3 hidden layers and one known output layer. After some testing of the model, making adjustments 

The nodes on the hidden layers will be based on the number of inputs and all use the "tanh" activation equation.

*   Hidden Layer one: input*1.25
*   Hidden Layer two: input*1.75
*   Hidden Layer three: input/2

The goal at this point is to be at or above 75% accuracy, the model at this point provides 72% accuracy with the testing data. This will be attempted in a seperate ipynb notebook.

## Optimzation Results:

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
    
*    **Results:** Ending results for the encoded True/False data did not do as well as the scaled version of the data. A range of 68% to 63% for the top Three instead of the ballpark 72% from the previous 2 attempts. The **Rabbit Hole** ending results are even worse without the ASK_AMT scaled. This did not work and proves that the scaling is beneficial to the model.

**Optimizing Attempt 4:** Add features, EIN and NAME columns to the X features, However i will add them seperately because they both have the same meaning as unique identifier columns. There will be 2 data sets, X_ein and X_name. 
*    **X_ein Results:** Slightly better results than the first 2 optimized models, just above 73% instead of the varying 72.X%.
*    **X_name Results:** These models reach and pass the goal of 75%. name_model_1 is the best with a 77.06% accuracy rating. 
    

## Final Model Rankings: 
(ranked first by Accuracy then by Loss)

1. **Name Model Number 1** =>  Loss: 60.55%, Accuracy: 77.06%
2. Name Model Number 2 =>  Loss: 72.37%, Accuracy: 76.75%
3. Name Model Number 0 =>  Loss: 62.25%, Accuracy: 75.97%
4. EIN Model Number 0 =>  Loss: 82%, Accuracy: 73.41%
5. EIN Model Number 1 =>  Loss: 62.14%, Accuracy: 73.18%
6. First Model Number 2 =>  Loss:64.70%, Accuracy: 72.92%
7. Original Model => Loss: 0.56.09%, Accuracy: 72.87%
8. Multi Model Number 0 =>  Loss: 62.98%, Accuracy: 72.80%
9. First Model Number 1 =>  Loss: 57.44%, Accuracy: 72.76%
10. EIN Model Number 2 =>  Loss: 85.59%, Accuracy: 72.69%
11. First Model Number 0 =>  Loss: 57.94%, Accuracy: 72.68%
12. Multi Model Number 2 =>  Loss: 70.04%, Accuracy: 72.66%
13. Multi Model Number 1 =>  Loss: 67.24%, Accuracy: 72.60%
14. Encoded_1 Model Number 2 =>  Loss: 60.15%, Accuracy: 71.40%
15. Encoded_1 Model Number 1 =>  Loss: 61.50%, Accuracy: 67.16%
16. Encoded_1 Model Number 0 =>  Loss: 63.48%, Accuracy: 65.37%
17. Encoded_2 Model Number 2 =>  Loss: 1615230.625%, Accuracy: 53.36%
18. Encoded_2 Model Number 1 =>  Loss: 161730.0%, Accuracy: 53.36%
19. Encoded_2 Model Number 0 =>  Loss: 118593.0%, Accuracy: 46.63%

## Next Steps and things to pondor:
- Why were the "name" models better than "ein" models by 3%? That is a large gap for improvement based on what I have seen so far. Both columns are unique id columns, so why....?
- With better processing resources I would increase the epocs during the Keras Tuner Optimization search to 500 epochs (instead of the 50 that was used) for the following models: First, Multi, EIN and NAME. I want to see how much they improve given more resources and time.
