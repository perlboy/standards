## Get Payees

<a id="opIdgetPayees"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://myserver.com/cds-au/banking/v1/payees \
  -H 'Accept: application/json' \
  -H 'x-v: 1' \
  -H 'x-min-v: 1' \
  -H 'x-<<PID>>-Id: string' \
  -H 'x-Correlation-Id: string' \
  -H 'Authorization: Bearer {access-token}'

```

```javascript
var headers = {
  'Accept':'application/json',
  'x-v':'1',
  'x-min-v':'1',
  'x-<<PID>>-Id':'string',
  'x-Correlation-Id':'string',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://myserver.com/cds-au/banking/v1/payees',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /payees`

*Payee Data.*

Obtain a list of pre-registered payees.

<h3 id="getpayees-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|x-v|header|integer(int32)|true|Version of the API end point requested by the client. Must be set to a positive integer. If the version(s) requested is not supported then the provider should respond with a `406 Not Acceptable`.|
|x-min-v|header|integer(int32)|false|Minimum version of the API end point requested by the client. Must be set to a positive integer if provided. The provider should respond with the highest supported version between `x-min-v` and `x-v`.|
|x-<<PID>>-Id|header|string|false|A provider specific version of extension fields. Should not be used in conjunction with `x-min-v`.|
|x-Correlation-Id|header|string|false|The version of the API end point that the provider has responded with.|
|type|query|[PayeeTypeEnum](#schemapayeetypeenum)|false|Filter on type payee.|
|page|query|integer(int32)|false|Page  of results to  request  (standard  pagination).|
|page-size|query|integer(int32)|false|Page  size to  request. Default is  25 (standard pagination).|

#### Detailed descriptions

**x-v**: Version of the API end point requested by the client. Must be set to a positive integer. If the version(s) requested is not supported then the provider should respond with a `406 Not Acceptable`.

**x-min-v**: Minimum version of the API end point requested by the client. Must be set to a positive integer if provided. The provider should respond with the highest supported version between `x-min-v` and `x-v`.

If all versions requested are not supported then the provider should respond with a `406 Not Acceptable`.

#### Enumerated Values

|Parameter|Value|
|---|---|
|type|DOMESTIC|
|type|INTERNATIONAL|
|type|BILLER|

> Example responses

> 200 Response

```json
{
  "links": {
    "self": "http://example.com",
    "first": "http://example.com",
    "prev": "http://example.com",
    "next": "http://example.com",
    "last": "http://example.com"
  },
  "meta": {
    "totalRecords": 6,
    "totalPages": 2
  },
  "data": {
    "payees": [
      {
        "payeeId": "string",
        "nickname": "string",
        "description": "string",
        "type": "DOMESTIC"
      }
    ]
  }
}
```

<h3 id="getpayees-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[PayeesResponse](#schemapayeesresponse)|

<aside class="notice">
To perform this operation, you must be authenticated by means of one of the following methods:
openId ( Scopes: bank_payees )
</aside>

## Get Payee Detail

<a id="opIdgetPayee"></a>

> Code samples

```shell
# You can also use wget
curl -X GET https://myserver.com/cds-au/banking/v1/payees/{payeeId} \
  -H 'Accept: application/json' \
  -H 'x-v: 1' \
  -H 'x-min-v: 1' \
  -H 'x-<<PID>>-Id: string' \
  -H 'x-Correlation-Id: string' \
  -H 'Authorization: Bearer {access-token}'

```

```javascript
var headers = {
  'Accept':'application/json',
  'x-v':'1',
  'x-min-v':'1',
  'x-<<PID>>-Id':'string',
  'x-Correlation-Id':'string',
  'Authorization':'Bearer {access-token}'

};

$.ajax({
  url: 'https://myserver.com/cds-au/banking/v1/payees/{payeeId}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

`GET /payees/{payeeId}`

*Detailed Payee Data.*

Obtain detailed information on a single payee.

<h3 id="getpayee-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|payeeId|path|[PayeeId](#schemapayeeid)|true|ID of the payee requested.|
|x-v|header|integer(int32)|true|Version of the API end point requested by the client. Must be set to a positive integer. If the version(s) requested is not supported then the provider should respond with a `406 Not Acceptable`.|
|x-min-v|header|integer(int32)|false|Minimum version of the API end point requested by the client. Must be set to a positive integer if provided. The provider should respond with the highest supported version between `x-min-v` and `x-v`.|
|x-<<PID>>-Id|header|string|false|A provider specific version of extension fields. Should not be used in conjunction with `x-min-v`.|
|x-Correlation-Id|header|string|false|The version of the API end point that the provider has responded with.|

#### Detailed descriptions

**x-v**: Version of the API end point requested by the client. Must be set to a positive integer. If the version(s) requested is not supported then the provider should respond with a `406 Not Acceptable`.

**x-min-v**: Minimum version of the API end point requested by the client. Must be set to a positive integer if provided. The provider should respond with the highest supported version between `x-min-v` and `x-v`.

If all versions requested are not supported then the provider should respond with a `406 Not Acceptable`.

> Example responses

> 200 Response

```json
{
  "links": {
    "self": "http://example.com",
    "first": "http://example.com",
    "prev": "http://example.com",
    "next": "http://example.com",
    "last": "http://example.com"
  },
  "data": {
    "payeeId": "string",
    "nickname": "string",
    "description": "string",
    "type": "DOMESTIC",
    "payee": {
      "payeeType": "domestic",
      "domesticAccountPayee": {
        "domesticPayeeType": "payId",
        "name": "string",
        "identifier": "string",
        "type": "EMAIL"
      }
    }
  }
}
```

<h3 id="getpayee-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|successful operation|[PayeeResponse](#schemapayeeresponse)|

### Response Headers

|Status|Header|Type|Format|Description|
|---|---|---|---|---|
|200|x-v|integer|int32|The version of the API end point that the provider has responded with.|
|200|x-Correlation-Id|string||Reflected value of the correlation ID provided by the data consumer in the request headers. If no correlation ID was provided in the request this header should not be supplied. If a correlation ID was provided in the request then this header is mandatory.|

<aside class="notice">
To perform this operation, you must be authenticated by means of one of the following methods:
openId ( Scopes: bank_payees )
</aside>