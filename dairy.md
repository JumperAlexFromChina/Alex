# 20200422

1. Agilent Technology安捷伦  HDMI电气特性分析仪示波器 

   探头1 对应 clock channel

   探头2，3，4分别对应D0，D1，D2

2. Athena rework平台TMDS clock channel P line短路（万用表测电阻十几欧姆，而正常的N line电阻二十多兆欧姆），以至于clock信号异常，5台电视只有2台电视可以显示，Astro1831协议分析仪连timing都检测不到。**有电视能够显示，说明Rx并不完全依赖clock信号，Rx有能力从data channel恢复clock信号？ IMB的产品，例如soundbar等包含Rx的repeater的设备，都是先在detect clock稳定之后再去做其他处理，如果Tx clock信号异常，则会出现检测不到timing的情况。** *兼容性更强的rx应该要做到能从data channel中恢复clock信号？*

3. CTS测试中，Data channel才有眼图测试项，Clock channel没有眼图测试项，但有clock jitter测试项

4. Bootlin可查Linux源码；Xmind思维导图软件



# 20200428

为什么Dolby Standard HDR要把metadata嵌入到video数据中？

'能够做到最小程度的依赖别的IP，或者完全不依赖于别的IP。例如，原本的HDMI IP不支持Dolby Vision，如果为了支持Dolby HDR，需要做很大的改动。而Dolby IP有能力把metadata嵌入到video数据中，那原有的HDMI IP完全不用做改动，Dolby IP+原有HDMI IP就可能实现Dolby Standard HDR'。这个说法是有道理的，难道这也是Dolby能够很快占领市场的原因？



