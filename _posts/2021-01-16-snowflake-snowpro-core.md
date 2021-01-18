---
title: SnowflakeのSnowPro Core認定に合格した
---

先日、SnowflakeのSnowPro Core認定に[合格しました](https://www.youracclaim.com/badges/f955bd0f-8180-48f0-bc57-5e96cb0556ac)。


![snow.png](/assets/images/2021-01-16/snow_s.png)

* [Snowflake Certifications \| Stand Out in the Data Community](https://www.snowflake.com/certifications/)

どのように勉強していたのかを備忘録的に残しておきます。

スキル、経験値としては、

* 本業はデータベース屋さん。（多分）
* Google Cloudの[Google Cloud Certified Data Engineerには合格するレベル](/2020/12/02/google-cloud-certified-professional-data-engineer.html)。
* AWSの[Data Analytics Specialtyには合格するレベル](/2020/12/25/aws-data-analytics-specialty.html)。
* Snowflake経験は無し。

です。

## SnowPro CoreのStudy Guideを見る

まずはともあれ、どのような試験なのか、何をどう勉強するべきなのかを把握するために、SnowProのStudy Guideを見ます。
Snowflake Universityというラーニングサイト（サービス）があるので、そちらのアカウントを作成しておく必要があります（無料）。

* [SnowPro Certification Study Guide](https://snowflakeuniversity.mindtickle.com/#/update/1240380887853059998?series=1172211196159106059)

こちらをざっくり見ると、Coreのスコープは

* Database Basic Concepts
   * Basic Terminologies Related to Database and SQL
   * Tables & Data Types
   * Selecting & Manipulating Data
   * Views, Store Procedures, Function Concepts
   * Security (Authentication & Authorization)
* Basics of Cloud Fundamentals
   * Types of Cloud Computing & Benefits
   * Types of Cloud Services
   * Cloud Computing Architecture (Storage & Compute)

とありましたので、この辺の領域について、試験では100問を120分で回答する必要があります。

ちなみに、試験には「SnowPro Core認定試験_日本」という日本人向けの試験がありますが、こちらの試験は問題文も選択肢もすべて英語なのですが、日本人向けに「試験時間は150分、合格のための正答率も若干調整」されているそうです。（自分の試験でも、試験時間が150分なのは確認できましたが、正答率の違いについては確認できませんでした）

なお、日本語の試験は準備中のようです。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">英語圏でない日本人向けという意味で、試験時間や正答率を多少考慮しています。ちなみに、日本語での試験は準備中です。</p>&mdash; Mineaki Motohashi (@mmotohas) <a href="https://twitter.com/mmotohas/status/1350099071332073474?ref_src=twsrc%5Etfw">January 15, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 


## トライアルアカウントを作成しておく

Snowflakeでは30日有効のトライアルアカウントを無料で作成できます。400USD相当まで使えるようです。

* [Snowflake Trial](https://signup.snowflake.com/)

クレジットと残日数を消費していくので、自分は最初はトライアルアカウントを作成せずに学習を進めていたのですが（ケチ）、実際に動かしてみると思ったほどクレジットも消費しなかったので、もう少し早めに手を動かしてみれば良かったかな、と思いました。


## Cloud Data Summit 2020の動画を見る（～1週間）

Snowflakeの学習を始めようと思った時期、ちょうどCloud Data Summit 2020が開催されており、こちらの動画も活用させていただきました。

* [Snowflake \| Data Cloud Summit 2020](https://snowflake.events.cube365.net/snowflake/summit-2020)

Snowflakeの概要や設計思想、現在地をざっくり把握するのにかなり役に立ったように思います。


## Snowflake Universityの「ハンズオンエッセンシャル – 日本語」を受ける（数日）

さて、では本格的に勉強を始めます。

Snowflake Universityに日本語のコースがあるのですが、この中にハンズオンのコースがありますので、まずは最初の雰囲気を把握するためにこちらを受講します。

* [Snowflake University 日本語コース](https://snowflakeuniversity.mindtickle.com/#/courses/series/1164597286754116066?series=1164597286754116066)

字幕付きの動画を見て、ドキュメントを読んで、クイズに応えていく形式です。サクサク進めれば数日で完了できると思います。

## Study Guideに沿って勉強する（～1週間）

Study Guideには各種学習リソースへのリンクがありますので、その内容を確認しながらインプットしていきます。

基本的には、

* ドキュメント（マニュアル、公式ブログなど）を読む
* YouTubeの動画を見る
* Snowflake Universityのコースをこなす

という形になります。

Study Guideには以下の領域のコンテンツが整備されています。

* Overview & Architecture
* Virtual Warehouses
* Storage and Protection
* Data Movement
* Semi-structured Data
* Performance & Tuning
* Account & Security

この段階でSnowflake Universityにある模擬試験「SnowPro Core Sample Exam Questions」を受けたら、25/30で83.3%でした。（合格ラインは80%）

## 実際にデータパイプラインを作成してみる（～1週間）

せっかくトライアルアカウントがありますので、こちらを使ってデータパイプラインを作ってみました。

* AWSのS3をExternal Stageとして定義
* Staging TableをJSONのRawデータ保持用にVARIANT型を持ったテーブルとして定義
* External Stage→Staging Tableに取り込むSnowpipeを定義
* Production TableをStaging Tableに対するマテビューとして定義

をすることで、

* S3に着弾したJSONファイルを、Snowpipeを使ってVARIANT型としてStaging Tableに取り込み、Productionのマテビューで表形式に整形して見る

ということが自動的にできるようになります。（この話は後日別途書く予定です）

このプロセスを通して、何ができるのか、そのために何が必要なのか、をある程度把握できるようになりました。


## Udemyの「Snowflake Certification Preparation」を受ける（～1週間）

いつも何かのセールをしていることでおなじみのUdemyに、SnowPro Coreの模擬試験集があったので、こちらを購入して活用しました。

* [Snowflake Certification Preparation \| Udemy](https://www.udemy.com/course/snowflake-certification-preparation/)

ちなみに、試験の問題セットは全部で6セットあり、それぞれ

* SnowPro Core Certification - Practice Test 1 （100問）
* SnowPro Core Certification - Practice Test 2 （100問）
* SnowPro Core Certification - Practice Test 3 （100問）
* SnowPro Core Certification - Practice Test 4 （70問）
* SnowPro Core Certification - Practice Test 5 （60問）
* SnowPro Core Certification - Practice Test 6 （60問）

とあるのですが、自分は時間の都合上「Test 3」までを1回ずつしかこなせませんでした。

但し、「Test 1」、「Test 2」、「Test 3」ではそれぞれ出題される領域が異なっていましたので、まんべんなく学習するにはすべて受けて、間違った部分を確認しておいた方がいいと思います。

なお、これらの模擬試験は本番試験の直前に受けたのですが、

* Practice Test 1 → 73%
* Practice Test 2 → 65%
* Practice Test 3 → 72%

と、合格ラインとはほど遠い状態でありました。（それぞれのテストで出題される領域が偏っているので、苦手な領域に当たると点数が大きく下がるのです）

そういう観点でも、試験の前にはこれらの模擬試験を受けて自分の苦手領域を把握してマニュアルを確認しておく、などするのが良いと思います。

模擬試験では正答はもちろん、解説やマニュアルへのリンクなども提供されており、自分の学習には非常に役に立ちました。


## 本番の試験を受ける

本番試験は、Kryterionの「Online Proctored（遠隔監視オンライン試験）」を選びました。

テストの詳細については、以下も参考になるかと思います。

* [Snowflakeの認定資格「SnowPro Core」に合格するまでの道のり \| Developers.IO](https://dev.classmethod.jp/articles/how-to-pass-snowpro-core-certification/)

注意点としては、

* COVID-19の影響（？）もあり、現時点ではPCの内蔵カメラでも受験できます。
* WebassessorへのアクセスにはChromeを使い、Sentinel（試験用アプリ）はChromeから起動しましょう。Firefoxから起動しようとすると固まるかもしれません。（自分の環境では固まりました）
* 試験中に困ったら、スマホなどからWebassessorにログインしてChatで相談しましょう。大体どうにかなります。

ちょっとトラブルもあったのですが、まぁどうにかなりました。Chatでサポートしてくれた方に感謝。


## 全体を通しての感想

という感じで、今回はどうにか合格ラインには到達したのですが、出題された問題と自分の理解レベルを比較すると、

* Storage Integration
* Table Stream
* トランザクション
* Task
* Share
* ロール管理

当たりの領域が弱いかな、と感じました。

自分が学習してきた方法の中では、これらの領域はあまり手厚くカバーされていなかったので、これらの機能を使って自分でデータパイプラインを作ってみるなど、何らかの形で補完しておいた方が良かったかもしれません。（試験対策という意味でも、知っていれば確実に点が取れるものも多いので）

あと、（処理履歴、Fail-safe、Time Travel、キャッシュなど）各種のデータ保持期間は覚えるしかないので、チートシートなどを活用すると良いのではないかと思います。

ちなみに自分は、このチートシートの存在を試験を受けた後に知りました。。

* [Snowflake SnowPro Certification Exam Cheat Sheet](https://www.slideshare.net/JenoYamma/snowflake-snowpro-certification-exam-cheat-sheet)

また、上記のチートシートも便利そうではあるのですが、Snowflakeの特長はその豊富なメタデータとその活用にあると感じますので、各種メタデータとそのアクセス方法（SQLクエリ）を集めたチートシートを作っておくと、開発や運用の時に役に立ちそうだな、と思いました。

では。
