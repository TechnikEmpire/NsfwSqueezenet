# NsfwSqueezenet
Caffe Squeezenet model for binary classification of pornographic/non-pornographic material

The model has a single output, which consists of float values indicating the probability of the input belonging to one of two classes, ranging from 0.0 to 1.0. The first class, 0, is non-pornography, and the second class, 1, is pornography. Therefore, you can simply take the second index of the output (class 1 probability) as your result.

This project was inspired by [Open NSFW](https://github.com/yahoo/open_nsfw). Open NSFW has excellent accuracy but is computationally expensive. ~~While we don't quite meet the accuracy of OpenNSFW~~... This model is now slightly more accurate than Yahoo's Open NSFW. As a bonus, this model executes ~3x faster. On modern hardware, I can run classification with this model at ~3msec on the CPU, including preprocessing.

On a set of 24,000 images (12K per class), the final results for this model vs Yahoo's are:

```
Squeezenet Cutoff = 0.895677871187031
Classifier with type Squeezenet classified pornographic images with an accuracy of 99.2422285369844%.
Classifier with type Squeezenet classified non-pornographic images with an accuracy of 98.9925083957634%.
Classifier with type Squeezenet has an overall accuracy of 99.1173684663739%.

ResNet Cutoff = 0.3
Classifier with type ResNet classified pornographic images with an accuracy of 98.622233703608%.
Classifier with type ResNet classified non-pornographic images with an accuracy of 98.9150090415913%.
Classifier with type ResNet has an overall accuracy of 98.7686213725997%.
```

This model is sufficient enough for real time video classification (modern hardware) at ~13.8x normal playback speed (cinema framerate), or ~333FPS. On a less efficient DNN configuration, you can see a demonstration of this [here](https://www.youtube.com/watch?v=UAlVOGf9V1s), but only at ~3.5x normal playback speed. Making this model work at 333Hz on the CPU like I did is an exercise left to the reader.

It is my hope that you'll use this model to do something good. The development of this model and things like it takes a heavy toll. I am of the opinion that this particular problem is now conquered and am making this available so neither you or anyone else will have to revisit such work again.

## Todo

  - Right now this model performs very well with pornographic imagery, but still doesn't perform quite as well with plain nudity or suggestive imagery. The model can benefit from adding plain nudity, devoid of sexual actions, to the training input.

### Notice  
Everything except the file `nsfw_squeezenet.caffemodel` is a derivative of [SqueezeNet 1.1](https://github.com/DeepScale/SqueezeNet/tree/master/SqueezeNet_v1.1) and thus is under the original [copyright holder's license](https://github.com/DeepScale/SqueezeNet/blob/master/LICENSE), the BSD 2-clause license.

`nsfw_squeezenet.caffemodel` is licensed under the Mozilla Public License v2.
