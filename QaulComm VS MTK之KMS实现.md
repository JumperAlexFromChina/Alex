1. mtk的hdmi实现，在dts中有4个节点，节点数过多，不便于统一管理
2. mtk的hdmi没有加入component机制中，与DSI，DPI这些模块在初始上不统一
3. QualComm DRM初始化时，先抽象一般的硬件资源，例如reg，irq，clk等等，最后在component机制的最尾部来抽象出DRM object，如plane，crtc, encoder, bridge, connector, 并完成这些DRM object之间的关系链接，例如绑定crtc与plane的关系，绑定bridge，connect和encoder的关系； 而mtk的初始化，把抽象一般硬件资源和抽象drm object混在一起了，代码清晰度不如QualComm

---

**QaulComm DRM init process:**

module_init(msm_drm_register)

* 在每个子模块（包含HDMI，DSI，mdp，edp等）的probe中仅仅调用component_add（），并不直接调用每个子模块的.bind函数。component的.bind函数实现的都是对硬件资源的抽象，譬如获取reg，irq，clk，注册phy等等；

* 最后主模块probe的时候调用component_master_add_with_match（）

  > msm_drm_bind
  >
  > > msm_drm_init
  > >
  > > >component_bind_all(),会依次调用子模块的.bind函数
  > > >
  > > >mdp4_kms_init(),会依次抽象drm object并完成bind
  > > >
  > > >> modeset_init()
  > > >>
  > > >> > mdp4_plane_init, mdp4_crtc_init
  > > >> >
  > > >> > mdp4_modeset_init_intf
  > > >> >
  > > >> > > mdp4_dtv_encoder_init
  > > >> > >
  > > >> > > msm_hdmi_modeset_init
  > > >> > >
  > > >> > > > msm_hdmi_bridge_init
  > > >> > > >
  > > >> > > > msm_hdmi_connector_init

---

**msm_drm_init:**

​	*drm_dev_alloc*

​		platform_device->device->driver_data = drm_device *;

​		对drm_device内的变量赋值

​		drm_device->dev_private = msm_drm_private *, msm_drm_private包含整个drm下msm所有的资源，reg，clk等等

> platform_device
>
> > drm_device
> >
> > > msm_drm_private

​	*drm_dev_register*



---



找时间看一下QualComm dts的写法：
hdmi模块分成两个节点，一个phy，一个主节点
