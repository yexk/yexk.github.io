---
layout: blog
title: composer快速入门
date: 2017-08-19 13:52:19
categories: composer
tags:
- composer
- phpmailer
---

安装好后就可以开始使用`composer`命令了。

这里我们那phpmailer举例子。例如你的项目需要用到phpmailer来发邮件。只需要两步：`下载`->`加载使用`。

<!-- more -->

## composer快速入门

#### 第一步 
命令：`composer require phpmailer/phpmailer`  
使用上面这个命令进行安装`phpmailer`。  
执行完成后会看到生成`vendor/phpmailer` ，这样phpmailer就已经下载到你项目里面了。

#### 第二步
引用类库。在你需要的使用的项目的文件里面加上着行代码。（这是统一格式无需修改）。
`require 'vendor/autoload.php';`

接下来就可以使用了。详细内容可以参考phpmailer手册。
--- 
这里附上一个案例：   
在根目录创建一个`test.php`文件。
```PHP
<?php 
require 'vendor/autoload.php'; 
/**
 * 发送邮件 **实际项目改成你的配置文件**
 * @date 2016年11月14日
 * @author Yexk <yexk@yexk.cn>
 *
 * @param String $address 收件人邮箱地址
 * @param string $message 内容
 * @param string $title   主题
 * @return boolean        成功返回true,否则false
 *
 */
function send_mail($address,$message='',$title='')
{
    date_default_timezone_set("Asia/Shanghai");//设定时区东八区
    $mail = new \PHPMailer();
    
    //设置smtp参数
    // $mail->SMTPDebug = 3;
    $mail->IsSMTP();
    $mail->SMTPAuth  = true;
    $mail->SMTPKeepAlive = true;
    $mail->SMTPSecure = 'ssl';
    $mail->CharSet = 'UTF-8'; // 设置字符集编码
    $mail->Host    = 'smtp.exmail.qq.com';    // 主机
    $mail->Port    = '465';    // 端口
    
    //填写你的mail账号和密码 
    $mail->Username='test@yexk.cn'; // 
    $mail->Password='xxxxxxxxxxx'; // 
    
    //设置发送方，最好不要伪造地址
    $mail->From    = 'test@yexk.cn';
    $mail->FromName  = 'test';// 发件人的名字

    if (strlen($title)>0){
        $mail->Subject=$title;
    }else{
        $mail->Subject='scInternal内网系统';
    }// 邮件主题
    
    // $mail->WordWrap  = 50; // 设置自动换行
    $mail->MsgHTML($message); // 发件内容
    //设置邮件接收方的邮箱和姓名
    $mail->AddAddress($address,$address);
    //使用HTML格式发送邮件
    $mail->IsHTML(true);
    //通过Send方法发送邮件
    //根据发送结果做相应处理
    if(!$mail->Send())
    {
        $msg = '[' . date('Y-m-d H:i:s') . ' ==> ' . $mail->ErrorInfo ."]" . PHP_EOL;
        file_put_contents('send_mail.log', $msg ,FILE_APPEND);
        return false;
    } 
    else
    {
        return true;
    }
}
var_dump(send_mail('yexk@yexk.cn','测试composer'));
```