---
layout: post
title:  "TypeScriptに憧れる"
date:   2021-03-07
author: Emorard
---
プログラミング言語の分類として動的型付けと静的型付けがある。

僕は圧倒的に静的型付けの方が得意で、JavaやCのきつい型付けで慣れたからか、どの型なのか一目でわからない動的型付けは疲れる。

妥協点としてはClojureで、型ヒントというものが存在する。これはリフレクションを避けることで高速化を行う機能だが、見やすさという点でも良し。
自明な引数はコンパイラに任せることもでき、僕がClojureが「好き」な理由の一つでもある。

{% highlight clojure %}
(defn len [x] (.length x))

(defn len-hint [^String x] (.length x))

(time (reduce + (map len (repeat 1000 "qwerty"))))

(time (reduce + (map len-hint (repeat 1000 "qwerty"))))
{% endhighlight  %}
```
"Elapsed time: 37.918639 msecs"
"Elapsed time: 3.850565 msecs"
```

なんと10倍以上もの差がある

## 人気の訳

最近、Chromeの拡張機能を作るためにJavaScriptを使っている。非同期なAPIに振り回されながら、よくわからないany型に悩まされている。

しかし、TypeScriptがあるではないですか。数年前から人気が上昇していることは知っていたが、当時はScalaしか使っていなかったため、気にすることはなかった。

なるほど、確かに型が欲しくなる。信じて書いたコードがundefinedとかログに残るのはかなり痛い。

今作っている拡張機能はJavaScriptで書くが、次からはTypeScriptにしよう。
