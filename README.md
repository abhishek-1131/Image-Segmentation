# Image-Segmentation

Building an image segmentation model on the CamVid dataset (high-quality road-segmentation data)

Image segmentation involves the process of taking a digital image and segmenting it into multiple segments of pixels. The goal of image segmentation is to simplify and/or change the representation of an image into something more meaningful and easier to understand. 

U-Net:
The above was achieved using the U-net architecture. It is a type of CNN consisting of 2 paths. The contraction path (the encoder) and the expansion path (the decoder). The encoder extracts features which contain information about what is in an image using convolutional and pooling layers.Whilst encoding the size of the feature map gets reduced. The decoder is then used to recover the feature map size for the segmentation image, for which it uses Up-convolution layers. Because the decoding process loses some of the higher level features the encoder learned, the U-NET has skip connections. That means that the outputs of the encoding layers are passed directly to the decoding layers so that all the important pieces of information can be preserved.

Working:
After loading in the regular pictures and their segmented versions from the CamVid dataset, a function maps the the path of an image to the path of its segmentation. Forming and training the model is done with the help of fastai library in Pytorch, using the unet_learner class and passing the required parameters to create the U-net. The encoder network used is Resnet 34. This is followed by searching a fitting learning rate using fastai’s learn.lr_find() and training the model. 

After initial training, standardly only the decoder is unfrozen, which means that our pretrained encoder didn’t receive any training yet so after observing the results, the whole model is trained. An accuracy of 93% was achieved.

