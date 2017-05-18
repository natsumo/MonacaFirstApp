# 【Monaca問題集】<br>オンラインランキング機能を作ってみよう！<br>「連打ゲーム」
_2017/05/17作成 (2017/05/18修正)_

![RendaGame](/readme-img/RendaGame.png)

* Monacaデバッガー使用時(iPhone6)の画面例です

GitHub<br>
**https://github.com/natsumo/MonacaFirstApp**

<div style="page-break-before:always"></div>

## コンテンツ概要

* ニフティクラウドmobile backend の機能『データストア』を学習するための問題集です
 * ニフティクラウドmobile backend の利用登録（無料）が必要です。
* 問題用プロジェクトにはオンラインランキング機能が実装されていない状態の「連打ゲーム」です
 * 既に実装済みのニフティクラウドmobile backend を利用するための準備（SDK導入など）方法の詳細はこちらをご覧ください。<br>http://mb.cloud.nifty.com/doc/current/introduction/quickstart_ios.html

## 問題について

* 問題は２問あります
* ２問クリアすると「連打ゲーム」にオンラインランキング機能を実装したアプリが完成します
* Monaca（ハイブリットアプリ開発環境）を使用してアプリを作成します<br>https://ja.monaca.io/
 * アカウントをお持ちでない場合は会員登録（無料）が必要です。
* ブラウザ環境にInternet Explorerは使用できません
 * Google Chrome（推奨）をご使用ください。

<div style="page-break-before:always"></div>

## 問題に取り組む前の準備
### Monacaでプロジェクトインポートしてアプリを起動

![Monaca](/readme-img/Monaca.png)

▼問題用プロジェクト▼<br>
**https://github.com/natsumo/MonacaFirstApp/archive/Question.zip**

1. Monacaにログインします<br>https://ja.monaca.io/
1. 左上の「Import Project」をクリックします
1. 「プロジェクト名」を入力します　例）「連打アプリ」
1. 「インポート方法」の「URLを指定してインポート」をチェックし、上記リンク（問題用プロジェクト）をコピーし、貼り付けます
1. 「インポート」をクリックするとインポートされたプロジェクトが作成されます
1. 作成されたプロジェクトを「開く」をクリックして開きます
1. プロジェクトが開き、プレビュー画面が表示されます
 * プレビュー画面で遊んでみましょう！
 * Monacaデバッガーも使用可能です<br>https://ja.monaca.io/debugger.html

<div style="page-break-before:always"></div>

#### 「連打ゲーム」の操作方法

1. 「Start」ボタンをタップします
2. 「3」,「2」,「1」とカウントダウンし、「スタート！」から「タイムアップ！」の10秒間「◎」の部分がタップできるようになります
3. 10秒間の間に何回タップできるかを競う単純なゲームです
4. 10秒経つと名前を入力するアラートが表示されますので、入力し「OK」をクリックします
5. 画面に名前とスコアが表示されます
 * 4.で「キャンセル」をクリックした場合は「保存がキャンセルされました」と表示されます

※ __注意__：問題に取り組む前の状態では「ランキングを見る」ボタンをタップしてもランキングは表示されません

<div style="page-break-before:always"></div>

### アプリの新規作成とAPIキーの設定

![mBaaS](/readme-img/mBaaS.png)

*  ニフティクラウドmobile backend にログインしアプリの新規作成を行います
 * アプリ名はわかりやすいものにしましょう。例）「renda」
* アプリが作成されるとAPIキーが２種類（アプリケーションキーとクライアントキー）発行されます
 * 次で使用します。

![Monaca](/readme-img/Monaca.png)

* `js/tapGame.js`を編集します
* 先程ニフティクラウドmobile backendのダッシュボード上で確認したAPIキーを、それぞれ`YOUR_NCMB_APPLICATION_KEY`と`YOUR_NCMB_CLIENT_KEY`に貼り付けます

 ![問題0-1](/readme-img/0-1.png)

* このとき、ダブルクォーテーション（`"`）を消さないように注意してください！

<div style="page-break-before:always"></div>

## 【問題１】<br>名前とスコアの保存をしてみよう！
`js/tapGame.js`を開きます。下図の__`saveScore`__ メソッドを編集し、引数の__`name`__ （アラートで入力した名前）と__`score`__ （連打ゲームでタップした回数）の値をmBaaSに保存する処理をコーディングしてください

![問題1-1](/readme-img/1-1.png)

* データストアに保存先クラスを作成します
 * クラス名は「`GameScore`」としてください
* `name`を保存するフィールドを「`name`」、`score`を保存するフィールドを「`score`」として保存してください

### ヒント
* ニフティクラウドmobile backend のドキュメントページをご活用ください<br>http://mb.cloud.nifty.com/doc/current/datastore/basic_usage_monaca.html

<div style="page-break-before:always"></div>

### コーディング後の作業
問題１のコーディングが完了したら、下記の作業を行います

#### 【作業1-1】
それぞれ該当する箇所に以下の処理を追記して、実行時にコンソールにログを表示できるようにします

* 保存に成功した場合の処理を行う箇所に追記

 ![code1](/readme-img/code1.png)

* 保存に失敗した場合の処理を行う箇所に追記

 ![code2](/readme-img/code2.png)

#####  コンソールログの確認方法（ブラウザのコンソール表示）
* プレビュー画面の場合：【Windows】→「F12」キーまたは「Ctrl+Shift+K」、【Mac】「Command+Option+I」で表示されます
* デバッガーの場合：画面のアイコンをタップし、「!」マークのアイコンをクリックすると「App Log」画面に表示されます

※ __注意__：入力が完了したら必ず__「保存」をクリック__してプロジェクトを保存してください！Windowsの場合「Ctrl+S」、iOSの場合「Command+S」でも保存可能です。

<div style="page-break-before:always"></div>

#### 【作業1-2】
プレビュー画面あるいはデバッガーで実行し、「Start」ボタンを押してゲームを遊びます

* 名前を入力し、「OK」をクリックすると【問題１】で作成した`saveScore`メソッドが呼ばれ、データが保存されます
* このとき下記のいずれかのログが出力されます
 * 保存成功時：「`保存に成功しました。`」
 * 保存失敗時：「`保存に失敗しました。エラー:************`」

<div style="page-break-before:always"></div>

### 【問題１】答え合わせ

#### ニフティクラウドmobile backend上での確認
![mBaaS](/readme-img/mBaaS.png)

* 保存されたデータを確認しましょう
 * 「データストア」をクリックすると、「`GameScore`」クラスにデータが登録されていることが確認できます。

 ![ans1-1](/readme-img/ans1-1.png)

* 上図はスコアが35連打で名前を「あいうえお」とした場合の例です。

<div style="page-break-before:always"></div>

#### コードの答え合わせ

![Monaca](/readme-img/Monaca.png)

* 模範解答は以下です

 ![Answer1](/readme-img/Answer1.png)

<div style="page-break-before:always"></div>

## 【問題２】<br>ランキングを表示しよう！
`js/Ranking.js`を開きます。下図の`checkRanking`メソッドを編集し、データストアの`GameScore`クラスに保存した`name`と`score`のデータを`score`の降順（スコアの高い順）で検索・取得する処理をコーディングしてください

![問題2-1](/readme-img/2-1.png)

* 検索データ件数は５件とします

### ヒント
* ニフティクラウドmobile backend のドキュメントページをご活用ください<br>http://mb.cloud.nifty.com/doc/current/datastore/basic_usage_monaca.html<br>http://mb.cloud.nifty.com/doc/current/datastore/ranking_monaca.html

<div style="page-break-before:always"></div>

### コーディング後の作業
問題２のコーディングが完了したら、下記の作業を行います

#### 【作業2-1】
それぞれ該当する箇所に以下の処理を追記して、実行時にコンソールにログを表示できるようにします

* 検索に成功した場合の処理を行う箇所に追記

 ![code3](/readme-img/code3.png)

* 検索に失敗した場合の処理を行う箇所に追記

 ![code4](/readme-img/code4.png)

#####  コンソールログの確認方法（ブラウザのコンソール表示）
* プレビュー画面の場合：【Windows】→「F12」キーまたは「Ctrl+Shift+K」、【Mac】「Command+Option+I」で表示されます
* デバッガーの場合：画面のアイコンをタップし、「!」マークのアイコンをクリックすると「App Log」画面に表示されます

※ __注意__：入力が完了したら必ず__「保存」をクリック__してプロジェクトを保存してください！Windowsの場合「Ctrl+S」、iOSの場合「Command+S」でも保存可能です。

<div style="page-break-before:always"></div>

#### 【作業2-2】
プレビュー画面あるいはデバッガーで実行し、「ランキングを見る」ボタンをタップします
* 画面起動後、`checkRanking`メソッドが呼ばれ、【問題１】で保存されたデータが検索・取得されます
* このとき下記のいずれかのログが出力されます
 * 保存成功時：「`保存に成功しました。`」
 * 保存失敗時：「`検索に失敗しました。エラー:******`」

* 検索の状態（成功・失敗）に関係なく、「ランキングを見る」ボタンをタップしても、まだランキングは表示されません

#### 【作業2-3】
検索に成功したら、該当する箇所に以下の処理を追記して、取得した値から必要なデータを取り出し、ランキング画面へ反映させる`setData`メソッドを呼びます

* 検索に成功した場合の処理を行う箇所に追記

 ![code5](/readme-img/code5.png)


#### 【作業2-4】
プレビュー画面あるいはデバッガーで実行し、「ランキングを見る」ボタンを押します

* 先ほどのスコアが表示されれば完成です！おめでとうございます★

<div style="page-break-before:always"></div>

### 【問題２】答え合わせ

#### ランキング画面の確認

![Monaca](/readme-img/Monaca.png)

* ランキング画面を確認しましょう
 * アプリで「ランキングを見る」をタップすると以下のようにランキングが表示されます

 ![ans2-1](/readme-img/ans2-1.png)

* 上図は３回遊んだ場合の例です。複数回遊んで、ランキングが表示されることを確認しましょう！

<div style="page-break-before:always"></div>

#### コードの答え合わせ

![Monaca](/readme-img/Monaca.png)

* 模範解答は以下です

 ![Answer2](/readme-img/Answer2.png)

## 参考

* 問題の回答を実装した完全なプロジェクトをご用意しています

▼完成版プロジェクト▼<br>**https://github.com/natsumo/MonacaFirstApp/archive/AnswerProject.zip**

* APIキーを設定してご利用ください
