# tensorflow-opencv_basic_demo

本篇為tensorflow與opencv快速入門 <br />
分別翻譯與截取自:<br />
tensorflow v1.5:https://github.com/tensorflow/tensorflow<br />
opencv v3.4.0:https://github.com/opencv/opencv<br />

## 本篇使用基本配置:
<ul>
  <li>mac os</li>
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

根據早前在tensorflow issue其他大神的發現,我們需要先對protobuffer進行篇譯: <br >
```
cd ~/Desktop/tensorflow/models/research
protoc object_detection/protos/*.proto --python_out=.
```
之後應該可以嘗試運行:
```
cd object_detection
jupyter notebook
```
![image002](https://github.com/WilsonLTL/tensorflow-opencv_basic_demo/blob/master/002.png)

運行(click)object_detection_tutorial.ipynb,應該可以得出以下:
![image003](https://github.com/WilsonLTL/tensorflow-opencv_basic_demo/blob/master/003.png)

object_detection_tutorial.ipynb，解釋了解大部分使用object_detection的技巧,各位可以自己研究一下<br >

## opencv部分:<br />
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
     cv2.imshow("preview", frame)
  frame = wc.read()

  if cv2.waitKey(1) & 0xFF == ord('q'):
     break

wc.release()

cv2.destroyAllWindows()

```

如果成功你應該可以看到類似的畫面:<br >
![image001](https://github.com/WilsonLTL/tensorflow-opencv_basic_demo/blob/master/001.png)

