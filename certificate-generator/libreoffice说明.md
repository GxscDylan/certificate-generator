

【LibreOffice】
官网：https://zh-cn.libreoffice.org/
下载地址：https://mirrors.cloud.tencent.com/libreoffice/libreoffice/stable/
教程：https://zhuanlan.zhihu.com/p/614904084
LibreOffice是http://OpenOffice.org办公套件衍生版， 同样自由开源，以Mozilla Public License V2.0分发源代码 [3] ，但相比OpenOffice增加了很多特色功能。（ https://baike.baidu.com/item/LibreOffice/3862237?fr=aladdin ）

LibreOffice 基于开放源代码项目，对于用户完全自由。
LibreOffice 是一套可与其他主要办公室软件相容的套件，包含6大组件：
（1）文本文档【文字处理（word）】
（2）电子表格【计算表（excel）】
（3）演示文稿【简报（powerpoint）】，
（4）公式，绘图【visio】
（5）资料库【access】
（6）HTML【Sharepoint】


LibreOffice和OpenOffice都是免费的开源办公套件软件，由于它们有相似的起源和功能，所以经常被混淆或作为替代品使用。但是，它们不完全相同，存在一些区别。

LibreOffice 是 OpenOffice 的一个分支（fork）项目，它在 2010 年由 OpenOffice 开发者创建。虽然 LibreOffice 和 OpenOffice 共享许多相似点，但 LibreOffice 目前比 OpenOffice 更新、增长更迅速，并且已经实现了若干新特性。此外，LibreOffice 拥有更广泛的社区支持，并提供了更好的互操作性，更好地支持标准化开放文件格式。
从软件界面方面来看，两个软件在使用体验上没有太大差异，基本上有着类似的图标和菜单布局。总体而言，它们可以完成相同的任务，并支持相同的文档格式。
总之，选择 LibreOffice 还是 OpenOffice 取决于您个人的喜好和需求。如果您需要更多功能、更好的互操作性和更快的更新，建议使用 LibreOffice。


【OpenOffice】 安装
https://www.cnblogs.com/abel-he/p/16647082.html
简介：
OpenOffice.org 是一套跨平台的办公室软件套件，能在Windows、Linux、MacOS X (X11)和 Solaris 等操作系统上执行。它与各个主要的办公室软件套件兼容。OpenOffice.org 是免费软件，任何人都可以免费下载、使用及推广它
使用：
在使用程序开发的时候，部分业务需要针对文档(word/excel/html)实现在线预览
解决思路：
借助插件OpenOffice，将文件转换成pdf，将pdf输出到页面进行展示
官方下载地址：
https://www.openoffice.org/download/index.html
可选下载的地址：
链接：https://pan.baidu.com/s/1LBiEF1CidtTKSddVzZty9g?pwd=7alv
提取码：7alv
一、windowns安装：
和平常的安装方式一样唯一要注意的是本地启动方式
1、找到安装openoffice的目录，打开命令窗口cmd
 2、启动窗口命令
soffice.exe -headless -accept="socket,host=127.0.0.1,port=8100;urp;" -npfirststartwizard

该命令的作用是启动一个无头模式（headless mode）的 LibreOffice/OpenOffice 实例，同时使用 TCP/IP 协议监听 127.0.0.1:8100 端口，并在首次启动时自动运行新用户起始向导（New Profile First Start Wizard）。
-headless 选项表示以无头模式运行应用程序，即没有界面；
-accept= 选项表示设置应用程序接受特定协议、端口和选项的远程调用，这使得可以从其他地方发起对 LibreOffice/OpenOffice 的命令请求，此处使用的是 socket 协议并指定监听的主机为本地主机（127.0.0.1），监听的端口号为 8100，同时指定使用 Universal Network Objects (UNO) 进行对象访问和交互。
-npfirststartwizard 选项表示当出现新用户配置文件时，将启动新用户起始向导来配置和设置用户的工作环境。

 3、查看是否启动成功(有图中的信息表示启动成功)
netstat -anop tcp

二、Linux安装：
##解压
mkdir /root/openoffice
tar -zxvf /root/Apache_OpenOffice_4.1.10_Linux_x86-64_install-rpm_zh-CN.tar.gz -C /root/openoffice
cd /root/openoffice/zh-CN/RPMS
yum localinstall *.rpm
cd /root/openoffice/zh-CN/RPMS/desktop-integration
yum localinstall openoffice4.1.10-redhat-menus-4.1.10-9807.noarch.rpm

 ##安装成功后，会在 /opt目录下生成openoffice4文件夹, 即/opt/openoffice4
查看/usr/share/fonts目录是否存在，不存在执行下述命令
yum install libXext.x86_64
yum groupinstall "X Window System"

##添加字体库(ps:不然会出现转换中文字体乱码或直接不显示中文字体) 在 /usr/share/fonts 目录下新建文件夹，windowfonts,
 然后将我们windows系统得字体库文件拷贝到windowfonts下，windows字体库路径

复制代码
/opt/openoffice4/program/soffice.bin -headless -accept="socket,host=0.0.0.0,port=8100;urp;" -nofirststartwizard &

##查看进程
ps -ef|grep openoffice4

##或者
netstat -luntp|grep 8100
复制代码
至此，安装并启动OpenOffice的服务完成，接下来进行Java调用测试
