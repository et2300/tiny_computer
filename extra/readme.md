## 这个readme介绍assets文件夹中文件的制作方式。

### assets.zip中的文件：

- [proot](https://github.com/Cateners/proot), 使用[build-proot-android](https://github.com/green-green-avk/build-proot-android)脚本编译
- [busybox](https://github.com/meefik/busybox)
- [mediamtx相关](https://github.com/bluenviron/mediamtx)
- [tar](https://github.com/Rprop/tar-android-static)
- [Xserver XSDL, pulseaudio相关文件](https://github.com/pelya/commandergenius/tree/sdl_android/project/jni/application/xserver)
- [Tmoe Linux, debian包来源](https://github.com/2moe/tmoe)
- [容器文件xa*](build-tiny-rootfs.md)

其中tar、busybox和pulseaudio相关文件都是直接用了二进制文件。

### patch.tar.gz中的文件：

#### extra/getifaddrs_bridge_client_lib.so:

在安卓13以上的系统中，proot容器无权使用默认的getifaddrs，而这个库包含了一个getifaddrs实现。

linux在需要数据时，使用socket通知位于安卓的getifaddrs_bridge_server，让getifaddrs_bridge_server执行getifaddrs函数，并将结构体数据序列化后发送回linux端，这边接收数据并反序列化还原成指针结构体。简单来说就是用安卓的getifaddrs代替linux的getifaddrs。

源码和编译信息在getifaddrs_bridge文件夹查看。

#### caj, edraw

这些分别是cajviewer，亿图图示的补丁

- 亿图图示补丁的库文件是在小小电脑上下载了Qt对应版本源码后编译得到的；
- 编译进行了两次，第一次直接编译，可以得到Gui和Widgets两个库。第二次编译带上XcbQpa，虽然会编译失败，但在这之前就可以得到XcbQpa的库。


