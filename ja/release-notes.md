<!-- pre-align:aligned sig=3152e719e565 -->

<a id="application-service-shorturl-release-notes"></a>
## Application Service > ShortURL > リリースノート { #application-service-shorturl-release-notes }

<a id="march-10-2026"></a>
### 2026. 03. 10. { #march-10-2026 }

<!-- TODO: translate body -->

<a id="march-10-2026-feature-updates"></a>
#### 機能の改善/変更

<!-- TODO: translate body -->

<a id="april-25-2023"></a>
### 2023. 04. 25. { #april-25-2023 }

<a id="april-25-2023-feature-updates"></a>
#### 機能改善/変更
* 短縮URLの作成および修正時に簡単な説明(100文字制限)を入力できるように変更しました。

<a id="january-31-2023"></a>
### 2023. 01. 31. { #january-31-2023 }

<a id="january-31-2023-bug-fixes"></a>
#### バグ修正
* 原本URLにハングルなどASCII(7)エンコード範囲外の文字が含まれている時、短縮URLのリダイレクトが正常に行われない問題を修正しました。
  * 作成された短縮URLを介して原本URLにアクセスする場合、原本URLをASCII(7)文字列に変更してLocationヘッダに追加します。
  * この時、+ 文字はエンコードされずそのまま使われます。
    * たとえば、`https://nhn.com?query=안+녕`は`https://nhn.com?query=%EC%95%88+%EB%85%95`に変換され`+`文字を`%2B`にエンコードしません。

<a id="october-25-2022"></a>
### 2022. 10. 25. { #october-25-2022 }

<a id="october-25-2022-feature-updates"></a>
#### 機能改善/変更
* shortUrlを検索する時、状態値を使用できないように変更しました。
* shortUrlを検索する時、テキスト検索条件をshortUrlのbackHalfに制限するように変更しました。

<a id="june-30-2022"></a>
### 2022. 06. 30. { #june-30-2022 }

<a id="june-30-2022-feature-updates"></a>
#### 機能改善/変更
* APIエンドポイントのドメイン名が`api-shorturl.cloud.toast.com`から`api-shorturl.nhncloudservice.com`に変更されました。
* QRコードダウンロード機能が追加されました。
    * 作成された短縮URLのQRコードをクリックするとイメージをダウンロードできます。

<a id="march-29-2022"></a>
### 2022. 03. 29. { #march-29-2022 }

<a id="march-29-2022-feature-updates"></a>
#### 機能改善/変更
* queryParameter機能はプロジェクト単位で有効化または無効化できます。


<a id="november-23-2021"></a>
### 2021. 11. 23. { #november-23-2021 }

<a id="november-23-2021-feature-updates"></a>
#### 機能改善/変更
* ベータサービスから正式サービスに切り替わりました。
* 証明書更新機能の改善
    * 有効期限が切れた証明書が期限切れ状態と表示されます。
    * 編集ボタンを使用して証明書をcommon name(CN)が同じ証明書に更新できます。

<a id="november-23-2021-bug-fixes"></a>
#### バグ修正
* APIを介してshortUrlを作成する時、有効期限が正しく設定されなかった問題を修正しました。

<a id="september-28-2021"></a>
### 2021. 09. 28. { #september-28-2021 }

<a id="september-28-2021-feature-updates"></a>
#### 機能改善
ShortUrlの後ろにqueryParameterを付けて使用できます。
例) `nh.nu/abc` -> `www.coupang.com/vp/products/1821016708`の場合、 `nh.nu/abc?param=param`は`www.coupang.com/vp/products/1821016708?param=param`に接続されます。
<a id="september-28-2021-bug-fixes"></a>
#### バグ修正
* 証明書リストの状態表示色が実際の状態と合っていなかった問題を修正しました。

<a id="august-24-2021"></a>
### 2021. 08. 24. { #august-24-2021 }

<a id="august-24-2021-bug-fixes"></a>
#### バグ修正
* キャンペーンの所属URLを削除する場合、すべての所属URLが削除される問題を修正しました。

<a id="july-27-2021"></a>
### 2021. 07. 27. { #july-27-2021 }

<a id="july-27-2021-feature-updates"></a>
#### 機能改善/変更
* Cloud Trailでそれぞれのイベントを確認できます。

<a id="july-27-2021-bug-fixes"></a>
#### バグ修正
* ドメイン、証明書の共有対象を指定する時、使用できないプロジェクトが選択可能になっていた問題を修正しました。

<a id="june-29-2021"></a>
### 2021. 06. 29. { #june-29-2021 }

<a id="june-29-2021-feature-updates"></a>
#### 機能改善/変更
* すでにあるドメインの証明書を登録すると、証明書が登録されたプロジェクトの名前が案内されます。
* 最近登録したshortUrlがリストの最上部に表示されます。

<a id="june-29-2021-bug-fixes"></a>
#### バグ修正
* 短縮URL編集画面で原本URLを変更できる問題が修正されました。

<a id="may-25-2021"></a>
### 2021. 05. 25. { #may-25-2021 }

<a id="may-25-2021-feature-updates"></a>
#### 機能改善/変更
* [Console]ページ機能を追加
    * 照会 > URL画面にページ機能が追加されました。

<a id="april-27-2021"></a>
### 2021. 04. 27. { #april-27-2021 }

<a id="april-27-2021-new-service-release"></a>
#### 新規サービスリリース
* ShortURLを使用すると、文字数に制限があるさまざまな環境で、少ない文字数でWebページリンクを共有できます。
* 簡単に連動するためのRESTful APIを提供します。
