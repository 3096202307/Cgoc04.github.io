平台：Bugku
题目：[+-<>]
分类：Crypot
题目给出的密文由 +、-、>、<、[、] 组成，是典型的 Brainfuck（BF）极简编程语言特征。
Brainfuck 仅有 8 条指令，CTF 中仅需掌握核心 6 条即可解题：
- +：当前内存单元格数值 +1
- -：当前内存单元格数值 -1
- >：数据指针右移
- <：数据指针左移
- .：输出当前单元格 ASCII 字符
- []：循环结构，对应条件跳转
利用python编写程序进行解码
def brainfuck_decode(code):
    tape = [0] * 30000
    ptr = pc = 0
    bracket_map = {}
    stack = []

    ## 预处理括号跳转映射
    for idx, char in enumerate(code):
        if char == "[":
            stack.append(idx)
        elif char == "]":
            left = stack.pop()
            bracket_map[idx] = left
            bracket_map[left] = idx

    output = ""
    while pc < len(code):
        cmd = code[pc]
        if cmd == ">":
            ptr += 1
        elif cmd == "<":
            ptr -= 1
        elif cmd == "+":
            tape[ptr] = (tape[ptr] + 1) % 256
        elif cmd == "-":
            tape[ptr] = (tape[ptr] - 1) % 256
        elif cmd == ".":
            output += chr(tape[ptr])
        elif cmd == "[" and tape[ptr] == 0:
            pc = bracket_map[pc]
        elif cmd == "]" and tape[ptr] != 0:
            pc = bracket_map[pc]
        pc += 1
    return output

## 题目BF代码
bf_code = """+++++ +++++ [->++ +++++ +++<] >++.+ +++++ .<+++ [->-- -<]>- -.+++ +++.< ++++[ ->+++ +<]>+ +++.< +++++ +++[- >---- ----< ]>--- ----- ---.< +++++ ++[-> +++++ ++<]> +++.< +++++ +[->- ----- <]>-- ----- -.--. ----. --.++ +++++ +.<++ ++++[ ->+++ +++<] >++++ +.++. <++++ ++[-> ----- -<]>- ----- ----. -.<++ +++++ [->++ +++++ <]>+. ----. ++++. <++++ +++[- >---- ---<] >---- .+.<+ +++++ ++[-> +++++ +++<] >++++ +++++ ++.<"""
## 去除全部空格
bf_code = bf_code.replace(" ", "")
print(brainfuck_decode(bf_code))
<img width="3072" height="1920" alt="Image" src="https://github.com/user-attachments/assets/7e7b61a8-d2f9-46aa-99da-562fe81cd224" />

执行脚本后，程序自动解析 Brainfuck 循环逻辑，输出明文 Flag：
flag{brainfuck_1s_funny}
<img width="1310" height="1244" alt="Image" src="https://github.com/user-attachments/assets/08db9a96-1830-4d22-892d-f9fc926e429c" />

得到flag，提交，flag正确，完活。



