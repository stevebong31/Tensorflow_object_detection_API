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


Install Gnuwin 

A program that enables the make tool to be used in windows.

http://gnuwin32.sourceforge.net/downlinks/make.php
http://gnuwin32.sourceforge.net/downlinks/make-src.php

The location should be added to the environment variable.
C:\Program Files (x86)\GnuWin32\bin 


Install Cocoapi

https://github.com/cocodataset/cocoapi

Remove -master from file name and unzip the file.

