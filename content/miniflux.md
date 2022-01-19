+++
title = "Miniflux 自建 RSS 閱讀器服務"
template = "page.html"
date = 2018-11-04T13:52:07+08:00
[taxonomies]
tags = ["rss"]
[extra]
summary = "自建 RSS 閱讀器服務"
+++

在 Google Reader 收攤後，我後來嘗試了不少的 RSS 閱讀器服務，[Feedly](https://feedly.com/) 、[Flipboard](https://flipboard.com/) 和 [Feedspot](https://www.feedspot.com/)。嚴格來說 [Flipboard](https://flipboard.com/) 不算是 RSS 閱讀器，比較像是社群內容雜誌，但不可否認的它是個好 APP，以前甚至為了 [Flipboard](https://flipboard.com/) 買 iPad。[Feedspot](https://www.feedspot.com/) 感覺介面很像 Google Reader，又有計劃推出 iOS APP，中間有推出終生 Gold 方案，我也購買了。Gold 只差在通知，可以自訂時間區間而已，真的蠻雞肋的，有些 Bug 回報，官方似乎沒在維護，iOS APP. 也難產，讓我一直有想出走的想法，爾後又接觸到 [Tiny Tiny RSS](https://tt-rss.org/)、[FreshRSS](https://freshrss.org/) 和 [Miniflux](https://miniflux.app/)。

最近 [Reeder](http://reederapp.com/) 因為計畫出新版，將舊版限時免費，注意到來源設定裡面有一個自建服務叫做 Fever，上網查看後發現，原來作者已經停止維護了，真的是晴天霹靂。不過有網友幫 [Tiny Tiny RSS](https://tt-rss.org/)，額外寫支援 [Fever Plugin](https://github.com/dasmurphy/tinytinyrss-fever-plugin)，不過我一直對 TTRSS 的早期介面有點卻步，好像沒在更新，加上額外加入 Plugin 方式，有可能造成不相容的問題。

然後 [FreshRSS](https://freshrss.org/) 有內建 Fever API，可是嘗試架設後，[FreshRSS](https://freshrss.org/) 對 RSS 的標準十分嚴格，無法通過 RSS 標準驗證的，就無法加入，速度上有點緩慢，可能跟架構是 PHP + Apache 有關。

最後發現了 [Miniflux](https://miniflux.app/)，GO 語言撰寫出來的，容量很小內建 Web Server，內建 Ferver API，對 RSS 沒這麼挑嘴，反應也快的沒話說。作者對簡潔似乎有點偏執，不過剛好我也喜歡這樣的偏執，十分推薦使用。