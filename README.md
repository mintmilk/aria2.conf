# Aria2 树莓派(raspberry pi)配置


本项目是一套树莓派上的 Aria2 配置方案，全部fork大佬配置😄，包含了配置文件、附加功能脚本等文件，用于实现 Aria2 功能的增强和扩展，提升 Aria2 的使用体验，解决 Aria2 在使用中遇到的 BT 下载无速度、文件残留占用磁盘空间、任务丢失、重复下载等问题。

## 功能特性

* BT 下载率高、速度快
* 重启后不丢失任务进度、不重复下载
* 下载错误或取消下载自动删除未完成的文件防止磁盘空间占用
* 下载完成自动清除`.aria2`后缀名文件
* 一键获取 BT tracker，进一步提升 BT 下载速度
* 更好的 PT 下载支持
* 防版权投诉、防迅雷吸血
* 联动 RCLONE 自动上传

## 文件说明

`aria2.conf` - Aria2 配置文件。除非你对这些参数非常了解，否则修改后可能导致特性失效。

### 附加功能脚本

> **TIPS:** 脚本需配合配置文件使用，仅适用于 GNU/Linux

`autoupload.sh` - 自动上传脚本：在下载完成后执行([on-download-complete](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-on-download-complete))，调用 Rclone 上传(move)下载的文件到网盘，并删除 `.aria2` 后缀名文件。（默认不启用）

`delete.aria2.sh` - `*.aria2`文件删除脚本：在下载完成后执行([on-download-complete](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-on-download-complete))，删除 `.aria2` 后缀名文件。（默认启用）

`delete.sh` - 删除脚本：在下载停止后执行([on-download-stop](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-on-download-stop))，删除文件及 `.aria2` 后缀名文件。（默认启用）

`info.sh` - 任务信息显示脚本：在下载暂停后执行([on-download-pause](https://aria2.github.io/manual/en/html/aria2c.html#cmdoption-on-download-pause))，输出下载任务信息到日志中。（debug 专用）

`tracker.sh` - BT tracker 获取脚本：在 Aria2 配置文件(`aria2.conf`)所在目录执行即可获取[最新 tracker 列表](https://raw.githubusercontent.com/XIU2/TrackersListCollection/master/all.txt)并添加到配置文件中。执行`bash <(wget -qO- git.io/tracker.sh)`命令获取最新脚本并直接运行。其它使用方法详见[这里](https://p3terx.com/archives/solved-aria2-cant-download-magnetic-link-bt-seed-and-slow-speed.html)。

### DHT 文件

提升 BT 下载率和下载速度的关键之一。相关科普：《[解决 Aria2 无法下载磁力链接、BT种子和速度慢的问题](https://p3terx.com/archives/solved-aria2-cant-download-magnetic-link-bt-seed-and-slow-speed.html)》

`dht.dat` - DHT（IPv4）文件

`dht6.dat` - DHT（IPv6）文件（目前数据为空，仅用作占位）


## 声明

本项目使用 [MIT](https://github.com/P3TERX/aria2.conf/blob/master/LICENSE) 开源协议，对于本项复制、修改、发布等行为请遵守相关协议，并保留所有文件顶部的版权信息。
