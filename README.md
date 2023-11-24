# 2023_2_opensw_201912427

1.번과제 Mask_RCNN tf2

가상환경 만들고 tensorflow-gpu==2.2 install<br/>
cuda와 cudnn 텐서플로우 버전에 맞는걸로 설치함.<br/>

<br/>tensorflow2부터는 케라스와 통합됬다해서 따로 keras 설치 하지 않았음.<br/> 
https://github.com/matterport/Mask_RCNN.git 깃 클론하고
<br/>requirements.txt에서 케라스와 텐서플로를 지우고 pip install했음<br/>
만들어진 Maks_RCNN폴더에 coco.h5 와 balloon.h5를 넣고 
<br/>smaple\balloon 폴더에 balloon\train balloon\val 넣음 <br/>

python balloon.py train --dataset="C:\Users\skwkn\Mask_RCNN\samples\balloon\balloon" --weights=coco - 아나콘다에 입력했으나 오류발생.<br/>

<img width="853" alt="image" src="https://github.com/SeoGyeongWon/2023_2_opensw_201912427/assets/126853734/cdf9f925-1022-457a-8b02-3873b4ed6368"> <br/><br/>

*끝끝내 해결하지 못했음.<br/><br/>


#코드관련 수정  <br/><br/>
tensorflow upgrade script를 사용하여 Tf1.x의 코드를 Tf2.x코드로 업그레이드 해준다고 함.<br/><br/>

tf_upgrade_v2 --infile 변환시킬파일.py --outfile 변환시킬파일-upgrade.py <-tf upgrade script <br/><br/>


utils.py<br/><br/>
line 202,203 rename -> tf.log 를 tf.math.log 로 변경 <br/><br/>

parallel_model.py<br/><br/>
INFO line 72:21: `name` passed to `name_scope`. Because you may be re-entering an existing scope, it is not safe to convert automatically,  the v2 name_scope does not support re-entering scopes by name.<br/>
INFO line 72:21: Renamed 'tf.name_scope' to 'tf.compat.v1.name_scope'<br/>
INFO line 132:8: Renamed 'tf.reset_default_graph' to 'tf.compat.v1.reset_default_graph'<br/>


modle.py<br/><br/>
INFO line 287:62: Added keywords to args of function 'tf.shape'<br/>
INFO line 324:55: Added keywords to args of function 'tf.shape'<br/>
INFO line 325:24: Added keywords to args of function 'tf.pad'<br/>
INFO line 341:11: Renamed 'tf.log' to 'tf.math.log' <br/>
INFO line 341:23: Renamed 'tf.log' to 'tf.math.log' <br/>
INFO line 399:17: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 431:44: Added keywords to args of function 'tf.shape' <br/>
INFO line 439:43: Added keywords to args of function 'tf.shape' <br/>
INFO line 445:27: Added keywords to args of function 'tf.shape' <br/>
INFO line 445:48: Added keywords to args of function 'tf.shape' <br/>
INFO line 466:35: Added keywords to args of function 'tf.shape' <br/>
INFO line 467:26: Added keywords to args of function 'tf.shape' <br/>
INFO line 482:32: Added keywords to args of function 'tf.shape' <br/>
INFO line 482:53: Added keywords to args of function 'tf.shape' <br/>
INFO line 509:29: Added keywords to args of function 'tf.shape' <br/>
INFO line 518:19: Added keywords to args of function 'tf.boolean_mask' <br/>
INFO line 520:35: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 526:15: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 527:19: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 538:20: Added keywords to args of function 'tf.reduce_max' <br/>
INFO line 542:18: Added keywords to args of function 'tf.reduce_max'  <br/>
INFO line 545:23: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 547:23: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 553:23: Renamed 'tf.random_shuffle' to 'tf.random.shuffle' <br/>
INFO line 554:21: Added keywords to args of function 'tf.shape' <br/>
INFO line 558:23: Renamed 'tf.random_shuffle' to 'tf.random.shuffle' <br/>
INFO line 565:28: Added keywords to args of function 'tf.cond' <br/>
INFO line 566:19: Added keywords to args of function 'tf.shape' <br/>
INFO line 567:26: Added keywords to args of function 'tf.argmax' <br/>
INFO line 579:38: Added keywords to args of function 'tf.transpose' <br/>
INFO line 597:26: Added keywords to args of function 'tf.shape' <br/>
INFO line 611:8: Added keywords to args of function 'tf.shape' <br/>
INFO line 612:49: Added keywords to args of function 'tf.shape' <br/>
INFO line 613:11: Added keywords to args of function 'tf.pad' <br/>
INFO line 614:19: Added keywords to args of function 'tf.pad' <br/>
INFO line 615:23: Added keywords to args of function 'tf.pad' <br/>
INFO line 616:13: Added keywords to args of function 'tf.pad' <br/>
INFO line 617:12: Added keywords to args of function 'tf.pad' <br/>
INFO line 700:16: Added keywords to args of function 'tf.argmax' <br/>
INFO line 716:11: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 719:20: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 720:15: Renamed 'tf.sets.set_intersection' to 'tf.sets.intersection' <br/>
INFO line 722:15: Renamed 'tf.sparse_tensor_to_dense' to 'tf.sparse.to_dense' <br/>
INFO line 734:14: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 744:47: Added keywords to args of function 'tf.shape' <br/>
INFO line 745:21: Added keywords to args of function 'tf.pad' <br/>
INFO line 756:35: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 758:11: Renamed 'tf.sets.set_intersection' to 'tf.sets.intersection' <br/>
INFO line 760:11: Renamed 'tf.sparse_tensor_to_dense' to 'tf.sparse.to_dense' <br/>
INFO line 764:26: Added keywords to args of function 'tf.shape' <br/>
INFO line 772:8: Changed tf.to_float call to tf.cast(..., dtype=tf.float32). <br/>
INFO line 777:43: Added keywords to args of function 'tf.shape' <br/>
INFO line 778:17: Added keywords to args of function 'tf.pad' <br/>
INFO line 857:33: Added keywords to args of function 'tf.shape' <br/>
INFO line 869:50: Added keywords to args of function 'tf.shape' <br/>
INFO line 1035:14: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 1043:20: Added keywords to args of function 'tf.size' <br/>
INFO line 1060:14: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 1072:20: Added keywords to args of function 'tf.size' <br/>
INFO line 1093:21: Added keywords to args of function 'tf.argmax' <br/>
INFO line 1108:11: Added keywords to args of function 'tf.reduce_sum' <br/>
INFO line 1108:33: Added keywords to args of function 'tf.reduce_sum' <br/>
INFO line 1126:22: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 1136:20: Added keywords to args of function 'tf.size' <br/>
INFO line 1154:17: Added keywords to args of function 'tf.shape' <br/>
INFO line 1156:17: Added keywords to args of function 'tf.shape' <br/>
INFO line 1160:17: Added keywords to args of function 'tf.transpose' <br/>
INFO line 1164:18: Renamed 'tf.where' to 'tf.compat.v1.where' <br/>
INFO line 1175:20: Added keywords to args of function 'tf.size' <br/>
INFO line 2173:16: Added keywords to args of function 'tf.reduce_mean' <br/>
INFO line 2180:73: Added keywords to args of function 'tf.size' <br/>
INFO line 2197:16: Added keywords to args of function 'tf.reduce_mean' <br/>
INFO line 2822:24: Added keywords to args of function 'tf.reduce_sum' <br/>
INFO line 2823:12: Added keywords to args of function 'tf.boolean_mask' <br/><br/><br/>


3개의 .py 파일 외에는 따로 수정되는 파일은 없었음.


