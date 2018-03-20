---
title: Android ChromeのBookmarkletでTwitter共有を実装する
---

SONYのXperia Z3 Tablet Compactを愛用しています。外出中の読書や情報収集にはもっぱらこの端末を使っています。

使っているアプリは

* Kindle
* Pocket
* Feedly
* Chrome

くらいで、集中を妨げられないようにTwitter/Facebookなどのソーシャル系アプリは入れていません。Googleアカウントも最近削除したので、カレンダーもメールも何もありません。

が、ブラウザで読んでいるWebページをTwitterに投げたい場合も多々あり、そういう時の方法としてどうしたものか、考えあぐねていました。（TwitterやFacebookのアプリは入れていないので）

で、先日、

* [いまさらまとめるブックマークレットの作り方 〜 2016年版 〜 - 無駄と文化](http://blog.mudatobunka.org/entry/2016/02/29/030633)

という記事が流れてきたのを見かけ、「これなのでは？」という気がしたので試してみました。

## Bookmarkletを実装

Twitterで共有するためのBookmarkletのコードは以下になります。
```
javascript:void((function(undefined) {
  p = "text=" + encodeURIComponent(document.title) + "&url=" + encodeURIComponent(document.location);
  window.open("https://twitter.com/intent/tweet?" + p);
})());
```

これを[packer](http://dean.edwards.name/packer/)で1行にまとめると以下のようになります。
```
javascript:void((function(undefined){p="text="+encodeURIComponent(document.title)+"&url="+encodeURIComponent(document.location);window.open("https://twitter.com/intent/tweet?"+p)})());
```

ついでに、Facebookで共有するためのコードは以下のようなもので、
```
javascript:void((function(undefined) {
  p = "u=" + encodeURIComponent(document.location);
  window.open("https://www.facebook.com/sharer/sharer.php?" + p);
})());
```

packerにかけると以下のようになります。
```
javascript:void((function(undefined){p="u="+encodeURIComponent(document.location);window.open("https://www.facebook.com/sharer/sharer.php?"+p)})());
```

## Android Chromeで起動する

上記のBookmarkletをPCのFirefoxに登録したところ、想定通り動作したのですが、そのままAndroidのChromeで実行しても動作しませんでした。どうも単にブックマークリストから開こうとしただけでは起動できないようです。

というわけで、以下の記事を参考に呼び出し方を変えてみました。

* [AndroidのChromeでブックマークレットを起動する方法！  あめつくのブログ](http://ametuku.com/archives/6858)

すると、以下のように期待通りの動作をしてくれるようになりました。

まず、Webページを開きます。

![Screenshot_20180320-121036.png](/assets/images/2018-03-20/Screenshot_20180320-121036.png)

アドレスバーにブックマーク名（今回の場合は Share on Twitter）の一部をタイプ。プルダウンに出てきたら、それをクリック。

![Screenshot_20180320-121613.png](/assets/images/2018-03-20/Screenshot_20180320-121613.png)

Bookmarkletが起動してTwitter上で共有できるタブが開く。

![Screenshot_20180320-121631.png](/assets/images/2018-03-20/Screenshot_20180320-121631.png)

これで、ソーシャルアプリの入っていない私のタブレットでも簡単にTwitter上で共有できるようになりました。

めでたしめでたし。
