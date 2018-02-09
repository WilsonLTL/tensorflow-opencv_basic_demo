# tensorflow-opencv_basic_demo

本篇為tensorflow與opencv快速入門 <br />
分別翻譯與截取自:<br />
tensorflow v1.5:https://github.com/tensorflow/tensorflow<br />
opencv v3.4.0:https://github.com/opencv/opencv<br />

## 本篇使用基本配置:
<ul>
  <li>mac os 10.12.6</li>
  <li>python2.7</li>
  <li>opencv 3.4.0</li>
  <li>tensorflow 1.5</li>
</ul>

首先本篇並不推薦缺乏ML與DL基本知識的朋友現時學習,詳細知識理論可以在網上自己學習<br />
要求擁有一種以上的編程語言為熟識階段,最好是python,不過即使不認識python也不用太擔心<br />

to python雞精:<br >
![python](http://coffeeghost.net/pybat/python_cheatsheet.png)

## tensorflow部分:<br />
refer自 https://www.tensorflow.org/install/install_mac<br />

首先打開terminal,安裝最為重要的pip套件:
```
sudo easy_install pip
pip install --upgrade virtualenv 
```

mac我默認安裝了cpu版本的tensorflow:
```
pip install tensorflow
```

然後分別安裝pillow (Python的圖像處理庫) , lxml (spider) , jupyter (notebook) , matplotlib (math expression) :
``` 
sudo pip install pillow
sudo pip install lxml
sudo pip install jupyter
sudo pip install matplotlib
```

然後使用git直接downolad github的tensorflow source ,還沒有git就先去下載一下:<br />
```
git clone https://github.com/tensorflow/tensorflow.git
```

根據早前在tensorflow issue其他大神的發現,我們需要先對protobuf進行篇譯: <br >
```
cd ~/Desktop/tensorflow/models/research
protoc object_detection/protos/*.proto --python_out=.
```
同理,沒protobuf自己去下載一下<br />
之後應該可以嘗試運行:
```
cd object_detection
jupyter notebook
```
![image002](https://github.com/WilsonLTL/tensorflow-opencv_basic_demo/blob/master/002.png)

運行(click)object_detection_tutorial.ipynb,應該可以得出以下:
![image003](https://github.com/WilsonLTL/tensorflow-opencv_basic_demo/blob/master/003.png)

object_detection_tutorial.ipynb，解釋了大部分使用object_detection的基礎技巧,各位可以自己研究一下<br >

## COCO-trained models差異
ref:https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md
tensorflow提供大量不同類型的models以供使用:
<table>
  <tr><td>Model name</td><td>Speed (ms)</td><td>COCO mAP</td></tr>
  <tr><td>ssd_mobilenet_v1_coco</td><td>30</td><td>21</td></tr>
  <tr><td>ssd_inception_v2_coco</td><td>42</td><td>24</td></tr>
  <tr><td>faster_rcnn_inception_v2_coco</td><td>58</td><td>28</td></tr>
  <tr><td>faster_rcnn_resnet50_coco</td><td>89</td><td>30</td></tr>
  <tr><td>faster_rcnn_resnet50_lowproposals_coco</td><td>64</td><td></td></tr>
  <tr><td>rfcn_resnet101_coco</td><td>92</td><td>30</td></tr>
  <tr><td>faster_rcnn_resnet101_coco</td><td>106</td><td>32</td></tr>
  <tr><td>faster_rcnn_resnet101_lowproposals_coco</td><td>82</td><td></td></tr>
  <tr><td>faster_rcnn_inception_resnet_v2_atrous_coco</td><td>620</td><td>37</td></tr>
  <tr><td>faster_rcnn_inception_resnet_v2_atrous_lowproposals_coco</td><td>241</td><td></td></tr>
  <tr><td>faster_rcnn_nas</td><td>1833</td><td>43</td></tr>
  <tr><td>faster_rcnn_nas_lowproposals_coco</td><td>540</td><td></td></tr>
</table>
其中ssd_mobilenet_v1_coco最為適合realtime video analysis,但精準度不高,具體的差別可以自己嘗試一下<br >

## opencv部分:<br />
import opencv的方法網上有很多,再加上不同版本之間也有差異,所以各位可以自己找最適合自己的版本<br >
### 基礎測試

```python
#cv2 = opencv
import cv2

#啟動webcam
cv2.namedWindow("testing_preview")
wc = cv2.VideoCapture(0)

#讀取畫面
frame = wc.read()

#無限loop
while True:

  if frame is not None:
     cv2.imshow("testing_preview", frame)
  frame = wc.read()

  if cv2.waitKey(1) & 0xFF == ord('q'):
     break

wc.release()

cv2.destroyAllWindows()

```

如果成功你應該可以看到類似的畫面:<br >

## Tutorial
A real time child AI video analysis base on opencv and tensorflow-object-detection api <br >
pseudo code: <br />

```
import tf,cv2,sys,os,numpy,tarfile,utils
class 
  setting models detail
  download the models
  fun detection graph as deafult ...
  
  while true loop:
    read the frame from cv2
    analysis from models
    show the result
    
    break if system call exit
```


