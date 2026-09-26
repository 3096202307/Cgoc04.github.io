# Bugku 这是一张单纯的图片 Write up
平台：bugku<br />
题目：这是一张单纯的图片<br />
分类：MISC（杂项）<br />
题目给出一张 jpg 图片，提示 flag 格式为`key{}`，从图片肉眼观察看不到任何信息，需要从文件本身寻找隐藏内容。
下载图片，保存为`1.jpg`。<br />![题.png](/Bugku%20这是一张单纯的图片%20Write%20up/题.png)
用Windows自带的记事本打开该图片，发现是一堆乱码。<br />![乱码.png](/Bugku%20这是一张单纯的图片%20Write%20up/乱码.png)
下拉找到&#***；形式的 HTML 实体编码字符串。<br />![解码.png](/Bugku%20这是一张单纯的图片%20Write%20up/解码.png)
使用HTML解码工具对该编码进行解码后得到flag.<be />![flag.png](/Bugku%20这是一张单纯的图片%20Write%20up/flag.png)
提交flag，flag正确，完活。