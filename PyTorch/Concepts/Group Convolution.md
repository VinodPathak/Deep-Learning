## How groups work in PyTorch convolutions

![Group Convolution](https://user-images.githubusercontent.com/22738317/32132612-f5294242-bbc6-11e7-9406-3419a2e504cf.png)

- https://mc.ai/how-groups-work-in-pytorch-convolutions/

### Groups
If you look, by default the group parameter is set to 1. This means, according to the docs:

At groups=1, all inputs are convolved to all outputs.

That’s exactly what we saw in the formula above! Again, further in the docs we observe:

At groups=2, the operation becomes equivalent to having two conv layers side by side, each seeing half the input channels, and producing half the output channels, and both subsequently concatenated.

Let’s formalize this. First of all, we need to be able to split number of input channels in two, aka input channels must be an even number. Then, PyTorch creates weights W1 and W2 for each half of the new input. These groups of weights now output exactly half of the desired number of output channels, meaning that the number of channels must be divisible by 2. The weights take half the input channels. Then the formulas above are applied to each group (which now consists of two inputs and two sets of weights), the result of both convolutions is concatenated to produce the output of the desired shape.

So, for k groups in the setting of Conv2d, we must ensure that the number of input channels and the number of output channels are both divisible by k.

Say you want to take (1, 3, 64, 64) input image (tensor) and produce (1, 9, 64, 64) output tensor. You can have at most 3 groups (since 9mod3 = 0, 3mod3=0) in this situation and each channel will be convolved with 9/3=3 filters.

So, if you have (N, M, H, W) input shape where N is the batch size and M is the number of input channels, and you want to produce (N, L, H’, W’) output, the maximum number of groups you can have the Greatest Common Divisor of these two numbers.

### Conclusion
Groups can be a useful feature, especially in models where each channel needs to be processed differently. If some input channels carry different information from others, then we might want to make the model learn to extract this relevant information channel-wise in the early layers. Hence, the groups parameter becomes really handy. It saves a great deal of time instead of processing each individual channel one by one.
