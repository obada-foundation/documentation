# Data Repository Database Specification



## General Information

| Database Name | **Database Version** | **Database Engine** | Collections                                                  |
| ------------- | -------------------- | ------------------- | ------------------------------------------------------------ |
| MongoDB       | 3.6                  | Wired Tiger         | * metadata_collection <br />* events <br />* device_info_collection |



## metadata_collection

### Perpose

Collection contains transactions for obada assets

### Table Schema

#### Columns

| **column_position** | **column_name** | **column_type** | description                                                  |
| ------------------- | --------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id             | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |
| 2                   | asset_id        | String          | *UUID* (Universally Unique Identifier).<br /> Generated with [ramsey/uuid](https://github.com/ramsey/uuid) library |
| 3                   | label_id        | String          | Custom identifier that can be added by asset owner for the personal tracking purpose. |
| 4                   | metadata_url    | String          | The link to get the additional data about asset              |
| 5                   | device_info_url | String          | The link to get the device info information                  |
| 6                   | signatures      | Array           | The collection of registrar signatures (JWT tokens)          |
| 7                   | created_at      | Date            | Datetime of creation in UTC format                           |
| 8                   | updated_at      | Date            | Datetime of last update in UTC format                        |

#### Indexes

| **index_name** | **index_type**      | **column_name(s)**        | description                                                  |
| -------------- | ------------------- | ------------------------- | ------------------------------------------------------------ |
| ``_id_``       | Default `_id` Index | {<br/>    "_id" : 1<br/>} | More info about [default index](https://docs.mongodb.com/manual/indexes/#default-id-index) |

#### Document example

```javascript
{
    "_id" : ObjectId("5c98fdea051078000f6a1b22"),
    "asset_id" : "c7bbd680-4f18-11e9-a696-0242ac120003",
    "label_id" : "",
    "metadata_url" : "http://metadata.obada.io/c7bbd680-4f18-11e9-a696-0242ac120003",
    "device_info_url" : "http://metadata.obada.io/device-info/c7bbd680-4f18-11e9-a696-0242ac120003",
    "signatures" : [ 
        "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJyZWdpc3RyYXIub2JhZGEuaW8iLCJ2ZXJpZmljYXRpb25fdXJsIjoiaHR0cHM6XC9cL3JlZ2lzdHJhci5vYmFkYS5pb1wvdmVyaWZ5IiwidmVyaWZpY2F0aW9uX2h0dHBfbWV0aG9kIjoiUE9TVCIsInZlcmlmaWNhdGlvbl9odHRwX3Zhcl9uYW1lIjoic2lnbmF0dXJlIiwiaWF0IjoxNTUxMzk2NDM4LCJhdWQiOiI2M2QwMGM1Mi0zYmIwLTExZTktOWNjYS0wMjQyYWMxMjAwMDMiLCJyZWdpc3RyYXJfaWQiOiI5ZGI2MGI4NjVjNjg1OWQ2ODUzZDBiNjIzYzgyM2EyNiJ9.StIeyoLiLkM46D8nrWTDRakpWNYWorUZX6jyLuW7LWLn5jeHfWa7bmEoUYeQmJUj4UEP-KwZbyIrvxcZ3-2aPHTVMFw-JE66bXz9_vtJpft_bbewPwK42xHSEZzea2NkgzZCRDoJNUDbUaqJuHERx9pzvcQTAb1Clgw0KEIKMjhG8152u4YBoFjgcWbQ4AhgGnsL-EiNyyyG35HmhFRRoYzMDe8ETZ169dgtVlu8ZxOU88Hh6b97TWthkzSbIILN_cy0UWC0JCMIvVedu_loZUPzzrkSvacgDe6e-s3usIKvK3HR5lgVbDatiA1rf2-DdUMmC548YrjcAks6g2PX4qgCLRq8S_gJSWvzWmUAwvK5CiRG2KCGrKkNp2DhZt8xt27NWefJcfJMG47Qd1aLMizvpvx87U4VARR8L8kyR2ymtZTbwFAzBFlyBnOF8cJ3IoW1GkemdlS1fEY5n1DOSi6vXJkWfPIy0-GN49mwxydydalEn4OC9_37Qeff4UqRA2QIrMRRkpRrbCTQVxwAjY13gGAlURAXKVKLdiwSV2-8PA63n_xcszF0IlQmgk62aIrVjdbEKhT80nW0Chbf52mOXJj5QRAZdkKX2TH-dgvZXlcLW0SJWZU8nGSQSsdxv3Sltu59skL4_GfBeQGDi4j5-5WplY7miXu5R8kLzqg"
    ],
    "updated_at" : ISODate("2019-03-25T16:12:26.000Z"),
    "created_at" : ISODate("2019-03-25T16:12:26.000Z")
}
```



## events

### Perpose

Collection contains changes log for obada assets. The functionality is done on top of [Laravel Auditing Library]([http://www.laravel-auditing.com/](http://www.laravel-auditing.com/)). 

### Schema

#### Columns

| **column_position** | **column_name** | **column_type** | description                                                  |
| ------------------- | --------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id             | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |
| 2                   | old_values      | String          | *UUID* (Universally Unique Identifier).<br /> Generated with [ramsey/uuid](https://github.com/ramsey/uuid) library |
| 3                   | new_values      | String          | Custom identifier that can be added by asset owner for the personal tracking purpose. |
| 4                   | event           | String          | The link to get the additional data about asset              |
| 5                   | auditable_id    | String          | The link to get the device info information                  |
| 6                   | auditable_type  | Array           | The collection of registrar signatures (JWT tokens)          |
| 7                   | user_id         | Null            | Not used                                                     |
| 8                   | user_type       | Null            | Not used                                                     |
| 9                   | url             | String          |                                                              |
| 10                  | ip_address      | String          |                                                              |
| 11                  | user_agent      | String          |                                                              |
| 12                  | tags            | Null            |                                                              |
| 13                  | updated_at      | Date            | Datetime of last update in UTC format. Can be removed.       |
| 14                  | created_at      | Date            | Datetime of creation in UTC format                           |

#### Indexes

| **index_name** | **index_type**      | **column_name(s)**        | description                                                  |
| -------------- | ------------------- | ------------------------- | ------------------------------------------------------------ |
| ``_id_``       | Default `_id` Index | {<br/>    "_id" : 1<br/>} | More info about [default index](https://docs.mongodb.com/manual/indexes/#default-id-index) |

#### Document example

```javascript
{
    "_id" : ObjectId("5c7028ed8d160c0013496d05"),
    "old_values" : "[]",
    "new_values" : "{\"asset_id\":\"5082d334-36c2-11e9-95b1-0242ac120003\",\"label_id\":\"qr_code\",\"metadata_url\":\"http:\\/\\/metadata.obada.io\\/5082d334-36c2-11e9-95b1-0242ac120003\",\"device_info_url\":\"http:\\/\\/metadata.obada.io\\/device-info\\/5082d334-36c2-11e9-95b1-0242ac120003\",\"_id\":{\"$oid\":\"5c7028ed8d160c0013496d04\"}}",
    "event" : "created",
    "auditable_id" : "5c7028ed8d160c0013496d04",
    "auditable_type" : "App\\Entities\\Transaction",
    "user_id" : null,
    "user_type" : null,
    "url" : "http://blockchain.obada.io/v0.0.1?",
    "ip_address" : "167.99.112.146",
    "user_agent" : "GuzzleHttp/6.3.3 curl/7.61.1 PHP/7.1.21",
    "tags" : null,
    "updated_at" : ISODate("2019-02-22T16:53:01.000Z"),
    "created_at" : ISODate("2019-02-22T16:53:01.000Z")
}
```

## device_info_collection

### Perpose

Collection contains transactions for obada assets

### Table Schema

#### Columns

| **column_position** | **column_name** | **column_type** | description                                                  |
| ------------------- | --------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id             | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |
| 2                   | asset_id        | String          | *UUID* (Universally Unique Identifier).<br /> Generated with [ramsey/uuid](https://github.com/ramsey/uuid) library |
| 3                   | label_id        | String          | Custom identifier that can be added by asset owner for the personal tracking purpose. |
| 4                   | metadata_url    | String          | The link to get the additional data about asset              |
| 5                   | device_info_url | String          | The link to get the device info information                  |
| 6                   | signatures      | Array           | The collection of registrar signatures (JWT tokens)          |
| 7                   | created_at      | Date            | Datetime of creation in UTC format                           |
| 8                   | updated_at      | Date            | Datetime of last update in UTC format                        |

#### Indexes

| **index_name** | **index_type**      | **column_name(s)**        | description                                                  |
| -------------- | ------------------- | ------------------------- | ------------------------------------------------------------ |
| ``_id_``       | Default `_id` Index | {<br/>    "_id" : 1<br/>} | More info about [default index](https://docs.mongodb.com/manual/indexes/#default-id-index) |

#### Document example

```javascript
{
    "_id" : ObjectId("5c98fdea051078000f6a1b22"),
    "asset_id" : "c7bbd680-4f18-11e9-a696-0242ac120003",
    "label_id" : "",
    "metadata_url" : "http://metadata.obada.io/c7bbd680-4f18-11e9-a696-0242ac120003",
    "device_info_url" : "http://metadata.obada.io/device-info/c7bbd680-4f18-11e9-a696-0242ac120003",
    "signatures" : [ 
        "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJpc3MiOiJyZWdpc3RyYXIub2JhZGEuaW8iLCJ2ZXJpZmljYXRpb25fdXJsIjoiaHR0cHM6XC9cL3JlZ2lzdHJhci5vYmFkYS5pb1wvdmVyaWZ5IiwidmVyaWZpY2F0aW9uX2h0dHBfbWV0aG9kIjoiUE9TVCIsInZlcmlmaWNhdGlvbl9odHRwX3Zhcl9uYW1lIjoic2lnbmF0dXJlIiwiaWF0IjoxNTUxMzk2NDM4LCJhdWQiOiI2M2QwMGM1Mi0zYmIwLTExZTktOWNjYS0wMjQyYWMxMjAwMDMiLCJyZWdpc3RyYXJfaWQiOiI5ZGI2MGI4NjVjNjg1OWQ2ODUzZDBiNjIzYzgyM2EyNiJ9.StIeyoLiLkM46D8nrWTDRakpWNYWorUZX6jyLuW7LWLn5jeHfWa7bmEoUYeQmJUj4UEP-KwZbyIrvxcZ3-2aPHTVMFw-JE66bXz9_vtJpft_bbewPwK42xHSEZzea2NkgzZCRDoJNUDbUaqJuHERx9pzvcQTAb1Clgw0KEIKMjhG8152u4YBoFjgcWbQ4AhgGnsL-EiNyyyG35HmhFRRoYzMDe8ETZ169dgtVlu8ZxOU88Hh6b97TWthkzSbIILN_cy0UWC0JCMIvVedu_loZUPzzrkSvacgDe6e-s3usIKvK3HR5lgVbDatiA1rf2-DdUMmC548YrjcAks6g2PX4qgCLRq8S_gJSWvzWmUAwvK5CiRG2KCGrKkNp2DhZt8xt27NWefJcfJMG47Qd1aLMizvpvx87U4VARR8L8kyR2ymtZTbwFAzBFlyBnOF8cJ3IoW1GkemdlS1fEY5n1DOSi6vXJkWfPIy0-GN49mwxydydalEn4OC9_37Qeff4UqRA2QIrMRRkpRrbCTQVxwAjY13gGAlURAXKVKLdiwSV2-8PA63n_xcszF0IlQmgk62aIrVjdbEKhT80nW0Chbf52mOXJj5QRAZdkKX2TH-dgvZXlcLW0SJWZU8nGSQSsdxv3Sltu59skL4_GfBeQGDi4j5-5WplY7miXu5R8kLzqg"
    ],
    "updated_at" : ISODate("2019-03-25T16:12:26.000Z"),
    "created_at" : ISODate("2019-03-25T16:12:26.000Z")
}
```