# Box64Droid-For-Chinese
本项目基于https://github.com/Ilya114/Box64Droid

安装方式(proot版)
安装Box64Droid后，运行curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/box64droid/install && chmod +x install && ./install，即可配置中文wine环境，并自动安装中文字体。

安装方式(chroot版)
安装Box64Droid后，运行curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/box64droid/install-root && chmod +x install&& ./install，即可配置中文wine环境，并自动安装中文字体。

经研究，proot上部分游戏崩溃，是因为proot的文件连接数太低导致的，proot上文件数限制为1024，使用显卡加速时（不管virgl还是dvxk），在proot上都不会及时的释放已经使用的数据。
因此，proot上的中文化补丁，现在默认会解开proot的限制，理论上可以提升proot的稳定性（待测试）
如需恢复，只需在termux上输入
cp -f $PREFIX/var/lib/proot-distro/installed-rootfs/ubuntu/etc/security/limits.conf.bakup
 $PREFIX/var/lib/proot-distro/installed-rootfs/ubuntu/etc/security/limits.conf
 
若此前已经安装过中文补丁，需运行以下指令
(proot版）curl -o start https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/start  && cp -f start $PREFIX/var/lib/proot-distro/installed-rootfs/ubuntu/opt/start
(chroot版）
curl -o start https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/start  && sudo cp -f start ~/ubuntu/opt/start

5月23更新
添加快捷启动，安装中文补丁后，可在termux输入pbox，vbox，cbox进行快捷启动(分别对应start-box，start-box-virgl，start-box-root)
首次启动需要输入分辨率，此后再次启动会直接进入
如需变更分辨率，可用对应start-box进入游戏
另外添加快捷启动run.bat到d盘。默认启动ib。
如删掉该文件，会自动切换回原有启动。也可自行编辑run.bat达到不同的启动目的。若文件含有中文，需保存为ansi编码。

5月25更新
更改changewinever文件，在更新wine时，先检测在download/wineversions文件夹中是否存在离线版本。若存在，直接使用离线版本进行更新。
正常下载更新时，同样会备份一份到download/wineversions文件夹，以后再更新无需重新下载。
同样，下载不完全导致更新失败，则需手动删除download/wineversions的对应文件。
changewinever中若存在“复制”和“安装”字样，则会跳过对changewinever的更新（方便制作整合的人员使用和识别）

5月28更新
<p>新增定制版termux-x11（由本人进行汉化，java部分由补补23456完成），定制版termux添加以下功能：</p>
<p>1、termux-x11全汉化</p>
<p>2、termux-x11添加全屏居中功能（预设分辨率或自定义分辨率时生效）</p>
<p>3、termux-x11设定的分辨率，输出到手机存储\Download\resolution.conf（需手动赋予termux-x11存储权限,变更分辨率需设置分辨率后返回初始界面才会生效）</p>
<p>4、快捷启动对定制版termux-x11进行优化，若存在手机存储\Download\resolution.conf文件，启动box64droid时无需再次手动输入分辨率</p>

6月1日更新
鉴于box4droid现在已经处于可用状态(另一个box版本，非box64droid)，因此，将termux-11的分辨率文件resolution.conf输出目录从Box64Droid文件夹改成Download文件夹。方便对其他版本的适配

6月2日更新一
更新E盘，位置位于/data/data/com.termux/files/home/drive_e/，增加E盘的原因，是因为每次更新box64droid后，C盘和Z盘的空间都会重置，需要重新导入数据。
因此增加E盘，作为日常存放游戏的目录。box64droid更新时，E盘的数据不会清除，更新后，只需重新打box64droid汉化补丁即可使用。

6月2日更新二
增加box4droid0.0.3版的简易中文补丁，可通过curl -o install https://raw.githubusercontent.com/lsl330/Box64Droid-For-Chinese/main/box4droid/0.0.3/install && chmod +x install && ./install进行安装
<p>简易补丁特点：对定制版X11进行适配，只需要在x11中变更分辨率即可使用，添加中文支持，添加E盘，数据可以与box64droid共用，box64droid中更换wine版本，需要重新下载中文补丁进行安装</p>

6月3日更新
增加box4droid脚本中文化，变更wine脚本添加检测离线脚本包功能，添加自定义下载wine版本功能，变更wine后自动配置中文。
另外，ib功能需要在脚本里手动开启。需要在ib选择“蒋安装程序”复制到下载，即download文件夹有ib的安装文件，才能正常安装。
