<!-- pre-align:aligned sig=b1e01460c70d -->

<a id="application-service-shorturl-console-user-guide"></a>
## Application Service > ShortURL > コンソール使用ガイド { #application-service-shorturl-console-user-guide }

<a id="url"></a>
## URL { #url }

<a id="add-shortened-url"></a>
### 短縮URLの追加 { #add-shortened-url }
- **照会 > URL**タブで**URL追加**ボタンを押して、新しい短縮URLを追加できます。
- 元のURL、ドメインを選択して新しい短縮URLを追加します。
- 任意のURLを作成するには、**URLの種類 > ユーザー入力**を選択して、任意のURLを入力します。
  - 作成された短縮URLを介して原本URLにアクセスする場合、原本URLをASCII(7)文字列に変更してLocationヘッダに追加します。
  - この時、+ 文字はエンコードされずそのまま使われます。
    - たとえば、`https://nhn.com?query=안+녕`は`https://nhn.com?query=%EC%95%88+%EB%85%95`に変換され`+`文字を`%2B`にエンコードしません。
- **オープン日時**と**有効期限**は、追加されたURLを介して接続可能な期間で、特定の時間以降にアクセスを望まない場合に便利です。

<a id="view-shortened-url"></a>
### 短縮URL照会 { #view-shortened-url }
- **照会 > URL**タブで、追加したURL情報を確認できます。
- **ドメイン** そして**検索ワード**を入力してURLを検索できます。
- **コピー**ボタンを押して、簡単にリンクをコピーできます。
- **無効化**ボタンを押して、いつでも使用している短縮URLへのアクセスを止めることができます。
- **削除**ボタンを押して、今後使用しない短縮URLを削除できます。



<a id="campaign"></a>
## キャンペーン { #campaign }

<a id="add-campaign"></a>
### キャンペーン追加 { #add-campaign }
- **照会 > キャンペーン**タブで**キャンペーン追加**ボタンを押して、新しいキャンペーンを追加できます。
- **キャンペーン**は、複数の短縮URLを含めることができるイベントグループです。
- **所属URL**に任意のURLを追加して管理できます。
- **編集**ボタンを押して**所属URL**を追加または削除できます。
- **詳細**ボタンを押してキャンペーンに含まれる短縮URLリストを確認できます。

<a id="view-campaign"></a>
### キャンペーン照会 { #view-campaign }
- **照会 > キャンペーン**タブで**キャンペーン**情報を確認できます。
- **ドメイン**、**状態**、そして**検索ワード**を入力してキャンペーンを検索できます。


<a id="domain"></a>
## ドメイン { #domain }

<a id="register-dns"></a>
### DNS登録 { #register-dns }
> IP: 180.210.71.141
- **ドメイン**を追加するにはDNSサーバーの上のIPで**ドメイン**が登録されている必要があります。
    - **Aレコード**を見て検証するため、**Aレコード**が存在している必要があります。
- **nslookup**コマンドを使用して、以下のようにDNSが正常に登録されているかを確認できます。
```bash
...
Name:   nh.nu
Address: 180.210.71.141
```
<a id="add-domain"></a>
### ドメイン追加 { #add-domain }
- **管理 > ドメイン**タブで**ドメイン追加**ボタンを押してユーザーが所有しているドメインを追加できます。
- **ドメイン**を登録する時、IPが短縮URLサーバーIPであるかを検証します。
- **公開範囲**は、同じ組織内の複数のプロジェクトで**ドメイン**を共有して使用できるように提供します。
- **詳細**ボタンを押してドメインの詳細な情報を確認できます。

<a id="view-domain"></a>
### ドメイン照会 { #view-domain }
- **管理 > ドメイン**タブで**ドメイン**報を確認できます。
- **詳細**ボタンを押して、詳細なドメイン情報を確認できます。



<a id="certificate"></a>
## 証明書 { #certificate }

<a id="certificate-file-format"></a>
### 証明書ファイル形式 { #certificate-file-format }
- **.pem**形式の証明書ファイルのみサポートします。
- [passphrase](#passphrase-削除)が削除された証明書のみ追加できます。
- ファイルには証明書(チェーン)情報と、秘密鍵情報が含まれています。

```
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
-----BEGIN RSA PRIVATE KEY-----
...
-----END RSA PRIVATE KEY-----
```

<a id="delete-passphrase"></a>
### passphrase削除 { #delete-passphrase }
- passphraseは、次のコマンドを使用して削除できます。
```bash
openssl rsa -in input.key -out output.key
```

<a id="how-to-create-a-certificate-file-pem"></a>
### 証明書ファイル(.pem)の作成方法 { #how-to-create-a-certificate-file-pem }
1. 証明書情報を**.pem**形式に変換します。
2. 証明書チェーンと秘密鍵を含む単一の**.pem**ファイルを作成します。

```bash
cat mydomain.crt mydomain.key root-ca-chain.pem > mydomain.pem
```

- **cat**コマンドを利用してresult.pem 1個のファイルに統合する例です。
- 統合されたresult.pemファイルをテキストエディタで開き、PEM内容間が区分されているかを必ず確認する必要があります。
- ルート/チェーン証明書は違いがある場合があります。


<a id="add-certificate"></a>
### 証明書の追加 { #add-certificate }
- **管理 > 証明書**タブで**証明書追加**ボタンを押してユーザーが所有している証明書を追加できます。
- **証明書**をアップロードすると、証明書を検証して使用することができる証明書の場合、自動的に情報がコンソールに表示されます。
    - すでに使われている証明書は使用できません。
- **公開範囲**は、同じ組織内の複数のプロジェクトで**証明書**を共有して使用できるように提供します。
    - _wildcard_証明書の場合、1つだけ登録できるため、証明書を共有されると使用できます。
- **詳細**ボタンを押して、証明書の詳細な情報を確認できます。

<a id="view-certificate"></a>
### 証明書の照会 { #view-certificate }
- **管理 > 証明書**タブで**証明書**情報を確認できます。
- **詳細**ボタンを押して、詳細な証明書情報を確認できます。

<a id="renew-certificate"></a>
### 証明書の更新 { #renew-certificate }
- **管理 > 証明書**タブで各証明書の**編集**ボタンをクリックして証明書を更新できます。
    - Common name(CN)が同じ証明書のみ登録可能です。
    - 期限が既に登録されている証明書より後の証明書のみ登録可能です。
