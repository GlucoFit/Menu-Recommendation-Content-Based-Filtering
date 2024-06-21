# Menu-Recommendation-Content-Based-Filtering

# Deep Learning Content Based Filtering

Building Menu Recommendation System with Content Based Filtering with Deep Learning by TensorFlow. This notebook provide preprocessing data, training model, post processing and testing the model output to recommending menu based on user input in self assessment content.

**Notebook Preparation**

The notebook that used in the code in this repo is from kaggle

We will use numpy and pandas library to preprocessing purpose (colect, read, and cleaning data), then we also use sickit-learn library for preprocess and postprocess the data too before train the model. Then we use tensorflow to build model, training the model, and save the model.

**Cleaning Dataset**

The next thing that we do is to check and cleaning the dataset (checking null input, or duplicate input in dataset), for best training model purpose (avoid overfitting or underfitting)

To check missing value in data, we can use 
> menu_df.isna().sum()

Then, tips if there is missing value in your data, to simplify the process cleaning and for optimize model training process we can overwrite the missing value with the dominan trend of the data. This is example function if we want to overwrite the missing value
> menu_df.fillna(value="input_data", inplace=True)

**Preparation Data for Training**

First we will get the variable that we want to match and train from menu and user. Then we encode the input variable ,with OneHotEncoder, to be float format, and scaling the encoded variable with StandardScaler. Next the input and target data will be splited to train and test data to training process.

**Training Model**

Training model will use tensorflow with custom model. From tensorflow library we use model, early stopping(callback), Dense, Dropout, regulizer, and Adam optimizer for optimizing the training model.

We will use menu and user as diferent input in the neural network which have independent layer. Then each input will be merged with concatenate process to match each input, so we can get the compatibility of each input that play important role in this recommendation system. Then we can start train the model with model.compile, and model.fit.

In model we use Dropout, BatchNormalitation, and kernel_regularizer to avoid overfitting. Than we use optimizer Adam to get the maksimum accuracy, because adam can iterating close range loss fucntion.

We also use earlystoping to build automation stop for the stopping in the best epoch training condition.
> early_stopping = EarlyStopping(monitor='val_accuracy', patience=50, restore_best_weights=True)

**Testing Model**

In this process, we will repeat the preprocessing step for new input variabel from user (encode the input with OneHotEncoding, then scaling the encode input with StandardScaler

**Generate Recommendation**

From the new input and the post processing above, we will generate the recommendation model to outputing the best compatibility score of the menu and user input from the model variabel
