平台：Bugku
题目：入门逆向
分类：Reserve

下载题目所给附件，得到名为“file”的压缩包，解压缩得到名为“baby”的exe程序。
<img width="349" height="246" alt="Image" src="https://github.com/user-attachments/assets/5fa5f0c7-8db0-4ab9-8a33-9292c49ff34a" />

拿到程序baby.exe，是Windows下32位PE可执行文件。
常规逆向思路：先查看字符串，若字符串中无flag，则进入main函数阅读程序逻辑。
用IDA加载baby.exe，加载格式选择 80386可执行文件（PE）[pe.dll]，保持其余参数默认，等待IDA自动分析完成。
<img width="2521" height="1622" alt="Image" src="https://github.com/user-attachments/assets/da2d61a2-2747-42cb-8c55-7e70cd67ffa4" />

查看字符串：顶部【视图】→【打开子视图】→【字符串】，检索 flag 关键词，没有找到目标flag字符串。打开函数列表：顶部【视图】→【打开子视图】→【函数】，在函数列找到 _main （gcc编译生成的主函数，名称带下划线），双击进入 _main 函数汇编代码页面。发现flag为单个字节纵向排列。
<img width="3071" height="1919" alt="Image" src="https://github.com/user-attachments/assets/face1ec1-ccce-4dbb-befe-620fffc8d448" />

直接读取汇编注释即可拿到flag，提交flag，flag正确，完活。
