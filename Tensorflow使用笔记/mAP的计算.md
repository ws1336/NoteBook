# mAP的计算

基于voc_eval.py进行计算

代码

```python
from voc_eval import voc_eval
 
print voc_eval('/home/cxx/Amusi/Object_Detection/YOLO/darknet/results/{}.txt', '/home/cxx/Amusi/Object_Detection/YOLO/darknet/datasets/pjreddie-VOC/VOCdevkit/VOC2007/Annotations/{}.xml', '/home/cxx/Amusi/Object_Detection/YOLO/darknet/datasets/pjreddie-VOC/VOCdevkit/VOC2007/ImageSets/Main/test.txt', 'person', '.')

```

