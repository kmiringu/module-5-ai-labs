I Built by hand in Numpy:

- Initialization- starting with random guess weights to break the symmetry.
- forward pass - computes the networks current guess.
- Loss - found one number by calculating the Mean Squared Error between the output and target.
- Backpropagation - mathematically routed gradients to travel backwards two layers.

By following this chain-rule theory process;

-   Output layer got blamed first
-   Walked the blame backwards to the hidden layer.
-   Every weight steps opposite its gradient from their blame
-   Repeated the process 10,000 times.


so that the Pytorch framework training loops are a convenience - not a mystery. 
When training fails, I know which gear to check under the hood.