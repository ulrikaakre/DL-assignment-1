# ST456 Assignment 1 - Provisional feedback and marks

## Questions

### P1-1
Ok, but the dimension of the summation layer output is wrong. It gives 1, but should be lat_dim (codomain of phi and domain of rho should be the same). Axis is wrong.
I think there are two Dense(1) layers at the end, but you should only have 1. Also, I don't think you need the concatenate. They are already "concatenated" here:

- model_Φ_output = model1(lat_dim)(combined_model_input)
- model_ρ_output = model2(lat_dim)(model_Φ_output)

It seems that concatenate works with concatenating inputs, which is not what we want here. In fact, the arrows in the picture suggest that something is not as we expect (arrow between O and concatenate).

### P1-2
As you say, this is counterintuitive cause we would expect higher lat_dim to be more flexible and fit better. The weird behaviour might be caused by the architecture you implemented.

### P1-3
Consistent reasoning.

### P1-4
It is true that sigmoid is used for the output layer of classifications, but it can also be included in regression hidden layers! Plus, the test set of this experiment has values in [0,1], which is ok if we were to use sigmoid on the output layer.
Also, the sigmoid does not have a binary behaviour, as it outputs probabilities!
There is something about the nature of the sigmoid that leads to the problem of vanishing gradients...

### P1-5
The question asked for the best model within each training run. Note that each epoch of a training run yields a model (a configuration of weights and biases), therefore you where asked to select the configuration with the lowest validation MSE. This can be achieved with the checkout option. You automatically selected the configuration attached to the last epoch, but that in principle might not be the best.
I believe the counterintuitive behaviour of the graph is related to your architecture and what is described in P1.2

### P2-1
Good attempt to define the model based on `tf.keras.layers.Conv1D` and other layers. Good rationale behind the use of MaxPooling to summarise channels, although you need to ensure this is not restricting your model.

### P2-2
Correct training given the architecture. Discussion of results is good but the figure is missing, so there is no way of visualising/comparing all models regarding time to convergence and influence of L,w combinations over the loss function. We expect some stability regardless L=2 or l=3, but some models may overfit for L=3 and larger w.

## Mark

| Total | 100 | 67 |
