# Speech Recognition

## Table of Contents
+ [About](#about)
+ [Prerequisies](#prerequisites)
+ [Results](#results)

## About <a name = "about"></a>
This is more a journey where I attempt to learn how to do some basic speech recognition. The goal of this project was to learn to do basic speech recogntion, in this case phoneme recognition. How different types of neural networks change the results, and their sizes. The "goal" if we can call it that was to see how small the neural networks could be while still getting good enough results. So that we could potentially use it in small embedded systems or the like.

This project was a project in the subject TDT4310 and this is the actual delivery I made.

## Prerequisites <a name = "prerequisites"></a>
Numpy

sklearn

matplotlib

pandas

python_speech_features

scipy

Tensorlfow 2.2.0

The only special piece of software used is the levenshtein algorithm which can be found [here](https://github.com/ztane/python-Levenshtein/) and installed by 
```
pip install python-Levenshtein
```

## Results <a name = "results"></a>
There were done multiple experiments on different neural networks, but they were either CNNs or simple DNNs.
The error rate used in this project is the PER (phoneme error rate). This can be calculated using the Levenshtein algotihm, which is done here.


| Neural Network                           | Average PER | min-max PER   | Parameters |
|------------------------------------------|-------------|---------------|------------|
| CNN {{m:150, p:6, f: 6} + 2 * 1000}      | 35.20 %     | 34.85-35.63%  | 8.3M       |
| CNN {{m:150, p:6, f: (40x1)} + 2 * 1000} | 34.66 %      | 34.41-34.84%  | 2.3M       |
| CNN {{m:50, p:6, f: (40x8)} + 2 * 256}   | 35.63 %      | 35.51-35.82%  | 181K       |
| DNN {2000 + 1000 * 2}               | 37.64 %     | 37.25-38.01%  | 6.9M       |
| DNN {256 * 2}                       | 42.23 %     | 41.94-42.45%  | 560K       |

As we can see the CNN based architecture is seemingly a lot better than the DNN based one. And while making the CNN smaller we still barely loose out in terms of PER.





The results are quite lacking, and is in all likelihood from bad pre-processing. A project similar project, [yh1008](https://yh1008.github.io/DNN-HMM/slides#/19), has quite a lot better results, with just about the same neural network. This other project used Kaldi, and therefore more standardised pre-processing techniques, and it seems like it would have helped considering everything else seemed to be the same.


### Thanks to
kyleobo. I borrowed the README template from [here](https://github.com/kylelobo/The-Documentation-Compendium/blob/master/en/README_TEMPLATES/Minimal.md)
