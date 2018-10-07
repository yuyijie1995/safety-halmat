# safety-halmat
2018国家电投安全帽检测 最后成绩B榜6/599
采用的模型有yolo3 重写了fpn https://github.com/qqwweee/keras-yolo3.git 得分是0.87
fasterrcnn https://github.com/you359/Keras-FasterRCNN.git 得分是0.78
retinanet https://github.com/fizyr/keras-retinanet.git 得分是0.88
maskrcnn去掉mask结构用的是tensorpack的接口 https://github.com/tensorpack/tensorpack.git 最后得到0.92的成绩
重点在于对训练集的分析
再训练集标注里面筛选像素小于25的记录，大约500多个，里面有标识到很小模糊的帽子，有的还标记到帽子里面的一小团
对无效的数据进行过滤
softnms对propasal类型的算法有0.5个点的提升
对训练集的坐标数据进行统计分析
由于标注是在缩小后的图像上标注，有些坐标值取不到
trick：输出结果时，避开这些永远没出现过的值就好了
把所有测试结果裁出来，去掉明显错误的

TODO
1.多模型融合
2.尝试cascadercnn，据说单模很容易能到0.91
3.数据的筛选和处理
4.数据增强
