# ASUS-FL8000UQ-Hackintosh

* 项目基于[ alexanderkin /
ASUS-FL8000UQ-Hackintosh ](https://github.com/alexanderkin/ASUS-FL8000UQ-Hackintosh) ，请先阅读原项目说明。

* 该仓库相比于原仓库相比，无线网卡使用的是Intel 9260AC。

* 此配置文件改动很少，只是帮助友人安装。他的设备状况不是很好，触摸板、麦克风等一些硬件都有问题（在Windows下都无法使用），所以这些硬件并不知道是否正常工作。

* 由于是帮友人安装的，设备的所有者和使用者都不是本人，无法确定长时间使用会不会出现 bug。对于设备只进行了短时间的测试，配置文件的之后可能不会进行更新，仅仅是分享一下最后可用的配置文件。

* **使用前请务必按照原仓库的说明，三码一定要进行重新生成再使用！！**

## 配置改动

1. 新增对 Intel 9260AC 无线网卡 `WIFI` 功能的支持，感谢[ OpenIntelWireless ](https://github.com/OpenIntelWireless)项目。

    * itwlm项目有两种驱动，一个是 `itlwm.kext`，开源的，使用IOEthernet，另一个是 `AirportItlwm.kext`，逆向工程的，使用IO80211Family。本项目使用的是 **AirportItlwm**（itlwm不知为何无法正常使用。）

    * AirportItlwm 需要额外操作，这里选择的是第二种方法：Force IO80211Family to load. 「Supports OpenCore and Clover(not tested)」

    * 如果你使用的并不是 9260AC，而是其他的 Intel 无线网卡，可以在[ OpenIntelWireless Compatibility ](https://openintelwireless.github.io/itlwm/Compat.html)中寻找是否在支持范围中。

2. 新增对 Intel 9260AC 无线网卡`蓝牙`功能的支持，同样感谢[ OpenIntelWireless ](https://github.com/OpenIntelWireless)项目

3. 更新 OpenCore 到 0.8.4 ，更新驱动文件至最新（2022年9月8日）。

4. 更改为图形选择菜单，选择等待时间调为 1 秒，并删除 `-v` 启动参数，关闭跑码。

## 相关测试

* **CPU** 运行正常，可以变频
* **核显** H.264 硬解正常，H.265 硬解测试未通过。不清楚是不是特殊原因，如果你使用了该项目发现的确无法硬解，可以提交一个 Issues 来确定这个问题存在。
* **WIFI** 使用正常
* **蓝牙**可以搜索到设备，但是未测试功能是否可用
* 内置**音响**正常
* 内置麦克风、触摸板无法测试。
* 可以关闭盖子**休眠**，开盖电源键唤醒正常。
* **电池**正常识别
