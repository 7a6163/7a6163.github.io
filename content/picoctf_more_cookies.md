+++
title = "pioCTF - More Cookies 150 points"
template = "page.html"
date = 2021-07-03T03:11:27+08:00
[taxonomies]
tags = ["ctf"]
[extra]
summary = "150 points"
+++

Cookies 的進階題，還有一個同名版本是 2021 年的 More Cookies 90 points 但那題感覺難上很多。

這次作者有提供 server 的 source code ，簡單來說就是直接 Open Book，他使用了一套叫做 Flask 的 Web framework。

服務啟動會隨機挑選餅乾名當作 Secret key，當使用 Session 時，去產生出加密後的 Cookies。

所以我們先照慣例，直接搜尋 snickerdoodle，從開發者模式取得 Cookie，原本想自己照他的模式，寫類似的 python 來跑，不過從 Google 發現這個有人已經寫出加解密套件。

[GitHub - noraj/flask-session-cookie-manager: Flask Session Cookie Decoder/Encoder](https://github.com/noraj/flask-session-cookie-manager)

```bash
cookies=(a b c)

for i in "${cookies[@]}"; do echo "$i"; python ./flask_session_cookie_manager3.py decode -s "$i" -c [cookies]; done
```

順利的話會找到對應的 Secret key，也可以稍微看一下解密出來的明文的樣子，再把內文改成 admin，再用 Key 拿去加密，組成 Cookies 回寫瀏覽器就解了。

