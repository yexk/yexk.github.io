---
layout: blog
title: PHP常用的函数
date: 2017-08-16 11:52:23
categories: PHP
tags: 
- php 
- common
- function
---

### 1. 去掉UTF8 BOM 头
>通过手动去除文件里面的bom实现。

```
    /**
     * 去掉UTF8 Bom头
     * Remove UTF8 Bom 
     * 
     * @param  string    $string 
     * @return string
     */
    function remove_utf8_Bom($string)
    {
        if(substr($string, 0, 3) == pack('CCC', 239, 187, 191)) return substr($string, 3);
        return $string;
    }
```

### 2. 增强substr字符截取函数（支持UTF8）
>当你的php没有开启mb_string函数扩展的时候就需要自己手动去书写

~~~
 /**
     * 增强substr方法：支持多字节语言，比如中文。
     * Enhanced substr version: support multibyte languages like Chinese.
     *
     * @param string $string
     * @param int $length 
     * @param string $append 
     * @return string 
     **/
    function substr($string, $length, $append = '')
    {
        if (strlen($string) <= $length ) $append = '';
        if(function_exists('mb_substr')) return mb_substr($string, 0, $length, 'utf-8') . $append;

        preg_match_all("/./su", $string, $data);
        return join("", array_slice($data[0],  0, $length)) . $append;
    }
~~~

### 3. 判断是不是ajax请求

~~~
    /**
     * 检查是否是AJAX请求
     * Check is ajax request.
     * 
     * @return bool
     */
    function is_ajax()
    {
        $isAjax = isset($_SERVER['HTTP_X_REQUESTED_WITH']) && $_SERVER['HTTP_X_REQUESTED_WITH'] == 'XMLHttpRequest';
        if(!$isAjax) $isAjax = (isset($_GET['HTTP_X_REQUESTED_WITH']) && $_GET['HTTP_X_REQUESTED_WITH'] == 'true');
        return $isAjax;
    }

~~~

### 4. 获取浏览器类型。

```
    /**
     * 获取浏览器类型。
     * Get browser.
     *
     * @return string
     */
    function get_browser()
    {
        if(empty($_SERVER['HTTP_USER_AGENT'])) return 'unknow';

        $agent = $_SERVER["HTTP_USER_AGENT"];
        if(strpos($agent, 'MSIE') !== false || strpos($agent, 'rv:11.0')) 
        {
            return "ie";
        }
        else if(strpos($agent, 'Firefox') !== false)
        {
            return "firefox";
        }
        else if(strpos($agent, 'Chrome') !== false)
        {
            return "chrome";
        }
        else if(strpos($agent, 'Opera') !== false)
        {
            return 'opera';
        }
        else if((strpos($agent, 'Chrome') == false) && strpos($agent, 'Safari') !== false)
        {
            return 'safari';
        }
        else
        {
            return 'unknown';
        }
    }

```

### 5. 获取浏览器版本

```
    /**
     * 获取浏览器版本
     * Get browser version. 
     * 
     * @return string
     */
    function get_browser_version()
    {
        if(empty($_SERVER['HTTP_USER_AGENT'])) return 'unknow';

        $agent = $_SERVER['HTTP_USER_AGENT'];   
        if(preg_match('/MSIE\s(\d+)\..*/i', $agent, $regs))
        {
            return $regs[1];
        }
        else if(preg_match('/FireFox\/(\d+)\..*/i', $agent, $regs))
        {
            return $regs[1];
        }
        else if(preg_match('/Opera[\s|\/](\d+)\..*/i', $agent, $regs))
        {
            return $regs[1];
        }
        else if(preg_match('/Chrome\/(\d+)\..*/i', $agent, $regs))
        {
            return $regs[1];
        }
        else if((strpos($agent,'Chrome') == false) && preg_match('/Safari\/(\d+)\..*$/i', $agent, $regs))
        {
            return $regs[1];
        }
        else if(preg_match('/rv:(\d+)\..*/i', $agent, $regs))
        {
            return $regs[1];
        }
        else
        {
            return 'unknow';
        }
    }
```

### 6. 获取客服端的操作系统

```
    /**
     * 获取客户端操作系统
     * Get client os from agent info. 
     * 
     * @return string
     */
    function get_os()
    {
        if(empty($_SERVER['HTTP_USER_AGENT'])) return 'unknow';

        $osList = array(
            '/windows nt 10/i'      =>  'Windows 10',
            '/windows nt 6.3/i'     =>  'Windows 8.1',
            '/windows nt 6.2/i'     =>  'Windows 8',
            '/windows nt 6.1/i'     =>  'Windows 7',
            '/windows nt 6.0/i'     =>  'Windows Vista',
            '/windows nt 5.2/i'     =>  'Windows Server 2003/XP x64',
            '/windows nt 5.1/i'     =>  'Windows XP',
            '/windows xp/i'         =>  'Windows XP',
            '/windows nt 5.0/i'     =>  'Windows 2000',
            '/windows me/i'         =>  'Windows ME',
            '/win98/i'              =>  'Windows 98',
            '/win95/i'              =>  'Windows 95',
            '/win16/i'              =>  'Windows 3.11',
            '/macintosh|mac os x/i' =>  'Mac OS X',
            '/mac_powerpc/i'        =>  'Mac OS 9',
            '/linux/i'              =>  'Linux',
            '/ubuntu/i'             =>  'Ubuntu',
            '/iphone/i'             =>  'iPhone',
            '/ipod/i'               =>  'iPod',
            '/ipad/i'               =>  'iPad',
            '/android/i'            =>  'Android',
            '/blackberry/i'         =>  'BlackBerry',
            '/webos/i'              =>  'Mobile'
        );

        foreach ($osList as $regex => $value)
        { 
            if(preg_match($regex, $_SERVER['HTTP_USER_AGENT'])) return $value; 
        }   

        return 'unknown';
    }
```

### 7. 检查IP是否合法

```
    /**
     * 检查IP是否合法。
     * Check ip avaliable.  
     * 
     * @param  string $ip 
     * @return bool
     */
    function check_ip($ip)
    {
        $ip = trim($ip);
        if(strpos($ip, '/') !== false)
        {
            $s = explode('/', $ip);
            preg_match('/^(((25[0-5])|(2[0-4]\d)|(1\d\d)|([1-9]\d)|\d)(\.((25[0-5])|(2[0-4]\d)|(1\d\d)|([1-9]\d)|\d)){3})$/', $s[0], $matches);
            if(!empty($matches) and $s[1] > 0 and $s[1] < 36) return true;
        }
        else
        {
            preg_match('/^(((25[0-5])|(2[0-4]\d)|(1\d\d)|([1-9]\d)|\d)(\.((25[0-5])|(2[0-4]\d)|(1\d\d)|([1-9]\d)|\d)){3})$/', $ip, $matches);
            if(!empty($matches)) return true;
        }
        return false;
    }
```

### 8. 创建随机的字符串

```
    /**
     * 创建随机的字符串。
     * Create random string. 
     * 
     * @param  int    $length 
     * @param  string $skip A-Z|a-z|0-9
     * @return void
     */
    function create_randomStr($length, $skip = '')
    {
        $str  = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
        $skip = str_replace('A-Z', 'ABCDEFGHIJKLMNOPQRSTUVWXYZ', $skip);
        $skip = str_replace('a-z', 'abcdefghijklmnopqrstuvwxyz', $skip);
        $skip = str_replace('0-9', '0123456789', $skip);
        for($i = 0; $i < strlen($skip); $i++)
        {
            $str = str_replace($skip[$i], '', $str);
        }

        $strlen = strlen($str);
        while($length > strlen($str)) $str .= $str;

        $str = str_shuffle($str); 
        return substr($str,0,$length); 
    }
```

### 9. mask地址类型转换
mask地址的类型转换，比如255.255.255.0 => 32 
```
    /**
     * 整形转字符型
     * @Author Yexk
     * @Date   2017-02-10
     * @param  {Int}      $bit [数字类型：1-32]
     * @return {String}        [mask字符串地址]
     */
    public static function maskbit2ip($bit)
    {
        $bit    = intval($bit);
        $lan    = ((1<<$bit) -1)<<(32-$bit) ;
        $lan    = str_split(''.decbin($lan), 8);
        $maskip = bindec($lan[0]).'.'.bindec($lan[1]).'.'.bindec($lan[2]).'.'.bindec($lan[3]);

        return $maskip;
    }
    
    /**
     * mask转整形
     * @Author Yexk
     * @Date   2017-02-10
     * @param  {String}   $ip [字符型:255.255.255.0]
     * @return {Int}          [返回整形]
     */
    public static function maskip2bit($ip)
    {
        $ips = explode('.',$ip);
        if(!is_array($ips) || 4 != count($ips)){
            return false;
        }

        $bit = (intval($ips[0])<<24) + (intval($ips[1])<<16) + (intval($ips[2])<<8) + intval($ips[3]);
        $bit = decbin($bit);
        $len = strlen($bit);
        if(32 != $len){
            return false;
        }
        $masklen = 0;
        $flag    = '1';
        for($i=0; $i<32; $i++){
            if('1'==$bit[$i]){
                $masklen++;
                if('1'!=$flag){
                    return false;
                }
            }
            $flag=$bit[$i];
        }

        return $masklen;
    }

```