
1) Explain what data normalization is, and its importance.
> This is one of the basic, yet relevant questions that are usually asked. Data normalization is a pre-processing step. It helps weight all the features that fit in a particular range equally. This prevents any kind of discrepancy when it comes to the cost function of features.

2) Highlight the significance of residual networks.
> Residual networks and their connections are mainly used to facilitate easier propagation through any given network. Thus, residual connections allow you to access certain features present in the previous layers directly. The presence of residual networks helps make the network as more of a multi-path structure. This gives room for features to tread across multiple paths, thus helping with better propagation throughout the system as a whole.

3) Why are convolutions preferred over FC layers for images?
> Though this is technically not a very common question, it is interesting because it tests your skills related to comparison and problem-solving. FC layers have one major disadvantage which is that they have no relative spatial information. On the other hand, convolutions not only use spatial information but also preserves and encodes it. Also, Convolutional Neural Networks (CNN) are said to have a built-in variance which makes each kernel a feature detector on its own.

4) What do you do if you find missing or corrupted data in any dataset?
There are mainly two things that you can do if you find missing or corrupted data in a dataset.

> Drop the respective rows or columns: This can be done by using two method functions, isnull() or dropna(). This will help you determine if any dataset is actually empty. If it is empty, you can simply drop it.
> Replace the data with non-corrupted values: To replace any invalid value with another value, the fillna() method can be used.

5) Why are 3×3 convolutional kernels preferred over larger kernels?
> Smaller kernels such as a 3×3 kernel generally use lesser computations as well as parameters. Thus, you can use several smaller kernels as opposed to a few larger ones. Also, larger kernels do not capture as much spatial content as smaller kernels do. Apart from this, smaller kernels use a lot more filters than larger kernels do. This, in turn, facilitates the use of more activation functions which can be used for discriminative mapping functions.

6) Why does the segmentation of CNN have an encoder-decoder structure?
> The segmentation structure of CNN’s is usually in the encoder-decoder style so that the encoder can extract features from the network while the decoder can decode these features to predict the segments of the image under consideration.

Thus, looking into simple questions like this that focus on your knowledge of the concepts of Data Science and Machine Learning will really help you face an interview while applying for a position in the field.
