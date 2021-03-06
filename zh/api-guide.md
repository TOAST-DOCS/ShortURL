## Application Service > ShortURL > API Guide

### Basic information
```http
API Endpoint: https://api-shorturl.cloud.toast.com
```

## Shortened URL

### 1. Create
- Create a shortened URL.

[URL]

```http
POST /open-api/v1.0/appkeys/{appkey}/urls
Content-Type: application/json
```

#### Request

[Path Variables]

| Value |	Type | Required? | Description |
|---|---|---|---|
| appkey | String | O | Service Appkey (**Manage Service** tab to be checked) |

[Request Body]

| Value |	Type | Required? | Description |
|---|---|---|---|
| url | String | O | Full URL |
| domain | String | X | The domain to use for shortened URL (create as nh.nu if there is none) |
| backHalf | String | X | Shortened URL ID (Refers to `example` in https://nh.nu/example; randomly create one if there is none) |
| campaigns | List<String> | X | List of campaign IDs to belong to |

```json
{
   "url": "https://nhn.com",
   "domain": "nh,nu",
   "campaigns": [0,1],
   "backHalf": "example"
}
```

#### Response
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

| Value | Type | Description |
|---|---|---|
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Failure message |
| body.shortUrl | String | Shortened URL |
| body.originUrl | String | Full URL |
| body.status | String | Shortened URL state |
| body.backHalfType | String | Shortened URL state |
| body.startAt | String | Date to start using the shortened URL |
| body.endAt | String | Date to end the use of the shortened URL |

### 2. Search
- Search for a shortened URL.

[URL]

```http
POST /open-api/v1.0/appkeys/{appkey}/domains/{domain}/urls/{backHalf}
Content-Type: application/json
```

#### Request

[Path Variables]

| Value |	Type | Required? | Description |
|---|---|---|---|
| appkey | String | O | Service Appkey (**Manage Service** tab to be checked) |
| domain | String | O | Domain name |
| backHalf | String | O | Shortened URL path ID |


#### Response
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

| Value | Type | Description |
|---|---|---|
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Result code |
| header.resultMessage | String | Failure message |
| body.shortUrl | String | Shortened URL |
| body.originUrl | String | Full URL |
| body.status | String | Shortened URL state |
| body.backHalfType | String | Method of creating the shortened URL |
| body.startAt | String | Date to start using the shortened URL |
| body.endAt | String | Date to end the use of the shortened URL |



### 3. Search for a QR code
- Create a shortened URL.

[URL]

```http
POST /domains/{domain}/urls/{backHalf}/qrcode
Content-Type: image/png
```

#### Request

[Path Variables]

| Value |	Type | Required? | Description |
|---|---|---|---|
| appkey | String | O | Service Appkey (**Manage Service** tab to be checked) |
| domain | String | O | Domain name |
| backHalf | String | O | Shortened URL path ID |

#### Response
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

| Value | Type | Description |
|---|---|---|
| header.isSuccessful | Boolean | Success |
| header.resultCode | Integer | Failure Code (0: Normal) |
| header.resultMessage | String | Failure message |
| body | String | Base64-encoded PNG image |
