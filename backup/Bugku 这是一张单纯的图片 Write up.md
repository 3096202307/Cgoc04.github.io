平台：bugku
题目：这是一张单纯的图片
分类：MISC（杂项）

题目给出一张 jpg 图片，提示 flag 格式为`key{}`，从图片肉眼观察看不到任何信息，需要从文件本身寻找隐藏内容。

下载图片，保存为`1.jpg`。
![题目](/Cgoc04.github.io/static/ti.png)

用Windows自带的记事本打开该图片，发现是一堆乱码。
![乱码](/Cgoc04.github.io/static/luanma.png)

下拉找到`&#***;`形式的 HTML 实体编码字符串。
![编码](/Cgoc04.github.io/static/bianma.png)

使用HTML解码工具对该编码进行解码后得到flag。
![flag](/Cgoc04.github.io/static/flag.png)

提交flag，flag正确，完活。