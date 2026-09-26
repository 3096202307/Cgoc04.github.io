平台：bugku
题目：ok
分类：Crypot

打开附件，内容是大量 `Ook.` `Ook?` `Ook!` 组成的字符串，没有其他提示，根据题目所给信息可知为"Ook!"编码形式。
<img width="2282" height="1306" alt="Image" src="https://github.com/user-attachments/assets/c42509ae-d6a0-4dc1-acdf-3bc4870106ad" />

## 原理分析

Ook! 是 Brainfuck 的变体，是一种极简的趣味编程语言，没有数字字母，仅由 `Ook.`、`Ook?`、`Ook!` 两两组合代表一条 BF 指令，映射关系：
```
Ook. Ook?   → > 指针右移
Ook? Ook.   → < 指针左移
Ook. Ook!   → + 当前单元格值+1
Ook! Ook.   → - 当前单元格值-1
Ook? Ook!   → . 输出当前单元格ASCII字符
Ook! Ook?   → , 读入字符（输入）
Ook! Ook!   → [ 条件跳转，为0则跳到对应]
Ook? Ook?   → ] 条件跳转，非0则跳到对应[
```
通过在线解密工具解密得到flag
1. 复制附件里全部 Ook 文本。
2. 打开 Ook 在线解码网：ttps://www.splitbrain.org/services/ook

<img width="3072" height="1706" alt="Image" src="https://github.com/user-attachments/assets/2874b10a-c942-45f5-bad3-aabb87f4b26a" />
点击”Ook! to Text“得到flag，提交flag，完活。