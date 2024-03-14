# Neural Network Review

# Overview
    The purpose of this analysis is to create a model that can assist the foundation Alphabet Soup in predicting which funding applications are most likely to succeed.

# Results 
    Data Preprocessing
    -The target variable of the model is "IS_SUCCESSFUL". This column ultimately indicates whether an organization's investment was successful or not. The code snippet below demonstrates where this target variable is implemented:
            y = application_df_encoded["IS_SUCCESSFUL"].values

    -The feature variables of the model include all columns except for "IS_SUCCESSFUL". This line of code demonstrates how this exclusion is implemented:
            X = application_df_encoded.drop(columns=["IS_SUCCESSFUL"]).values

            (List of features)
            APPLICATION_TYPE            17
            AFFILIATION                  6
            CLASSIFICATION              71
            USE_CASE                     5
            ORGANIZATION                 4
            STATUS                       2
            INCOME_AMT                   9
            SPECIAL_CONSIDERATIONS       2
            ASK_AMT                   8747
            dtype: int64
        
    -The variables "EIN" and "NAME" were removed from the dataset as they did not provide information that would determine the success of an organization. The following code snippet demonstrates where this action was taken:
             application_df.drop(columns=['EIN', 'NAME'], inplace=True)
            
    Compiling, Training and Evalualting the Model
    -80 neurons were selected for all three layers in my model. Additionally, the activation function 'relu' was chosen. This activation function proved successful in increasing the accuracy of the model. It facilitated rapid learning and effectively handled the binary (0 and 1) results found in the target variable. The combination of 80 neurons and three layers demonstrated the most success in improving model performance.

    -I was not able to achieve the target model performance of 75%. The highest performance observed was 74%.

    -Here are the steps taken to attempt to increase accuracy above 75%:
        -Increased the number of layers from 2 to 3. Testing with 4 layers resulted in decreased accuracy.
        -Increased the number of neurons in layers 2 and 3 to 80. Lower values did not improve accuracy.
        -Adjusted the number of epochs, ranging from 200 to 350, and settled on 350 for the final model.
        -Lowered the cutoff value for classification, which contributed to increased accuracy.
        -Tested various activation functions including TanH, Linear, etc., but found ReLU to be the most successful.

# Summary
    Overall, increasing the number of layers, neurons, epochs, and lowering the cutoff value improved the accuracy of the model. However, these adjustments were insufficient to reach the specified target accuracy. A recommended alternative model could be Long Short-Term Memory (LSTM). LSTMs are designed to address the issue of vanishing gradients, which appears to be a challenge in this scenario.