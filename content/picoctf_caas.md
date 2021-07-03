+++
title = "pioCTF - caas"
template = "page.html"
date = 2021-07-03T23:11:27+08:00
[taxonomies]
tags = ["ctf"]
[extra]
summary = "Cowsay as a Service"
+++

![](https://7a6163.github.io/assets//images/20210703230955.png)

`https://picoctf/cowsay/{message}`

蠻簡單的一題，一隻牛會說出您輸入的訊息。這題有提供 index.js，不過我沒注意到就直接解了。

首先思維要猜 Flag 在哪，從牛會講話的模式來看， Flag 應該是一個檔案，要藉由牛的嘴巴說出來。

`` `ls` ``

會看到一這個目錄的資料夾，然後會看到 flag 的檔案，還故意拼錯檔名。

`` `cat falg.txt` ``

Flag 就到手了，有興趣可以看一下他們的題目應該都是用 Docker 包裝，是不是可以 container escape attack 好像可以研究看看！
