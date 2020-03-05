L-PCM and IEC61937 compressed audio data is formatted in the **Audio Sample Packet** or in the **High Bitrate Audio Stream Packet** as a structure that closely resembles in an IEC60958 frame.



**Audio Clock Regeneration**: 128*fs = f_tdms * N/CTS



For any L-PCM stream, the ACR fs value shall be equal to the audio sample rate.

For any IEC60958 compressed audio with an IEC60958 frame rate at or below 192kHZ, the fs value shall be equal to the frame rate. For any such stream with an IEC60958 frame rate above 192kHZ, the ACR fs value shall be 1/4th of the frame rate.



人耳的反应范围在20HZ-20KHZ，根据奈奎斯特采样定律，fs>40KHZ就能不失真的还原信号。CD碟片的音频采样fs=44.1KHZ，属于高保真的数字音频。



basic audio：2 channel 32k，44.1k，48k

source可选支持2 channel 32k，44.1k，48k其中一种或几种

sink必须支持2 channel 32k，44.1k



有时候，为了获得足够的带宽来传输audio，可以选择pixel repetition。 pixel repetition就是Htotal增加一倍，因此会有足够的Data Island Period来传输audio，Htotal增加一倍的后果也有pixel clock会增加一倍。



2 channel PCM can never exceed 192kHZ.



**Audio,Video synchronization:** An HDMI source shall be capable of transmitting audio and video streams no more than +_ 20msec of audio delay ralative to the video.



1个audio sample packet包含4个2 channel L-PCM的采样

1个audio sample packet包含1个8 channel L-PCM的采样



**audio sample packet**：layout 0 for 2 channel L-PCM或IEC61937 compressed audio（fs<=192kHZ, 大于192kHZ的用High-Bitrate audio stream packet）, layout 1 for L-PCM multi-channel



**High-Bitrate audio stream packet**：when carrying IEC61937 compressed audio at frame rate above 192kHZ, the High-Bitrate audio stream packet shall be used. For many high bitrate streams (e.g. DTS-HD Master Audio and Dolby MAT), the IEC61937 data burst will have a repetition period that is multiple of four frames因为一个packet能包含4个frame, and so the Pa and Pb syncwords will always be found in the same subpacket. In such cases, the codec vendor may impose the additional constraint that Pa and Pb always appear in subpacket 0. Each packet carries four contiguous IEC60958 frames which corresponds to (4 * 2 * 16=) 128 bits of an IEC61937 stream.



**Audio Return Channel**:  The audio return channel features allows an HDMI Sink to transimit an IEC60958 audio stream in the reverse direction to the TMDS path to an HDMI source or an HDMI repeater. The Utility line alone (single mode) or the Utility line in conjunction  with the Hot  Plug Detect line (common mode) may be used for ARC transmission.



**Audio InfoFrame**: 

1. Audio Infoframe 至少每帧发送一次

2. Audio InfoFrame shall be transmitted no later than one video field following the first affected non-silent audio sample. 正常来讲，Audio Infoframe在audio packet发送之前就发送。

3. * **Channel Count **（可填0 refer to stream header，也可以填channel count实际值）

   * Coding Type（0，refer to stream header ）

   * Sample Size （0，refer to stream header ）

   * Sample Frequency（0，refer to stream header ）

   * **Channel  Speaker Allocation **(只对multi-channel L-PCM有效，因为它的data中不包含这部分信息，只能从audio infoframe中拿，而对于其他例如IEC61937 audio stream，它的data中会包含这部分信息，不用从audio infoframe中获取)

     > speaker placement :
     >
     >  Front 
     >
     > ​			FL - FLC - FC - FRC - FR
     >
     > ​													LFE
     >
     > ​			RL - RLC - RC - RRC -RR
     >
     > Rear
     >
     > ***FL*** : front left
     >
     > ***FLC*** : front left center
     >
     > ***LFE***: low frequency effect

   * LSV0…LSV3 (Level shift value, for downmixing)

   * DM_INH (Donwmix Inhibit,只针对DVD audio应用下才设置为1)

   * LFEPBL0，LFEPBL1