# 2023_2_opensw_201912427

1.번과제 Mask_RCNN tf2

tensorflow2부터는 케라스와 통합되므로 requirements.txt에서 케라스를 지우고 tensorflow >=2.0.0으로 바꿔준다.

-utils.py-<br/>
    dh = tf.log(gt_height / height)
    dw = tf.log(gt_width / width)
    텐서플로2에서 tf.math.log가 권장되는 방식이므로 수정함, 둘다 기능적으로는 문제없음
    dh = tf.math.log(gt_height / height)
    dw = tf.math.log(gt_width / width)
