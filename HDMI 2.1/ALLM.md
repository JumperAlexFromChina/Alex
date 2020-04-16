10.11 Auto Low-Latency Mode

Auto Low-Latency Mode (ALLM) allows a Source to enable or disable a Sink's low-latency mode feature automatically without requiring the user to navigate a Sink's menus to set the optimal latency for their content. For more information, see Appendix G.

A Sink that supports a feature for reducing latency may support ALLM. A Sink that supports ALLM may have its low-latency mode enabled and disabled either: a) manually via menu navigation, or b)automatically via the ALLM feature.

Sinks supporting ALLM shall set(=1)the ALLM bit in the HF-VSDB (see Section 10.3.2)

![IMG_1027](./picture/IMG_1027.jpg)

If the ALLM bit is set (=1) , a Source may set(=1) the ALLM Mode bit in the HF-VSIF. A Source shall not set the ALLM bit in HF-VSIF unless the ALLM bit is set(=1)in the Sink's HF-VSDB.

![IMG_1029](./picture/IMG_1029.jpg)

Figure 10-18 shows how Sinks should change their low-latency mode based on input variables. Transition from a non-low-latency mode to a low-latency mode is the logical OR of ALLM Mode and the Sink's menu setting: if the Source transmits ALLM_ Mode=1 OR the user selects a low-latency mode in the Sink, then the Sink shall transition to its low-latency mode. If the Source is transmitting ALLM- Mode=0 AND the user has selected a non-low-latency mode, the Sink shall transition to its previous mode. Implementing a menu setting for low-latency mode in the Sink is optional; in such a case, low-latency mode is driven only by ALLM Mode.**是否进入LLM，由HF-VSIF中的ALLM bit决定，与菜单中LLM的设定是否相关是可选的。**

![IMG_1031](./picture/IMG_1031.jpg)



When an ALLM capable Sink receives an HF-VSIF with ALLM_Mode set(=1), it should enable its low-latency mode within 1 second. A Sink shall exhibit the same behavior whether its low-latency mode is enabled due to ALLM signaling or through use interatction(e.g. using on-screen menus). If a  Sink's Low-Latency mode is already enabled, either manually or automaticatically, the receipt of an HF-VSIF with ALLM Mode set (=1)shall have no discernible effect on the presentation of video or audio.

When the Sink receives an HF-VSIF with ALLM_Mode cleared (=0) and user interaction is not requesting low-latency mode, the Sink should revert to its previous mode within 1second. For example, if a display is

in "Cinena" mode and ALLM changes to =1, the display should change to its low-latency mode(say, "Game"). When ALLM changes again(=0), the display should go back to "Cinema"mode. If the user had already selected low-latency mode, then ALLM transition shall have no discernible effect.

To prevent disruption of the user's audio/video experience, when ALLM causes the low-latency mode to change, the Source shall not display a notification message. (意思是不发CEC OSD message？)

To prevent disruption of the users audio/video experience, when ALLM causes the low-latency mode to change, the Sink should limit video and audio content not directly derived from the video and audio received from the Source. Unrelated video(e. g. black or corrupted sceen, a notification message, etc.)shall not be displayed for more than one second. Unrelated audio (e.g. indication chimes, clicks, pops, etc.) shall not be rendered. After the Sink receives at HF-VSIF with ALLM Mode set (=1)and changes the latency setting, the new latency setting shall persist until there is a mode change, HF-VSIF packets are no longer sent, or there is a hot-plug event.

Devices that implement ALLM should implement the mechanisms defined in This Specification for synchronizing Audio and Video, See Dynamic Auto Lip Sync(Section 10,7. 2) for more information.





**Appendix G Auto Low-Latency Mode( Informative)**

Auto Low- Latency Mode (ALLM)(Section 10. 11) is a control feature that allows a Repeater or a Sink with a low latency Mode (LLM) (commonly called the"Game Mode" feature) to entrust the configuration of that feature to the Source device as opposed to the user. This allows the Source to anticipate the users preference based on the of the experience, and then forward that preference downstream to Repeaters and Sinks on behalf of the user. The feature thus off-loads the user from having to manually change the settings in various downstream Repeaters and Sinks using those devices' individual menus and remotes when the user switches between different types of content. For example, a user could be watching a movie when they receive an incoming video call. The Source could pause the commencement of the video call. When the user completes the call and wishes to resume playback of the movie, the ALLM feature can be used to return the devices back to their normal- latency configuration.

Downstream Sinks and Repeaters may disable some picture enhancement modes to achieve a lower latency, therefore, automatic activation of other devices' Low-Latency Modes should only be considered for applications that would truely benefit. If the application is latency-sensitive(e. g, game, video conferencing, etc. ) the Source should enable LLM using the ALLM feature. If the application is not latency-sensitive(e.g. movie, TV, etc.), the source should disable LLM using the ALLM feature. If the application changes (e. g, movie to/from game), the Source should enable or disable LLM using the ALLM feature as appropriate for the new application.



**The Relationship Between ALLM and the Content Type Feature**

The Content Type feature a llows the Source to inform downstream Devices when it deems that the content falls into one of four special categories: "Graphics", "Photo", "Cinema", or "Game". CTA 861-G provides recommendation for Sink Signal processing that would be the most appropriate for content htat has been placed into these categories. For example, it states, "when the IT content bit is set to 1 and the Game type is indicated, the Sink should "pass-through" game content with minimal scaling and picture enhancement  in order to avoid undesirable artifacts. Audio and video latency should be minimized. The Game type should not be associated with device type. For example, game machines are capable of supplying various content types such as DVD movies.

When content does not fall into one of the predefined Content Type categories, the Content Type feature does not make any recommendations. ALLM provides a mechanism for entering into a low-latency mode in these cases. For example, ALLM can be used in applications that will be benefit from reduced latency but where content is not game content, such as video conferencing and touch applications.



Table G-1 summarize recommended operation for Sink as function of the AVI InfoFrame Packet ITC and CN1,CN0 settings

![IMG_1023](./picture/IMG_1023.jpg)

Recommendation A: Assume that the content delivered is of high image quality and does not need additional image processing to improve it. Present the images with the lowest latency possible.

Recommendation B: Strive to deliver an optimal balance between best picture quality and low-latency. The right balance may depends on the target market for the device.

Recommendation C-F: Refer to CTA-861-G Section 6.4(fields ITC and CN)



ALLM does not replace the Content Type feature.

A both the ALLM and Content Type feature are optional, an adopter may implement neither, either, or both of these features.