## Win+R ##
----

1. cmd => 命令行
2. lpksetup => 弹出安装或者卸载Windows显示语言
3. ipconfig => 查看IP配置
4. dcpromo => Windows Server 安装域控制器
5. compmgmt.msc =>直接打开计算机管理
6. msconfig => 打开Windows配置
7. services.msc =>打开windows服务
8. control =>打开控制面板
9. mstsc=>打开远程连接
 

## CD

----

*cd的全称是Change Directory，直译为改变文件夹，也就是跳转目录、切换路径的意思。它后面可以接驱动器符号、完整路径和相对路径。*
一般我们打开命令行窗口的时候，默认的目录位于当前用户所在的路径下，比如：`C:\Documents and Settings\jacran>`

1. 跳转到当前驱动器的根目录
    cd [当前驱动器盘符]:\ 例如： cd c:\  或者更简单的 cd\
2. 跳转到当前驱动器的其他文件夹
    以C盘下的WINDOWS文件夹为例 输入：cd C:\WINDOWS
3. 跳转到其他驱动器 
    以从C盘跳转到D盘为例 在任意目录下直接输入： D:
4. 跳转到其他驱动器的其他文件夹
    假设当前在C盘，要跳转到E的software目录 cd /d e:\software
    注意此处必须加/d参数。否则无法跳转。
5. 跳转到上一层目录
    cd..



## Command

---

1. Win+R => cmd => net user username /active:no 禁用某个用户名
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 