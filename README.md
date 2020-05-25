# keras_FM
This is a tensorflow.keras implementation of Factorized Machine(FM)

## Dataset
* The dataset is a Click-Through Rate Prediction dataset provided by Avazu in a Kaggle competition.
* You can find the data [here](https://www.kaggle.com/c/avazu-ctr-prediction)


## Data preprocessing
* 'hour' contains year, month, day, and hour information. Only hour information is kept for training. Thus, this feature can be treated as a catagorical feature(hour = 0, 1, 2, ..., 23).
* All other features are catagorical(discrete), one hot encoding is used on the datset to make it suitable for FM training.

## FMCrossLayer class
* Set the weights(the hidden vectors in FM) in build().
* Define the forward propagatation in call().
* Here is how we simply crossed features: 

![alt text](https://i.ibb.co/mvJ3TLQ/image.png)

## Generate FM model
* Generate input_layer with tf.keras.Input()
* Generate linear_layer with tf.keras.Dense()(input_layer)
* Generate cross_layer with FMCrossLayer()(input_layer)
* Add the output of linear_layer and cross_layer to get the final FM model

## Some settings
* Sigmoid is used as the activation function
* Loss is set to "binary_crossentropy"
* Optimizer is set to tf.optimizers.Adam(learning_rate=0.001)
* Metrics is set to "binary_accuracy"
* The length of hidden vactor in FM is set to 5 by default
