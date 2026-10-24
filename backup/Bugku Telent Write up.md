  平台：Bugku
题目：Telent
分类：MISC

下载题目所给附件，得到一个名为“telent”的后缀为zip的压缩包，解压缩后得到名为“networking”的后缀为pcap的抓包文件。

<img width="136" height="140" alt="Image" src="https://github.com/user-attachments/assets/35a9a437-c6d1-49d5-ba93-87321dab96aa" />

<img width="156" height="148" alt="Image" src="https://github.com/user-attachments/assets/659cf03b-5196-4140-b1cc-1c2f84545e30" />

解题过程

### 1. 初步分析

用 Wireshark / tshark 打开流量包，协议统计显示：
<img width="3072" height="1828" alt="Image" src="https://github.com/user-attachments/assets/1f2a049c-f5bd-4d6d-875c-10b66d4dbdc8" />

    TCP → TELNET（36 帧，2300 字节）
    其中 23 帧标记 [Malformed Packet]
    连接：192.168.221.128:1146 → 192.168.221.164:23

**★ 关键判断：TELNET 是明文协议，直接跟踪流就能看到内容。**

### 2. 跟踪 TCP 流

    tshark -r networking.pcap -q -z follow,tcp,ascii,0

或者 Wireshark 里：右键任意 TELNET 包 → **Follow → TCP Stream**
<img width="946" height="784" alt="Image" src="https://github.com/user-attachments/assets/88b80b4a-318e-4403-91f0-bc30d97f397f" />

### 3. 读取明文

流里清晰可见：
<img width="1432" height="1608" alt="Image" src="https://github.com/user-attachments/assets/a6a0b45b-15e9-4523-b17c-647532ba936a" />



    Ubuntu 12.04.2 LTS
    hockeyinjune-virtual-machine login: csaaw      ← 用户名（逐字符发送）
    Password: flag{d316759c281bf925d600be698a4973d5}   ← ★ 密码就是 flag
    Login incorrect

**★ 用户名 `csaaw` 每个字符单独一个包 —— 这是 TELNET 逐字符回显的特性。**

**★ 用户把 flag 当作密码输入，登录当然失败，但流量里已经完整记录了。

<img width="674" height="144" alt="Image" src="https://github.com/user-attachments/assets/83a08a01-3bb2-4860-a5aa-b4a9f429c726" />

## Flag

    flag{d316759c281bf925d600be698a4973d5}



