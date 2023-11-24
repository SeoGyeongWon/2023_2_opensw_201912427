# 2023_2_opensw_201912427

1.번과제 Mask_RCNN tf2

가상환경 만들고 tensorflow-gpu==2.2 install<br/>
cuda와 cudnn 텐서플로우 버전에 맞는걸로 설치함.

<br/>tensorflow2부터는 케라스와 통합됬다해서 따로 keras 설치 하지 않았음.<br/> 
requirements.txt에서 케라스와 텐서플로를 지우고 pip install했음<br/>

<br/>-utils.py-<br/>
    dh = tf.log(gt_height / height)<br/>
    dw = tf.log(gt_width / width)<br/>
    텐서플로2에서 tf.math.log가 권장되는 방식이므로 수정함, 둘다 기능적으로는 문제없음<br/><br/>
    dh = tf.math.log(gt_height / height)<br/>
    dw = tf.math.log(gt_width / width)<br/><br/>

    -parallel_model.py- <br/>
import keras.backend as K<br/>
import keras.layers as KL<br/>
import keras.models as KM<br/><br/>
기존의 케라스 패키지에서 tf.keras패키지로 변경한다.<br/><br/>
import tensorflow.keras.backend as K<br/>
import tensorflow.keras.layers as KL<br/>
import tensorflow.keras.models as KM<br/>
