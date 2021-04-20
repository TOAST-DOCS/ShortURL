## Application Service > ShortURL > API 가이드

### 기본 정보
```http
API Endpoint: https://api-shortly.cloud.toast.com
```

## 단축 URL

### 1. 생성
- 단축 URL을 생성합니다.

[URL]
```http
POST /open-api/v1.0/appkeys/{appkey}/urls
Content-Type: application/json
```

#### 요청

[Path Variables]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| appKey | String | O | 서비스 Appkey(**서비스 관리** 탭에서 확인 가능) |

[Request Body]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| url | String | O | 원본 URL |
| domain | String | X | 단축 URL에 사용할 도메인(없을 경우 nh.nu로 생성) |
| backHalf | String | X | 단축 URL ID(https://nh.nu/example에서 example을 가리키며, 없을 경우 랜덤 생성) |
| campaigns | List<String> | X | 소속될 캠페인 ID 목록 |
```json
{
   "url": "https://nhn.com",
   "domain": "nh,nu",
   "campaigns": [0,1],
   "backHalf": "example"
}
```

#### 응답
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

| 값 | 타입 | 설명 |
|---|---|---|
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 실패 메시지 |
| body.shortUrl | String | 단축된 URL |
| body.originUrl | String | 원본 URL |
| body.status | String | 단축 URL 상태 |
| body.backHalfType | String | 단축 URL 생성 방식 |
| body.startAt | String | 단축 URL 사용 시작 날짜 |
| body.endAt | String | 단축 URL 사용 종료 날짜 |

### 2. 검색
- 단축 URL을 검색합니다.

[URL]
```http
POST /open-api/v1.0/appkeys/{appkey}/domains/{domain}/urls/{backHalf}
Content-Type: application/json
```

#### 요청

[Path Variables]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| appKey | String | O | 서비스 Appkey(**서비스 관리** 탭에서 확인 가능) |
| domain | String | O | 도메인 이름 |
| backHalf | String | O | 단축 URL path ID |


#### 응답
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

| 값 | 타입 | 설명 |
|---|---|---|
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 결과 코드 |
| header.resultMessage | String | 실패 메시지 |
| body.shortUrl | String | 단축된 URL |
| body.originUrl | String | 원본 URL |
| body.status | String | 단축 URL 상태 |
| body.backHalfType | String | 단축 URL 생성 방식 |
| body.startAt | String | 단축 URL 사용 시작 날짜 |
| body.endAt | String | 단축 URL 사용 종료 날짜 |



### 3. QR 코드 검색
- 단축 URL을 생성합니다.

[URL]
```http
POST /domains/{domain}/urls/{backHalf}/qrcode
Content-Type: image/png
```

#### 요청

[Path Variables]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| appKey | String | O | 서비스 Appkey(**서비스 관리** 탭에서 확인 가능) |
| domain | String | O | 도메인 이름 |
| backHalf | String | O | 단축 URL path ID |

#### 응답
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

| 값 | 타입 | 설명 |
|---|---|---|
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 실패 코드(0은 정상) |
| header.resultMessage | String | 실패 메시지 |
| body | String | Base64로 인코딩된 PNG 이미지 |
