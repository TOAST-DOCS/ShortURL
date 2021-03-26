## Management > Service Monitoring > API 가이드

### 기본 정보
```
API Endpoint: https://api-shortly.cloud.toast.com
```

## 단축 URL

### 생성
- 단축 URL을 생성합니다.

[URL]
```http
POST /open-api/v1.0/appkeys/{appkey}/url
Content-Type: application/json
```

#### 요청

[Path Variables]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| appKey | String | Required | 서비스 Appkey(**서비스 관리** 탭에서 확인 가능) |

```json
{
   "url": "https://cloud.nhn.com",
   "domain": "nhn.com",
   "campaigns": [0,1],
   "backHalf": "example"
}
```

[Request Body]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| url | String | Required | 원본 URL |
| domain | String | X | 단축 URL에 사용할 도메인 (없을 경우 nh.nu로 생성) |
| backHalf | String | X | 단축 URL ID (https://nh.nu/example에서 `example`을 가리키며 없을 경우 랜덤 생성)|
| campaigns | List<String> | X | 소속될 캠페인 ID 목록 |

#### 응답
```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "body": {
       
    }
}
```

| 값 | 타입 | 설명 |
|---|---|---|
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 실패 코드(0은 정상) |
| header.resultMessage | String | 실패 메시지 |
| body.pk.serviceId | String | 서비스 고유 ID |


### QR 코드 검색
- 단축 URL을 생성합니다.

[URL]
```http
POST /qrcode/{domain}/{backHalf}
Content-Type: image/png
```

#### 요청

[Path Variables]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| appKey | String | Required | 서비스 Appkey(**서비스 관리** 탭에서 확인 가능) |

```json
{
 
}
```

[Request Body]
| 값 |	타입 | 필수 여부 | 설명 |
|---|---|---|---|
| url | String | Required | 원본 URL |
| domain | String | X | 단축 URL에 사용할 도메인 (없을 경우 nh.nu로 생성) |
| backHalf | String | X | 단축 URL ID (https://nh.nu/example에서 `example`을 가리키며 없을 경우 랜덤 생성)|
| campaigns | List<String> | X | 소속될 캠페인 ID 목록 |

#### 응답
```json
{
    "header": {
        "isSuccessful": true,
        "resultCode": 0,
        "resultMessage": "SUCCESS"
    },
    "body": {
       
    }
}
```

| 값 | 타입 | 설명 |
|---|---|---|
| header.isSuccessful | Boolean | 성공 여부 |
| header.resultCode | Integer | 실패 코드(0은 정상) |
| header.resultMessage | String | 실패 메시지 |
| body.pk.serviceId | String | 서비스 고유 ID |
