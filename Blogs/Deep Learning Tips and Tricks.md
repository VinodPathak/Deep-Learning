### https://towardsdatascience.com/deep-learning-tips-and-tricks-1ef708ec5f53

## Deep Learning Techniques  
Here are a few ways you can improve your fit time and accuracy with pre-trained models:

1. Research the ideal pre-trained architecture: Learn about the benefits of transfer learning, or browse some powerful CNN architectures. 2 Consider domains that may not seem like obvious fits, but share potential latent features.
2. Use a smaller learning rate: Since pre-trained weights are usually better than randomly initialized weights, modify more delicately! Your choice here depends on the learning landscape and how well the pre-training went, but check errors across epochs for an idea of how close you are to convergence.
3. Play with dropout: As with Ridge and LASSO regularization for regression models, there is no optimized alpha or dropout for all models. It’s a hyper-parameter that depends on your specific problem, and must be tested. Start with bigger changes — a wider gridsearch span across orders of magnitude, like np.logspace() can provide— then drop down as with the learning rate above.
4. Limit weight sizes: We can limit the max norm (absolute value) of the weights for certain layers in order to generalize our model
5. Don’t touch the first layers: The first hidden layers of a neural network tend to capture universal and interpretable features, like shapes, curves, or interactions that are very often relevant across domains. We should often leave these alone, and focus on optimizing the meta² latent level further back. This may mean adding hidden layers so we don’t rush the process!
6. Modify the output layer: Replace model defaults with a new activation function and output size that is appropriate for your domain. However, don’t limit yourself to the most obvious solution. While MNIST may seem like it wants 10 output classes, some numbers have common variations, and allowing for 12–16 classes may allow better settling of these variants and improved model performance! As with the tip above, deep learning models should be increasingly modified and tailored as we near output.  

### Dropout Best Practices:
1. Use small dropouts of 20–50%, with 20% recommended for inputs. Too low and you have negligible effects; too high and you underfit.
2. Use dropout on the input layer as well as hidden layers. This has been proven to improve deep learning performance.
3. Use a large learning rate with decay, and large momentum.
4. Constrain your weights! A big learning rate can result in exploding gradients. Imposing a constraint on network weight — such as max-norm regularization with a size of 5 — has been shown to improve results.
5. Use a larger network. You are likely to get better performance when dropout is used on a larger network, giving the model more of an opportunity to learn independent representations.
