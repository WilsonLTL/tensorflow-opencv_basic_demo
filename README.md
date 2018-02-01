本篇為tensorflow與opencv快速入門 <br />
分別翻譯與截取自:<br />
tensorflow v1.5:https://github.com/tensorflow/tensorflow<br />
opencv v3.4.0:https://github.com/opencv/opencv<br />

## 本篇使用基本配置:
<ul>
  <li>mac os</li>
  <li>python2.7</li>
  <li>opencv 3.4.0</li>
  <li>tensorflow v1.5</li>
</ul>

首先本篇並不推薦缺乏ML與DP基本知識的朋友現時學習,詳細知識理論可以在網上自己學習<br />
要求擁有一種以上的編程語言為熟識階段,最好是python,不過即使不認識python也不用太擔心<br />

## tensorflow部分:<br />
refer自 https://www.tensorflow.org/install/install_mac<br />

## opencv部分:<br />
### 基礎測試

```python
#cv2 = opencv
import cv2

#啟動webcam
cv2.namedWindow("testing_preview")
wc = cv2.VideoCapture(0)

#讀取畫面
rval, frame = wc.read()

#無限loop
while True:

  if frame is not None:
     cv2.imshow("preview", frame)
  rval, frame = wc.read()

  if cv2.waitKey(1) & 0xFF == ord('q'):
     break

wc.release()

cv2.destroyAllWindows()

```
