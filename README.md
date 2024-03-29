# Box64Droid-For-Chinese  
本项目基于https://github.com/Ilya114/Box64Droid  
安装方式(native版)，运行以下命令进行配置  
curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/box64droid/install && chmod +x install && ./install  
native版已经足够，不再支持proot和chroot版  

# Box4Droid-For-Chinese  
本项目基于https://github.com/Herick75/Box4Droid  
安装Box4Droid后，运行以下命令进行配置  
curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/box4droid/0.0.3/install && chmod +x install && ./install

# Mobox-For-Chinese  
本项目基于https://github.com/olegos2/mobox  
安装mobox后，运行以下命令进行配置，只做了中文化，尚未汉化菜单  
curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/mobox/install && chmod +x install && ./install  

# Box64Droid-For-Chinese 和 Box4Droid-For-Chinese的共同修改  
1、添加中文，并可在更换wine版本时自动切换中文  
2、在更新wine时，先检测在download/wineversions文件夹中是否存在离线版本。若存在，直接使用离线版本进行更新。  
3、添加E盘，位置在/data/data/com.termux/files/home/drive_e/，该空间不随官方更新而删除，可将游戏存放在E盘减少不必要的数据迁移  
4、打上proot突破限制补丁，对一些游戏在proot上的闪退会有所帮助  
5、与定制版termux-x11关联，具体介绍相见termux-11中相关介绍  

# Box64Droid-For-Chinesed 单独优化    
1、添加pbox、vbox、cbox作为proot-dvxk、virgl、chroot版本的快捷启动命令，只需输入pbox、vbox、cbox即可进入对应的环境，若需进入设置项，可以输入startbox、startbox-virgl、startbox-root进入设置  
2、添加快捷启动run.bat到d盘。该文件存在与否同时会作为是否后台启动ib的判定，如删掉该文件，会自动切换回原有启动。  
   另外，可自行编辑run.bat达到不同的启动目的（如使用命令启动后，自动运行相关游戏）。需要注意的是，若run.bat含有中文，需保存为ansi编码方可正常识别。  
3、可使用lang、lang-root快捷切换proot和chroot的wine语言环境。
   
# Box4Droid 的注意事项    
ib功能需要在脚本里手动开启。需要在ib选择“蒋安装程序”复制到下载，即download文件夹有ib的安装文件，才能正常安装。  

# 为何要打proot突破限制补丁的原因  
经研究，proot上部分游戏崩溃，是因为proot的文件连接数太低导致的，proot上文件数限制为1024，使用显卡加速时（不管virgl还是dvxk），在proot上都不会及时的释放已经使用的数据。
因此，proot上的中文化补丁，现在默认会解开proot的限制，理论上可以提升proot的稳定性（待测试）  
如需恢复，只需在termux上输入  
(box64droid版本）cp -f $PREFIX/var/lib/proot-distro/installed-rootfs/ubuntu/etc/security/limits.conf.bakup $PREFIX/var/lib/proot-distro/installed-rootfs/ubuntu/etc/security/limits.conf  
(box4droid版本）cp -f ~/Box4Droid/ubuntu/etc/security/limits.conf.bakup ~/Box4Droid/ubuntu/etc/security/limits.conf  

# 定制版x11  
定制版termux-x11（由本人进行汉化，java部分由补补23456完成），定制版termux添加以下功能：  
1、termux-x11全汉化  
2、termux-x11添加全屏居中功能（因官方已添加居中功能，已合并到官方上游代码）  
3、termux-x11设定的分辨率，输出到手机存储\Download\resolution.conf（需手动赋予termux-x11存储权限,变更分辨率需设置分辨率后返回初始界面才会生效）  
4、快捷启动对定制版termux-x11进行优化，若存在手机存储\Download\resolution.conf文件，启动box64droid时无需再次手动输入分辨率
