平台：bugku
题目：这是一张单纯的图片
分类：MISC（杂项）

题目给出一张 jpg 图片，提示 flag 格式为`key{}`，从图片肉眼观察看不到任何信息，需要从文件本身寻找隐藏内容。

下载图片，保存为`1.jpg`。
<img width="678" height="756" alt="Image" src="https://github.com/user-attachments/assets/1c47f342-cda4-4252-ae9e-1d02f31482d0" />


用Windows自带的记事本打开该图片，发现是一堆乱码。
<img width="2268" height="1214" alt="Image" src="https://github.com/user-attachments/assets/8a1cb205-2c24-419c-b5f1-4429c5f0b4bc" />

下拉找到`&#***;`形式的 HTML 实体编码字符串。
<img width="2262" height="468" alt="Image" src="https://github.com/user-attachments/assets/e3935f3a-d284-4e76-9aa8-3270718f3f75" />

使用HTML解码工具对该编码进行解码后得到flag。
<img width="3072" height="1818" alt="Image" src="https://github.com/user-attachments/assets/72119821-7e88-496b-93ca-e06b6004edec" />

提交flag，flag正确，完活。