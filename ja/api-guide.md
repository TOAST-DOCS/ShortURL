## Application Service > ShortURL > APIガイド

### 基本情報
```http
API Endpoint: https://api-shorturl.cloud.toast.com
```

## 短縮URL

### 1. 作成
- 短縮URLを作成します。

[URL]
```http
POST /open-api/v1.0/appkeys/{appkey}/urls
Content-Type: application/json
```

#### リクエスト

[Path Variables]
| 値 |	タイプ | 必須かどうか | 説明 |
|---|---|---|---|
| appkey | String | O | サービスAppkey(**サービス管理**タブで確認可能) |

[Request Body]
| 値 |	タイプ | 必須かどうか | 説明 |
|---|---|---|---|
| url | String | O | 元のURL |
| domain | String | X | 短縮URLに使用するドメイン(ない場合はnh.nuで作成) |
| backHalf | String | X | 短縮URL ID(https://nh.nu/exampleではexampleを指す。ない場合はランダムに作成) |
| campaigns | List<String> | X | 所属するキャンペーンIDリスト |
```json
{
   "url": "https://nhn.com",
   "domain": "nh,nu",
   "campaigns": [0,1],
   "backHalf": "example"
}
```

#### レスポンス
```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "body": {
        "shortUrl": "http://nh.nu/a",
        "originUrl": "https://nhn.com",
        "status": "ACTIVE",
        "backHalfType": "AUTO",
        "startAt": "2021-03-26T03:35+0000",
        "endAt": "9999-12-31T00:00+0000"
    }
}
```

| 値 | タイプ | 説明 |
|---|---|---|
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 失敗メッセージ |
| body.shortUrl | String | 短縮されたURL |
| body.originUrl | String | 元のURL |
| body.status | String | 短縮URLの状態 |
| body.backHalfType | String | 短縮URLの作成方式 |
| body.startAt | String | 短縮URLの使用開始日 |
| body.endAt | String | 短縮URLの使用終了日 |

### 2. 検索
- 短縮URLを検索します。

[URL]
```http
POST /open-api/v1.0/appkeys/{appkey}/domains/{domain}/urls/{backHalf}
Content-Type: application/json
```

#### リクエスト

[Path Variables]
| 値 |	タイプ | 必須かどうか | 説明 |
|---|---|---|---|
| appkey | String | O | サービスAppkey(**サービス管理**タブで確認可能) |
| domain | String | O | ドメイン名 |
| backHalf | String | O | 短縮URL path ID |


#### レスポンス
```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "body": {
        "shortUrl": "http://nh.nu/a",
        "originUrl": "https://nhn.com",
        "status": "ACTIVE",
        "backHalfType": "AUTO",
        "startAt": "2021-03-26T03:35+0000",
        "endAt": "9999-12-31T00:00+0000"
    }
}
```

| 値 | タイプ | 説明 |
|---|---|---|
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 結果コード |
| header.resultMessage | String | 失敗メッセージ |
| body.shortUrl | String | 短縮されたURL |
| body.originUrl | String | 元のURL |
| body.status | String | 短縮URLの状態 |
| body.backHalfType | String | 短縮URLの作成方式 |
| body.startAt | String | 短縮URLの使用開始日 |
| body.endAt | String | 短縮URLの使用終了日 |



### 3. QRコード検索
- 短縮URLを作成します。

[URL]
```http
POST /domains/{domain}/urls/{backHalf}/qrcode
Content-Type: image/png
```

#### リクエスト

[Path Variables]
| 値 |	タイプ | 必須かどうか | 説明 |
|---|---|---|---|
| appkey | String | O | サービスAppkey(**サービス管理**タブで確認可能) |
| domain | String | O | ドメイン名 |
| backHalf | String | O | 短縮URL path ID |

#### レスポンス
```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "body": "iVBORw0KGgoAAAANSUhEUgAAAIIAAACCAQAAAACieC1QAAAA+0lEQVR4Xu3UsZHEIAwFUO0QkO024BnaIKMlbwNnuwHTkjO3wYwasDMCBp18wbHrxFJ6t4rMCzTigwE61QIf+ZOSAGizNILRCFIuj0yRPzQyeqoeZ9AKVjB6ScN66nMtlGmD0y4uhfPB2eN7Ypdy1JSPpUbSsHTPTNXqBEL6CtCDU8kdMC4urm0XAqGJuA+N9jcfiZS7L73FqaUqkfRcu4HMTk4jPHDpvdvbzCKpgcd2fIgq2Xx342w9aeSnlcWqk+OOcThzS1UifJ95aWpoO5UI/6ezB3h5E2TCb0J5vKQqExoD7rnNLBHK6ZaRUSNHPnExcVXJW33kX8g3k5xLHpTtgoMAAAAASUVORK5CYII="
}
```

| 値 | タイプ | 説明 |
|---|---|---|
| header.isSuccessful | Boolean | 成否 |
| header.resultCode | Integer | 失敗コード(0は正常) |
| header.resultMessage | String | 失敗メッセージ |
| body | String | Base64でエンコードされたPNGイメージ |
