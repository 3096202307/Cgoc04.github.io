打开题目所给靶机地址，出现代码：
$what=$_POST['what'];
echo $what;
if($what=='flag')
echo 'flag{****}';
通过代码中的“POST”判断其为POST题型，需要构造POST请求。
方法：利用Kali虚拟机终端构造POST请求（使用root模式），curl -X POST 靶机地址 -d"what=flag"，其中 -X POST 指定请求方式为POST，-d "what=flag"：请求体内携带POST数据，参数名what，值flag。请求构建完成后运行，得到flag，完活。