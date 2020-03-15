#Electrical Specification

1. During the powered-Off state (e.g. power removed), the CEC line is not monitored. 

   > 当device处于power off状态（完全断电情况下），cec line可以不监控。漏电流最大1.8微安。

   ![cec_electrical_power_off_state](./picture/cec_electrical_power_off_state.png)

2. in all other power states. In these states, the device shall keep monitoring the CEC line for any messages addressing that device, including any messages that bring the device out of Standby 

   > 当device处于power off以外的其它状态时，应该满足下面电气特性要求：

![cec_power_on_electrical_requirements](./picture/cec_power_on_electrical_requirements.png)



#Signaling and Bit Timings

##Start Bit Timing

![start bit timing](./picture/start bit timing.png)

## Data Bit Timing

![Data Bit Timing](./picture/Data Bit Timing.png)



## ACK Bit Timing

CEC Figure 5 shows an example bit with both Initiator and Follower where the Follower may assert the bit to a logical 0 to acknowledge a Data Block. The Initiator outputs a logical 1, thus allowing the Follower to change the CEC state **by pulling the control line low for the duration of the safe sample period.**

> Initiator继续发1，而Follower在Safe Sample Period拉低。

![cec ACK](./picture/cec ACK.png)



# Frame Description

##Frame Description

![cec frame](./picture/cec frame.png)



![cec header block](./picture/cec header block.png)



![cee logical address](./picture/cee logical address.png)