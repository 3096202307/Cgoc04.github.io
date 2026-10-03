平台：Bugku
题目：.?!
类型：Crypot

下载题目所给附件，得到名为“flag”的txt文本，打开后得到包含“.”、“?”、“!”的一串每五个字符为一组的长字符。
<img width="860" height="896" alt="Image" src="https://github.com/user-attachments/assets/3fe90022-30e6-4d10-a326-5e147b57e4de" />

由于其带有三种字符，不符合摩尔斯密码“.”、“-”形式且字母的编码形式最长只有四位字符，故排除摩斯密码编码，而后我们想到了先前做过的Bugku题目：“ok”，其为Brainfuck/Ook编码方式，我们将“.”视作“Ook.”，将“!”视作“Ook!”，将“?”视作“Ook?”进行解码，得到flag，提交flag，flag正确，完活。



