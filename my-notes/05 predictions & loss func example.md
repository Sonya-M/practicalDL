- simple example of training process using loss func as measurement of prediction accuracy to adjust weights and biases: see notebook `linear-regression-example.ipynb` (workspace/practicalDL)
- first we create mock data - assume mock data is our input, result of an actual measurement (e.g. correlation between height (X) and shoe-size (Y)), and that we don't know weight and bias, and we are trying to get to the ideal w and b values thru training:
```python
# create mock data
# using tf.random to add some noise to data
def data_creation(w=0.1, b=0.5, n=100):
    X = tf.random.uniform(shape=[n]) # input data
    noise = tf.random.normal(shape=[n], mean=0.0, stddev=0.01)
    Y = X*w+b+noise. # the actual data with noise
    return X.numpy(), Y.numpy() # convert X and Y from tf representation to regular array 
```
- find the error value - how far our predictions are from actual data: **loss func**:
	- can simply measure distance btw prediction line points and actual values, e.g. avg(square of diff btw each point)
```python
def predict(x, w, b):
    y = x * w + b
    return y

# calculated how far we are from the solution, our loss func
def mean_squared_error(y_predictions, Y):
    return tf.reduce_mean(tf.square(Y - y_predictions)) # calculate mean for all given args
```
-  to _minimize loss_ and get close to ideal w and b, we use **differentiation** in the process of back-propagation:
	- differentiation tell us how to change w and b to decrease the loss
	- derivatives tell us which way to go, but we want to go there slowly, so we multiply by our learning rate (see below)
	- `tensorflow` can calculate all derivatives in a single method using gradient tape:
```python
w = tf.Variable(0.0)
b = tf.Variable(-1.0)

learning_rate = 0.1 

steps = 200 # n steps to get to solution

for step in range(steps):
    # creating an environment in which tf is keeping track of arithmetical operations within this code block
    with tf.GradientTape() as tape:
        predictions = predict(X, w=w, b=b  )
        loss = mean_squared_error(predictions, Y)

    # get gradient(s), direction in which you want to modify value/values to get to minimum loss
    # second arg is a list of vals we want to modify, returns an array of gradients, one for each elem in that list
    gradients = tape.gradient(loss, [w, b]) 
    w.assign_sub(gradients[0] * learning_rate) # subtract given arg from w
    b.assign_sub(gradients[1] * learning_rate)

```

- small learning rate to avoid overshooting: ![[loss-overshoot.png]]
-  we slowly near the minimum, and end up jumping back and forth around it:
![[jumping-around-minimum-loss.png]]
- a common trick is to decrease the learning rate as we get close to it
- we never get to the exact solution, but we get close enough

- learning rate and n steps are **hyper-parameters** - control how we train the model
- too small learning rate - might need more steps to get to minimum loss
- too large learning rate - we jump out of the minimum

###  Summary
- loss func as measurement of prediction accuracy:
- if the input is an img of hotdog, and the output is "not hotdog" - loss func returns a big value;
- then we can calculate derivatives of loss for all weights/biases in NN,  so as to figure out how to modify those weights/biases in order to get to the correct answer;
- for **neural networks** it's essentially the same alg on a much larger scale, principle is the same:
	- provide input data and expected output;
	- then keep track of what is happening and calculate how ws and bs should be tweaked  to get to correct result with a similar input  