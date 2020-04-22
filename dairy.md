# 20200422

1. Agilent Technology安捷伦  HDMI电气特性分析仪示波器 

   探头1 对应 clock channel

   探头2，3，4分别对应D0，D1，D2

2. Athena rework平台TMDS clock channel P line短路（万用表测电阻十几欧姆，而正常的N line电阻二十多兆欧姆），以至于clock信号异常，5台电视只有2台电视可以显示，Astro1831协议分析仪连timing都检测不到。**有电视能够显示，说明Rx并不完全依赖clock信号，Rx有能力从data channel恢复clock信号？ IMB的产品，例如soundbar等包含Rx的repeater的设备，都是先在detect clock稳定之后再去做其他处理，如果Tx clock信号异常，则会出现检测不到timing的情况。** *兼容性更强的rx应该要做到能从data channel中恢复clock信号？*

3. CTS测试中，Data channel才有眼图测试项，Clock channel没有眼图测试项，但有clock jitter测试项

4. Bootlin可查Linux源码；Xmind思维导图软件

   

