## List of useful code snippets
* **Feature Columns**: `feature_columns = [tf.feature_column.numeric_column("total_rooms")]`
* **Mini-batch SGD**: `tf.train.GradientDescentOptimizer(learning_rate=0.0000001)`
* **Clip gradients**: `tf.contrib.estimator.clip_gradients_by_norm(my_optimizer, 5.0)` It will change in TensorFlow 2.0.
* **Linear Estimator**: `tf.estimator.LinearRegressor`
* **Input Function**: instructs tf on how to preprocess the data, as well as how to batch, shuffle and repeat it during model training.
Steps involve:
  * converting pandas data into `dict` of np array.
  * Dataset API to construct a dataset object from our data.
  * Break the data into batches of `batch_size`, to be repeated for `num_epochs`
  * Shuffle the data if `shuffle=True` with `buffer_size` specifying the size of dataset from which `shuffle` will randomly sample.
  * Construct an iterator for the dataset and return the next batch of data to the LinearRegressor.

```
def my_input_fn(features, targets, batch_size=1, shuffle=True, num_epochs=None):
    """Trains a linear regression model of one feature.
  
    Args:
      features: pandas DataFrame of features
      targets: pandas DataFrame of targets
      batch_size: Size of batches to be passed to the model
      shuffle: True or False. Whether to shuffle the data.
      num_epochs: Number of epochs for which data should be repeated. None = repeat indefinitely
    Returns:
      Tuple of (features, labels) for next data batch
    """
  
    # Convert pandas data into a dict of np arrays.
    features = {key:np.array(value) for key,value in dict(features).items()}                                           
 
    # Construct a dataset, and configure batching/repeating.
    ds = Dataset.from_tensor_slices((features,targets)) # warning: 2GB limit
    ds = ds.batch(batch_size).repeat(num_epochs)
    
    # Shuffle the data, if specified.
    if shuffle:
      ds = ds.shuffle(buffer_size=10000)
    
    # Return the next batch of data.
    features, labels = ds.make_one_shot_iterator().get_next()
    return features, labels
```
* **Train the model**
```
_ = linear_regressor.train(
    input_fn = lambda:my_input_fn(my_feature, targets),
    steps=100
) 
```
* **Evaluate the model**
```
# Create an input function for predictions.
# Note: Since we're making just one prediction for each example, we don't 
# need to repeat or shuffle the data here.
prediction_input_fn =lambda: my_input_fn(my_feature, targets, num_epochs=1, shuffle=False)

# Call predict() on the linear_regressor to make predictions.
predictions = linear_regressor.predict(input_fn=prediction_input_fn)

# Format predictions as a NumPy array, so we can calculate error metrics.
predictions = np.array([item['predictions'][0] for item in predictions])

# Print Mean Squared Error and Root Mean Squared Error.
mean_squared_error = metrics.mean_squared_error(predictions, targets)
root_mean_squared_error = math.sqrt(mean_squared_error)
print("Mean Squared Error (on training data): %0.3f" % mean_squared_error)
print("Root Mean Squared Error (on training data): %0.3f" % root_mean_squared_error)
```

* **Fix the model**
