##HDMI 2.0新增packet类型

![2020-04-08223437](./picture/2020-04-08223437.png)



##HDMI 2.0 AVI InfoFrame的改变

![2020-04-08224814](./picture/2020-04-08224814.png)



## HF-VSIF

**在HDMI 2.0中，HF-VSIF主要是用来传输3D相关信息**，如果用到Table 10-1中的feature，必须发HF-VSIF，每field一次。

![2020-04-08230248](./picture/2020-04-08230248.png)

![2020-04-08224952](./picture/2020-04-08224952.png)

![2020-04-08231215](./picture/2020-04-08231215.png)

###HF-VSIF定义

![iShot2020-04-0825153](./picture/iShot2020-04-0825948.png)

![2020-04-08232650](./picture/2020-04-08232650.png)





# E-EDID 

##Signaling of supported Video Formats

![2020-04-0823302](./picture/2020-04-0823302.png)



## HF-VSDB

**HDMI Forum Vendor Specific Data Block**

![2020-04-08232138](./picture/2020-04-08232138.png)

![2020-04-08232431](./picture/2020-04-08232431.png)



##HDMI Audio Data Block

![2020-04-08233343](./picture/2020-04-08233343.png)



# Status and Control Data Channel

**EDID    0xA0/0xA1 —>0x50**
**HDCP   0x74/0x75 —>0x3A**
**SCDC   0xA8/0xA9 —>0x54**

![2020-04-08233530](./picture/2020-04-08233530.png)



##Status and Control Data Channel Structure

![2020-04-08233707](./picture/2020-04-08233707.png)



###Update Flag

![iShot2020-04-0234158](./picture/iShot2020-04-0234158.png)



### TMDS Configuration

![2020-04-08234340](./picture/2020-04-08234340.png)



###Scrambler Status

![2020-04-08 235142](./picture/2020-04-08 235142.png)



### Status Flags

![2020-04-08235513](./picture/2020-04-08235513.png)



### Character Error Detection

![2020-04-08235635](./picture/2020-04-08235635.png)

![2020-04-08235744](./picture/2020-04-08235744.png)



#Auto Lipsync Correction Feature

![2020-04-0235946](./picture/2020-04-0235946.png)

对一般设备来讲，video latency 都会大于audio latency，因为video数据量大，因此video processing的时间长。一般要求，audio数据要在和它相关的video数据传输完成+-2ms内传输完成。