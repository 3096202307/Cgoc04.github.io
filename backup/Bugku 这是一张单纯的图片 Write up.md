
平台：bugku
题目：这是一张单纯的图片
分类：MISC（杂项）

题目给出一张 jpg 图片，提示 flag 格式为`key{}`，从图片肉眼观察看不到任何信息，需要从文件本身寻找隐藏内容。

下载图片，保存为`1.jpg`。
<img width="678" height="756" alt="Image" src="https://github.com/user-attachments/assets/f0a2e16f-f2db-4908-af55-95a2d245035e" />

用Windows自带的记事本打开该图片，发现是一堆乱码。
<img width="2262" height="468" alt="Image" src="https://github.com/user-attachments/assets/6585b118-a7fe-4df9-86c7-52b3f73b2bf7" />


下拉找到`&#***;`形式的 HTML 实体编码字符串。
<img width="2268" height="1214" alt="Image" src="https://github.com/user-attachments/assets/e23f8fb6-eb42-4f63-866f-93d8a6c25b89" />

使用HTML解码工具对该编码进行解码后得到flag。
<img width="3072" height="1818" alt="Image" src="https://github.com/user-attachments/assets/3f7a90c6-6aaa-4642-ac67-210be884ea1a" />

提交flag，flag正确，完活。