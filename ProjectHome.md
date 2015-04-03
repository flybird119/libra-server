# A keyword match server #

为什么需要关键字匹配服务器？你可能想用正则去匹配，不过细想一下，如果有10万个关键字，那不是要用正则匹配10万次。
<br />
而是用关键字匹配服务器只需要匹配一次即可，速度非常快，速度只跟你要匹配的原文长度有关。
<br />
#安装方法#
<br />
1.安装libevent(http://monkey.org/~provos/libevent/)
<br />
2.安装libdatrie(http://linux.thai.net/~thep/datrie/datrie.html)
<br />
3.make
<br />
<br />
PHP接口：
<br />
**存储**
```
<?php
include('matcher.php');
 
$matcher = new Matcher('192.168.10.20');
$matcher->set('hello');
$matcher->set('world');
$matcher->set('kitty');
?>
```

<br />
**匹配**
```
<?php
include('matcher.php');

$matcher = new Matcher('192.168.10.20');
$matchs = $matcher->gets('hello world, hello kitty')
if (!empty($matchs)) {
   print_r($matchs);
}
?>
```

输出：
```
Array
(
    [hello] => hello
    [world] => world
    [kitty] => kitty
)
```