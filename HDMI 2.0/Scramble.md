### Scrambling for EMI/RFI Reducation

由于HDMI 2.0会将TMDS Character Rate由340Mcsc拓展到600Mcsc，为了降低EMI和RFI，新增Scramble功能。Scramble的实质是，由于video数据可能频点集中在某一点或者某一小段，会造成EMI/RFI不符规定，**scramble(加扰)将原始数据打乱，让其数据频点不集中在某一点或某一段，从而降低EMI/RFI**。

**降低EMI/RFI方式：**

- TMDS Data Channel：Scramble

- TMDS Clock Channel：降低频率，降低幅值

**HDCP和scramble的先后顺序：**

![2020-04-07222211](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/2020-04-07222211.png)



![2020-04-07 220333](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/2020-04-07%20220333.png)

Scrambling shall be applied to Video Data Periods, Data Island Periods, Guard Bands, and Scrambled Control Periods. **除了SSCP中的8个unscrambled control characters,其余都都要scramble。每个field一个SSCP**，而不是每个Frame一个SSCP。

![2020-04-07221059](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/2020-04-07221059.png)



![iShot2020-04-072216](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/iShot2020-04-072216.png)

![2020-04-07221943](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/2020-04-07221943.png)

![iShot2020-04-0222537](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/iShot2020-04-0222537.png)

![2020-04-07222839](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/2020-04-07222839.png)

#### scrambling control

The scrambling capability of a Sink shall be indicated in the HF-VSDB **LTE_340Mcsc_scramble** bit, and (indirectly) the **Max_TMDS_Character_Rate** field.  340Mcsc以上，必须支持Scramble。

![2020-04-07225432](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/2020-04-07225432.png)



#### Control for TMDS Bit Period/TMDS Clock-Period Ratio

**TMDS Character Rate, TMDS Clock Rate, TMDS Bit Rate之间的关系：**

1. if TMDS Character Rate <= 340Mcsc, TMDS Clock Rate = TMDS Character Rate,  TMDS Bit Rate = 10 TMDS Clock Rate
2. if TMDS Character Rate > 340Mcsc, TMDS Clock Rate = 1/4 TMDS Character Rate,  TMDS Bit Rate = 40 TMDS Clock Rate

![2020-04-07230225](/Users/zengcan/Documents/GitHub/DRM/HDMI%202.0/picture/2020-04-07230225.png)



