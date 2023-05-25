# Box64Droid-For-Chinese
本项目基于https://github.com/Ilya114/Box64Droid

安装方式(proot版)
安装Box64Droid后，运行curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/install && chmod +x install && ./install，即可配置中文wine环境，并自动安装中文字体。

安装方式(chroot版)
安装Box64Droid后，运行curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/install-root && chmod +x install&& ./install，即可配置中文wine环境，并自动安装中文字体。

经研究，proot上部分游戏崩溃，是因为proot的文件连接数太低导致的，proot上文件数限制为1024，使用显卡加速时（不管virgl还是dvxk），在proot上都不会及时的释放已经使用的数据。
因此，proot上的中文化补丁，现在默认会解开proot的限制，理论上可以提升proot的稳定性（待测试）
如需恢复，只需在termux上输入
cp -f $PREFIX/var/lib/proot-distro/installed-rootfs/ubuntu/etc/security/limits.conf.bakup
 $PREFIX/var/lib/proot-distro/installed-rootfs/ubuntu/etc/security/limits.conf

5月23更新
添加快捷启动，安装中文补丁后，可在termux输入pbox，vbox，cbox进行快捷启动(分别对应start-box，start-box-virgl，start-box-root)
首次启动需要输入分辨率，此后再次启动会直接进入
如需变更分辨率，可用对应start-box进入游戏
另外添加快捷启动run.bat到d盘。默认启动ib。
如删掉该文件，会自动切换回原有启动。也可自行编辑run.bat达到不同的启动目的。若文件含有中文，需保存为ansi编码。

5月25更新
更改changewinever文件，在更新wine时，先检测在downloads/wineversions文件夹中是否存在离线版本。若存在，直接使用离线版本进行更新。
正常下载更新时，同样会备份一份到downloads/wineversions文件夹，以后再更新无需重新下载。
同样，下载不完全导致更新失败，则需手动删除downloads/wineversions的对应文件。
changewinever中若存在“复制”和“更新”字样，则会跳过对changewinever的更新（方便制作整合的人员使用和识别）
