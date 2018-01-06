# NsfwSqueezenet
Caffe Squeezenet model for binary classification of pornographic/non-pornographic material

The model has a single output, which consists of float values indicating the probability of the input belonging to one of two classes, ranging from 0.0 to 1.0. The first class, 0, is non-pornography, and the second class, 1, is pornography. Therefore, you can simply take the second index of the output (class 1 probability) as your result.

This project was inspired by [Open NSFW](https://github.com/yahoo/open_nsfw). Open NSFW has excellent accuracy but is computationally expensive. While we don't quite meet the accuracy of OpenNSFW, we get ~3X the execution speed in the network forward pass. As such, using OpenCV DNN with the CPU target on an i7-6700 at 3.4 Ghz, we get results like:

```
Classified pornographic images with an accuracy of 97.6086956521739%.
Classified non-pornographic images with an accuracy of 98.4782608695652%.
Took an average of 12.0554347826087 msec per image to classify.
```

Note that the average execution time above includes JPEG decoding time, as well as network input preprocessing time. This is not a measurement of just the forward pass execution time. Those benchmarks (forward pass only) are well [established](https://github.com/opencv/opencv/wiki/DNN-Efficiency).

This model is sufficient enough for real time video classification on a single core at ~3.5x playback speed (cinema framerate).

## Todo

Right now this model performs very well with pornographic imagery, but doesn't perform quite as well with plain nudity. The model can benefit from adding plain nudity, devoid of sexual actions, to the training input.

### Notice  
Everything except the file `nsfw_squeezenet.caffemodel` is a derivative of [SqueezeNet 1.1](https://github.com/DeepScale/SqueezeNet/tree/master/SqueezeNet_v1.1) and thus is under the original [copyright holder's license](https://github.com/DeepScale/SqueezeNet/blob/master/LICENSE), the BSD 2-clause license.

`nsfw_squeezenet.caffemodel` is licensed under the Mozilla Public License v2.
