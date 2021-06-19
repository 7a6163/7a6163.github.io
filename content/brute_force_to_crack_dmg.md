+++
title = "暴力破解加密的 dmg"
template = "page.html"
date = 2021-06-19T20:09:27+08:00
[taxonomies]
tags = ["hacking"]
[extra]
summary = "簡單教學如何暴力破解加密 dmg"
+++

首先先安裝 john-jumbo

```bash
$ brew install john-jumbo
```

先產生 hashes，注意程式版本是否不同
```bash
$ /usr/local/Cellar/john-jumbo/1.9.0/share/john/dmg2john target.dmg > target.dmg.hash
```

開始暴力破解
```bash
$ john target.dmg.hash
```

如果明確知道密碼組成，可以使用 `--mask`
```bash
$ john --mask="[0-9a-z][0-9a-z][0-9a-z]" target.dmg.hash
```

如果要多開 processes，可以使用 `--fork`，最高不要超過 CPU Core 數
```bash
$ john --fork=8 target.dmg.hash
```
