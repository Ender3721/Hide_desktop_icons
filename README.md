# Hide_desktop_icons
这是一个可以隐藏桌面图标的小应用程序的配置，我故意保留了任务栏，因为这会让程序调用方便，对我而言应用场景是直播或则录制视频，我不希望桌面上的大量图标泄露个人信息，参考高人的代码和仓库修改完成，由于我个人是一个代码小白，在这个仓库中我也会尽可能的写的直白，方便真正使用。
# 核心文件源代码
参考https://blog.csdn.net/qq_39529180/article/details/132375276  <br/>
，编译打包成了.exe（应用程序）文件，可以直接在win7以上系统运行  <br/>
点击这里即可下载https://github.com/Ender3721/桌面图标隐藏.exe  <br/>

# 优化使用体验
推荐使用autohotkey，其是一个自由开源的编程语言，其官网提供了下载：https://www.autohotkey.com/  <br/>
可以通过**记事本**编辑其脚本文件（后缀为.ahk），可以自己新建也可以直接下载我仓库中提供的，关于快捷调用这里有几点说明： <br/><br/>
**1.语法**  <br/>
可以在启动autohotkey后在其help files选项里查看语法  <br/>
![image](https://github.com/user-attachments/assets/f92b6976-64df-4c94-94fe-7db644e6a3b4) <br/>
在这里简单介绍一下我用到的部分  <br/>
我的脚本文件为：  <br/>

#Requires AutoHotkey v2.0  

!h::Run "C:\Users\86134\Desktop\桌面图标隐藏.exe"

第一个要求了使用AutoHotkey v2.0版本，其v1.1版本已经deprecated即弃用了  
第三行则就是快捷键的要求，不同符号对应不同的按键，常用的有： Ctrl (^), Alt (!), Shift (+) , Win (#)。!h的意思就是我按alt+H后会run 后面的“ ”里的文件，这里我设置为仓库中的 桌面图标隐藏.exe 的文件目录了  
这个案例提供了一个简单高效的链接快捷键的方法  
**2.开机后即自动监测的方法**  <br/>
经实践，可能的正确理解是，当启动.ahk文件后，对于快捷键这个案例，程序就开始监测键盘，然后监测到输入对应快捷键后就运行脚本指定程序。由此可知，要实现开机后自动监测，我们只需要将脚本.ahk文件放入开启自启文件夹即可，我的自启文件夹在 
 C:\Users\86134\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup，即C盘/用户/用户名/应用数据/漫游？/微软/Windows系统/开启菜单/程序们/启动，这个里面的程序一般在电脑开机后都会运行一遍，这样便进入监测键盘的逻辑了！也就是说我们需要把写好的.ahk脚本文件放到这个文件夹中，这样便实现了开机后即自动监测。  
**3.关于autohotkey的其他情况**  <br/>
当我安装完这个autohotkey程序后，我发现其文件目录下的.exe文件无法启动它本身（会报错），探索后发现启动autohotkey的正确姿势是**打开launcher.ahk（目录为.\autohotkey\UX\launcher.ahk，也就是安装目录）**，也就是说当安装完autohotkey后，.ahk文件就和.exe文件一样可方便快捷地运行
