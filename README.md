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
