# 古诗生成器

* 通过调整config的form和max_len选择生成五言绝句或七言绝句

* 两种模型可供训练：
1. 不带Attention Layer的LSTM模型
2. 带Attention Layer的LSTM模型

* 关于RNN/LSTM/Attention可以浏览以下资料：
[学习链接](https://blog.csdn.net/yyhhlancelot/article/details/102502355)

* 提供训练了6000epoch的带Attention的模型供下载测试
[下载链接](https://pan.baidu.com/s/1fLf94zv-jHwJ5U5oddBcpw)

### 训练过程，每一行代表不同的temperature，对结果的概率产生影响，可以理解为结果的宽容度/开放度
==============epoch 32=============
客心仍在楚，若轰余页蒙新朵易玉衰音狙友效函侍步鶒
客心仍在楚，尺味堰龉孀，鸥花履飞悸，中略矶苾躁。
客心仍在楚，盈芳冈涓，，烟橙失各。。危声丝重。。
==============epoch 428=============
秦地平如掌，神雪咤圜壶。柱恭鸣艳开为红卧拔背惟合
秦地平如掌，间尔慕开寻。承渐持紫明，能间天就早。
秦地平如掌，动静轩净阵。未尚影幽神，布凝朝转，。
==============epoch 1980=============
西陵侠少年，恋铁急真衫。倚玉将后静，光平半川将。
西陵侠少年，下化条斑央。日管筵卷杯，承道有间太。
西陵侠少年，长氛世披明。音天房宫合，早开发素日。
==============epoch 3808=============
玉管朝朝弄，喧九阴南王。朱诚朝爱见，愁泉喧天强。
玉管朝朝弄，明风诗气夜。人盛长自送，年高送风金。
玉管朝朝弄，仙徒气水欲。绕水龙秦月，独山风春中。
==============epoch 5200=============
江皋三月时，然镜四处破。容当水千波，事霜时门颜。
江皋三月时，持流风风看。知物两道在，十李将羽谁。
江皋三月时，白阳双轻尽。徒翠月黄人，多对北红复。

### 功能设置
功能仅仅设置了通过设置前一句，生成整首诗，例如：
输入
```
sentence = '江南季冬月，'
generate = model.predict_sentence(sentence, temperature = 1)
```
输出
```
generate
'江南季冬月，晴北轻庭西。步飞河从君，列照游千空。'
```
还可以添加藏头诗等功能，例如藏头诗的功能这么做：
比如第一个字是“月”，随机从训练数据中选择一首诗，然后作为前面开头几个字，类似：
输入
```
sentence = '翁夜往还。月'
generate = model.predict_sentence(sentence, temperature = 1)
```
输出
```
generate
'翁夜往还。月花未灵霜，山三恩尽已。愁泣雪都人，将'
```
这时只需要取我们需要的```月花未灵霜，```就行了，同理，就生成了藏头诗。
