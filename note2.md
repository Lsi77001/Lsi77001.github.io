Php
1.以<?php为开始，每一行以分号；结束，以?>结束（官方默认风格）
因为经常与html混写所以风格是为了易于区分。（其他风格在PHP7中已被淘汰）

echo是直接输出单引号‘’中的字符串原样，而双引号“”中若有变量，则输出变量结果

2.变量 php需要申明变量类型
变量以 $ 符号开始，后面跟着变量的名称
变量名必须以字母或者下划线字符开始
变量名只能包含字母数字字符以及下划线（A-z、0-9 和 _ ）
变量名不能包含空格
变量名是区分大小写的（$y 和 $Y 是两个不同的变量）
（此处cp梁总）

3.全局变量及在函数中的应用

```php
<?php
    $a="serious";
function fun(){
    global $a;
        echo $a;
}
fun();
 ?>
```

4.（1）static作用域
函数中的变量在运行之后会被销毁
但若在变量之前加入静态关键字static 则不会被销毁，如图，若无static，则变量输出一次后就销毁，输出结果为256和256!

```php
<?php
    function fun(){
    static$A="256";
    echo$A++,"<br>";
    
    
}
    fun();
fun();
    ?>
```

（2）参量作用域

```php
<?php
    $a="666";
function fun($a){
    echo$A,"<br>";
}
fun($a)
  ?>
```

5.常量（如图所示）

```php
<?php
    define("A","i want to sleep");
echo A;
    ?>
```

6.基本输出类型
（1）<?php echo "hello world!";//只能打印字符串
（2）print_r("hello world!");//能够打印数组和字符串 
（3）var_dump("hello world!");//能够打印数组和字符串同时输出打印内容的数据类型（还有数据个数）
（4）var_export("hello world!",true);//能够将字符串转换为php代码，第二个参数设置为true能够返回值（也能打印数组）
（5）die("hello world!");//结束程序并打印内容 ?>
此处改编自梁总

7.分支语言
（1）if语句（待写
<?php if(exp){//判断条件 //条件成立时候执行的代码块 } ?>
下面是简单举例

```php
<?php
    $x=6;
$y=7;
if($x>$y):
$x=$y
    echo"$x";
else:
$y=$x
    echo"y";
endif;

    ?>
```

（2）switch语句（有点类似于函数结构

```php
<?php
    $x=6;
    switch($x){
            case $x>7;
            echo"666";
        case $<7;
            echo"777";
            break;
    }
    ?>
```



判断词与结束词与IF有所不同

8.php中的数组/遍历数组

普通数组

```php
<?php
    $a=array('你的名字'=>'1101','1'=>'2202');
echo $a ['你的名字'];
    ?>
```



你的名字，1为键名，1101和2202为键值





var_dump的数组输出

Echo的输出主要用于关联数组
在一个数组中能通过有效输入得到特定的字符串输出（C语言中只能为整数）

补充：普通遍历数组

```php
<?php
    $a=['abc','666'];
for($i=0;$i<count($a);$i++){
    echo $a[$i],"<br>";
}
    ?>
```

count()是读取数组$a的长度

重要的是学会循环语句（下同）
（2）关联数组的遍历数组

```php
<?php
    $age=array("joe"=>"23","dio"=>"66","kono"=>"55");
foreach($age as $key =>$value){
    echo $value,"<br>";
}
    ?>
```

9.Cookie
存在于本地有一定生命周期的临时文件
语句为setcookie（“username”,”用户名”,time()+时间）  time（）是抓取当前时间  +时间是文件的生命周期

10.session 基于cookie，但不同的是数据储存在服务器，本地再利用cookie储存一个session
基本语句
session_start 启动session
$_SESSION[‘名称’]=’值’

11.两种基本的HTTP协议
（1）GET协议

```php
<?php
    echo $_GET['a'];
    ?>
```

然后在链接中的/后面加?a=(),就会打印出括号中的内容

get协议的基本语法（传输协议如图所示，链接中的?前有index.php（即源文件名），但浏览器默认省略）

（2）POST协议（常用于登录的协议）

```php+HTML
<?php
    echo $_POST['a'];
    ?>
<form action="http://127.0.0.1/index.php" method="post">
    <input type="text" name="a">
    <input type="submit" name="submit" value="登录">
</form>
```

Action中不输入网址即默认为当前网页

method后面的传输协议

Input为输入	
Type text为文本框
submit为确认按钮
value改变了确认按钮的名称


11.Mysql数据库连接与查询

SELECT 字段，字段... from 表 where 条件 
insert into 表名 (字段，字段...)values(值) 
update 表名 set 字段=新值，字段=新值 where 条件 
(cp教案)

12.include文件包含
包含语句 include/require（两者的区别是require遇到错误会直接停止而include不会
格式：include（“文件名”）

目前所知的第一种应用是通过该语句挟持服务器权限
通过上传真实内容是PHP代码的图片使源码有include漏洞的网页运行该有恶意代码的图片文件

