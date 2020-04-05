**HEAC (HDMI Ethernet and Audio Return Channel) **包含两个功能：

1. HEC , HDMI Ethernet Channel
2. ARC , Audio Return Channel



##Type A Connector Pin Assignment

![Connector Pin Assignments for HEAC](./picture/Connector_Pin_Assignments_for_HEAC.png)



**HEC only, 在differential mode **

**ARC only,可以是single mode或common mode**

**如果同时ARC和HEC，必须同时是common mode和differential mode**



##ARC 简图

如果支持ARC，ARC Rx必须同时支持single mode和common mode；而ARC Tx可以只支持single mode

![ARC](./picture/ARC.png)



## System Operating Conditions

![System Operating Conditions](./picture/System_Operating_Conditions.png)



## Differential Signal Characteristics

**differential mode电气特性**

![Differential Signal Characteristics](./picture/Differential_Signal_Characteristics.png)



##Common Mode Signal Characteristics

**Common mode电气特性**

![Common Mode Transmission Characteristics at TP2](./picture/Common_Mode_Transmission_Characteristics_at_TP2.png)

![HEAC Common Mode Transmission Characteristics at TP1](./picture/HEAC_Common_Mode_Transmission_Characteristics_at_TP1.png)



##Single Mode Signal Characteristics

**single mode电气特性**

* single mode只用HEAC+一根线即可

* single mode只能用来传ARC信号（即IEC60958信号），不能和differential mode一同传送

  ![屏幕快照 2020-03-22 01.00.51](./picture/2020-03-22_01_00_51.png)

![屏幕快照 2020-03-22 01.01.28](./picture/2020-03-22_01_01_28.png)



## Receiver Performance

同时传递HEC和ARC信号（即同时工作在differential mode和common mode），信号波形可能如下：

![屏幕快照 2020-03-22 01.09.53](./picture/2020-03-22_01_09_53.png)

在这个波形图上，其实有多个信号，一个高频信号（HEC），一个低频信号（ARC）。**两个信号相加减，就可以还原两个原始信号。**

