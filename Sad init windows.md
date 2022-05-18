# Sad Windows 重装系统及其初始化规范

## 历史渊源

Windows 系统用上一段时间，我就有想重装的冲动，而每每重装，都想总结一套符合我习惯的重装规范，来指导每次的「冲动」。

## 系统安装

一般来说，重装系统你需要：

1. 一个非系统盘的存储空间；
2. 系统镜像文件；

而根据你的安装环境，又可以分为两种情况：

1. 计算机无操作系统或计算机操作系统为非 Windows 操作系统、 Windows 操作系统版本不支持安装目标版本操作系统，这种情况你需要做一个系统 PE 盘来辅助安装。
2. 计算机系统为支持安装目标版本操作系统的 Windows 操作系统，这种情况需要将系统镜像放在非系统盘的存储空间中进行安装。

第一种情况需要查阅检查主板的 BIOS 设置 U盘启动进行安装，第二种情况直接傻瓜式运行就可以安装了。

## 系统配置（纯属个人喜好）

1. 用户账户控制设置为从不通知；
2. 连接蓝牙键盘和鼠标；
3. 设置双拼模式，规则为[小鹤双拼](https://github.com/sad912/sad-tricks/blob/main/setting%20flypy%20in%20win11.md)；
4. 打开剪贴板历史记录；
5. 多任务处理中 Alt + Tab 设置为「仅打开的窗口」；
6. 更新系统；
7. Mono font 字体安装；

## 软件安装（纯属个人喜好）

很早之前，我总会修改软件的默认安装目录，后来才知道 Program Files 是系统的默认安装目录，软件开发人员如果遵循规则会默认安装到此目录，在这之后，我一般会遵循这个默认规则，然后检查软件的设置，是否有保存文件到其他目录的设置。

1. 火绒
2. [Clask for Windows](https://dl.trojan-cdn.com/trojan/windows/)
3. Bandizip
4. 开黑啦
5. WPS Office 国际版
6. Git
   1. 生成SSH 密钥
   2. 添加公钥到 Github
7. pnpm
   1. 安装最新版本 Node.js `pnpm env use —global latest`
8. Steam
9. Foxmail
10. Anaconda
11. Pycharm
12. WebStrom
13. PotPlayer
14. 飞书
15. npm fanyi
16. iTues
17. WeChat（极其不情愿）

