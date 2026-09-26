平台：Bugku
题目：瑞士军刀
分类：PWN 入门
考点：netcat (nc，网络瑞士军刀)，熟悉 TCP 连接、基础 Linux 命令，无漏洞，纯交互式连接

点击【启动场景】，平台给出一行连接指令：nc ip端口。
复制平台所给端口，在kali虚拟机的终端上切换至root模式输入：
nc ip端口

连上之后，进入一个交互式 Linux shell。查看当前目录：
ls

会看到多个文件，其中就有文件flag，查看文件flag：
cat flag

得到flag，提交，完活。

