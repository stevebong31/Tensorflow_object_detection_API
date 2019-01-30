# Tensorflow Object Detection API in Windows
This document is based on the content of V-AIS object detection API document and has been modified to suit the project in progress.

(https://github.com/V-AIS/tensorflow/tree/master/Object_Detection_API )

## 1. Install
Download the file from that link.
https://github.com/tensorflow/models

Remove -master from file name and unzip the file.

The official documentation for the installation is available at the following link:
https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/installation.md

You must install all of the dependency packages.
If using a window, use anaconda.

* Protobuf 3.0.0
* Python-tk
* Pillow 1.0
* lxml
* tf Slim (which is included in the "tensorflow/models/research/" checkout)
* Jupyter notebook
* Matplotlib
* Tensorflow (>=1.9.0)
* Cython
* contextlib2
* cocoapi

And then set up Tensorflow.

<pre><code>pip install tensorflow-gpu
or   
conda install tensorflow-gpu</code></pre>

Install Protobuf compialtion

https://github.com/google/protobuf/releases

(I used the 3.4 version.)

The location of the unziped bin file should be added to the environment variable.
C:\Users\hostname\Documents\protoc\bin

<pre><code>> cd models\research
> protoc object_detection\protos\*.proto --python_out=.
</code></pre>


### Install Gnuwin 

A program that enables the make tool to be used in windows.

http://gnuwin32.sourceforge.net/downlinks/make.php
http://gnuwin32.sourceforge.net/downlinks/make-src.php

The location should be added to the environment variable.
C:\Program Files (x86)\GnuWin32\bin 


### Install Cocoapi

https://github.com/cocodataset/cocoapi

Remove -master from file name and unzip the file.

<pre><code>> cd cocoapi\PythonAPI
> python setup.py build_ext --inplace
</code></pre>

The location should be added to the environment variable.

C:\Users\hostname\Documents\models\research
C:\Users\hostname\Documents\models\research\slim

### Test installation
<pre><code>> cd models\research
> python object_detection\builders\model_builder_test.py
</code></pre>


### Imange Crawler

https://github.com/YoongiKim/AutoCrawler


### Imange labeling

 https://github.com/tzutalin/labelImg
 
### xml to csv
 To generate tfrecord data, we need to change the xml file to csv.
 xml files created per image are converted into one csv file. The Python code is located in src.
 We use 90 percent as training data and 10 percent as testing data.

 <pre><code> + obj_recog
        + data
                - train_labels.csv
                - test_labels.csv
        + images
                + train
                        - train_images
                        - train_xmls
                + test
                        - test_images
                        - test_xmls
        - xml_to_csv.py
</code></pre>

### csv and images to tfrecord

Finally, we can create tfrecord data with images and csv files.
The Python code is located in src.

  #### line path = os.path.join(os.getcwd(), 'images/train')  <--- train/test



### Train model and set config file

https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md

We use ssdlite_mobilenet_v2_coco.

https://github.com/tensorflow/models/tree/master/research/object_detection/samples/configs


data/object-detection.pbtxt


  <pre><code> item {
    name: "cantatacoffee"
    id: 1
    display_name: "cantatacoffee"
}
</code></pre>

-folder and file-

  <pre><code> + obj_recog
        + data
                - train_labels.csv
                - test_labels.csv
                - train.record
                - test.record
                - object-detection.pbtxt
        + images
                + train
                        - train_images
                        - train_xmls
                + test
                        - test_images
                        - test_xmls
        - xml_to_csv.py
        - generate_tfrecord.py
        - faster_rcnn_resnet101_coco_2018_01_28.config
        - faster_rcnn_resnet101_coco_2018_01_28.tar
</code></pre>


### Train
We need to copy /models/research/object_detection/train.py file to the data file.

To selectively use a GPU, use the following command: (CUDA_VISIBLE_DEVICES=3)
<pre><code>python3 train.py --logtostderr --train_dir=.\save_model --pipeline_config_path=.\ssdlite_mobilenet_v2_coco.config
</code></pre>
Tensorboard (CUDA_VISIBLE_DEVICES= )
<pre><code>> cd ~/model/research/object_detection
> tensorboard --logdir=./ --port=****
</code></pre>