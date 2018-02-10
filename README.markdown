# YOLO with Core ML

This repo was forked and modified from [hollance/YOLO-CoreML-MPSNNGraph](https://github.com/hollance/YOLO-CoreML-MPSNNGraph). Some changes I made: 

1. Only keep CoreML since that is the only part I am interested at
2. Use YOLO2 pre-trained model instead of TinyYOLO. YOLO2 pre-trained model provides more classes and more accurate than Tiny-YOLO. It is slower, but it can recognizes more stuff. 
3. Drop yad2k converter. I use darkflow to convert YOLO pre-trained models from darknet format to tensorflow. And use tf-coreml to convert from tensorflow to CoreML.


## About YOLO object detection

YOLO is an object detection network. It can detect multiple objects in an image and puts bounding boxes around these objects. [Read hollance's blog post about YOLO](http://machinethink.net/blog/object-detection-with-yolo/) to learn more about how it works.

![YOLO in action](YOLO.jpg)

In this repo you'll find:

- **YOLO-CoreML:** A demo app that runs the YOLO neural network on Core ML.
- **Converter:** The scripts needed to convert the original DarkNet YOLO model to Core ML.

To run the app:

1. execute download.sh to download the pre-trained model
`% sh download.sh`
2. open the **xcodeproj** file in Xcode 9 and run it on a device with iOS 11 or better installed.

The reported "elapsed" time is how long it takes the YOLO neural net to process a single image. The FPS is the actual throughput achieved by the app.

> **NOTE:** Running these kinds of neural networks eats up a lot of battery power. The app can put a limit on the number of times per second it runs the neural net. You can change this in `setUpCamera()` by changing the line `videoCapture.fps = 50` to a smaller number.

## Converting the models

> **NOTE:** You don't need to convert the models yourself. Everything you need to run the demo apps is included in the Xcode projects already. 

If you're interested in how the conversion was done, check the [instructions](Converter/).

