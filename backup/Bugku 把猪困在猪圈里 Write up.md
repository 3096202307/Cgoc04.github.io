平台：Bugku
题目：把猪困在猪圈里
分类：Crypot

下载题目所给附件，得到一个名为“file”的txt文本文档。
<img width="96" height="138" alt="Image" src="https://github.com/user-attachments/assets/51ea8933-1802-4d82-b0a9-60d6ca6c9c43" />

打开文档，发现文档内有14736个字符。
<img width="2326" height="1310" alt="Image" src="https://github.com/user-attachments/assets/ad8e6792-ef66-4079-bd77-05bb6a103e9d" />

看**开头四个字符**：
 ```  
     /9j/
     └┬┘
      └── 这是 JPEG 文件头 FF D8 FF 的 Base64 形式
```

**所以：这是一张图片被 Base64 编码了。** 题目在提示"猪圈" —— 那图里八成是猪圈密码的符号。
做法：在网上搜"base64 转图片"，把密文粘进去。得到猪圈密码的符号。
<img width="2426" height="1222" alt="Image" src="https://github.com/user-attachments/assets/bfbd50df-fe03-4f74-b3e9-94d7f2355296" />

<img width="840" height="180" alt="Image" src="https://github.com/user-attachments/assets/b4970215-8865-4f15-a9f0-ddf483d1c753" />

按照猪圈密码表进行解码，得到flag。
<img width="1846" height="366" alt="Image" src="https://github.com/user-attachments/assets/fef81bb7-00ae-4f6a-b264-a32b04cc649e" />

解得flag{thisispigpassword}，提交flag，flag正确，完活。