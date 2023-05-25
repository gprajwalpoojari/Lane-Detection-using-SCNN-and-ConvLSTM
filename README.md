# Lane-Detection-using-SCNN-and-ConvLSTM


## Video Demonstration
This video was recorded on the campus of Worcester Polytechnic Institute. The results (i.e Lane Detection) are not accurate because the model was tested only after training it for 3 epochs.

![lane_detection](https://github.com/gprajwalpoojari/Lane-Detection-using-SCNN-and-ConvLSTM/assets/53962958/966fd002-8426-4dac-b855-9def122623c9)

## About the project

This project performs lane detection on continuous driving scenes and approaches it as a segmentation task. The hybrid network implements a novel hybrid spatial-temporal sequence-to-one deep learning architecture that integrates the following aspects: (a) the single image feature extraction module equipped with the spatial convolutional neural network (SCNN); (b) the spatial-temporal feature integration module constructed by spatial-temporal recurrent neural network (ST-RNN); (c) the encoder-decoder structure, which makes this image segmentation problem work in an end-to-end supervised learning format. Several experiments were performed to measure the accuracy, precision, recall and F1 measure of various networks formed by a combination of different variants of ST-RNN and Encoder-Decoder modules along with SCNN module.

## Network Architecture

![Network](https://github.com/gprajwalpoojari/Lane-Detection-using-SCNN-and-ConvLSTM/assets/53962958/24dd64a1-4ce3-428e-a9ce-5dc7e3aa522e)

## tvtLANE dataset

This project uses tvtLANE Dataset for the training and evaluation of the network. This dataset contains 19383 image sequences for lane detection, and 39460 frames of them are labeled. These images were divided into two parts, a training dataset contains 9548 labeled images and augmented by four times, and a test dataset has 1268 labeled images. The size of images in this dataset is 128*256.

The dataset can be downloaded here:
https://drive.google.com/drive/folders/1MI5gMDspzuV44lfwzpK6PX0vKuOHUbb_?usp=sharing

The dataset folder should have the following structure:
```
.
├── testset
│   ├── image
│   ├── test_index_0530.txt
│   ├── test_index_0531.txt
│   ├── test_index_0601.txt
│   └── truth
└── trainset
    ├── train_index.txt
    ├── trainset
    │   ├── image
    │   └── truth
    └── val_index.txt
```

Note - If you have different folder structure, you will need to adjust the paths accordingly.

## Scripts
1. config.py - This file define the parameters, settings and preferences utilized by the network.
2. data_set.py - This file reads and converts the data into tensor format, which is accepted by the network.
3. model.py - This file implements ST-RNN module (ConvLSTM) sandwiched between encoder-decoder structure. SCNN module is inserted in the encoder.
4. model_GRU.py - This file implements ST-RNN module (ConvGRU) sandwiched between encoder-decoder structure. SCNN module is inserted in the encoder.
5. train.py - This file trains and validate the model using training and validation dataset respectievely.
6. test.py - This file test the model on the testing dataset.

## Results
The figure below shows the detection of Lane in different conditions:

Lane Detection in Normal Condition:

![result1](https://github.com/gprajwalpoojari/Lane-Detection-using-SCNN-and-ConvLSTM/assets/53962958/b8e4d49e-4e50-4cb2-b586-5e35e0ea6d0f)

Lane Detection under Occlusion:

![result3](https://github.com/gprajwalpoojari/Lane-Detection-using-SCNN-and-ConvLSTM/assets/53962958/7dd26627-42d1-4a2c-aae5-bf57198eec38)

Lane Detection inside a tunnel:

![result4](https://github.com/gprajwalpoojari/Lane-Detection-using-SCNN-and-ConvLSTM/assets/53962958/dc6d89a0-eeea-4c0e-b18d-6cae10dc4cf4)

Failed Lane Detection in low lightning condition:

![result5](https://github.com/gprajwalpoojari/Lane-Detection-using-SCNN-and-ConvLSTM/assets/53962958/db5f7f92-7222-47b7-bb31-2db930aace8e)

## References

https://github.com/qinnzou/Robust-Lane-Detection
