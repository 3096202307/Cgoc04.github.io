平台：Bugku CTF
题目类型：Web
题目名称：source
考察知识点：.git源码泄露、git reflog恢复被删除的提交记录

访问题目所给靶机地址，页面处未找到falg，Ctrl+U查看网页源代码得到“flag”，提交“flag”显示flag错误，判断flag不带当前页面。题目名为 source ，提示需要获取网站源码，判断发生源码泄露尝试访问 /.git 目录，确认存在git源码泄露漏洞。
通过kali虚拟机使用wget递归下载整个.git目录：
wget -r http://靶机地址/.git/

wget会生成以靶机IP端口命名的文件夹，进入该目录：
cd 靶机地址
ls -a

执行 ls -a 可以看到隐藏的 .git 文件夹，确认是完整git仓库。

使用 git reflog 查看仓库所有操作记录（ git log 只能查看当前分支有效提交记录，被reset删除的记录需要reflog查看）：
git reflog

发现3个commit编号 ******* 为包含flag的提交，使用 git show 查看该三个commit提交详情：
git show commit编号

随后得到三个flag，依次提交得到正确的flag，完活。
