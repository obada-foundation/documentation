# Data Repository Database Specification



## General Information

| Database Name | **Database Version** | **Database Engine** | Collections                                                  |
| ------------- | -------------------- | ------------------- | ------------------------------------------------------------ |
| MongoDB       | 3.6                  | Wired Tiger         | * metadata_collection <br />* events <br />* device_info_collection |



## metadata_collection

### Perpose

Collection contains dynamic characteristcs of the Obada asset

### Table Schema

#### Columns

| **column_position** | **column_name** | **column_type** | description                                                  |
| ------------------- | --------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id             | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |
| 2                   | asset_id        | String          | *UUID* (Universally Unique Identifier).<br /> Generated with [ramsey/uuid](https://github.com/ramsey/uuid) library |
| 3                   | data            | Array           | Dynamic key/value collection of asset properties             |
| 4                   | created_at      | Date            | Datetime of creation in UTC format                           |
| 5                   | created_at      | Date            | Datetime of last update in UTC format                        |

#### Indexes

| **index_name** | **index_type**      | **column_name(s)**        | description                                                  |
| -------------- | ------------------- | ------------------------- | ------------------------------------------------------------ |
| ``_id_``       | Default `_id` Index | {<br/>    "_id" : 1<br/>} | More info about [default index](https://docs.mongodb.com/manual/indexes/#default-id-index) |

#### Document example

```javascript
{
    "_id" : ObjectId("5c635813408b120011209162"),
    "asset_id" : "c5edd368-2f1e-11e9-879b-0242ac150005",
    "data" : [ 
        {
            "color" : "green",
            "cable": "3 meters"
        }
    ],
    "updated_at" : ISODate("2019-02-12T23:34:43.000Z"),
    "created_at" : ISODate("2019-02-12T23:34:43.000Z")
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
    "_id" : ObjectId("5c75cdcb315a090012010bc3"),
    "old_values" : "[]",
    "new_values" : "{\"asset_id\":\"859f993e-3a1f-11e9-b873-0242ac120003\",\"_id\":{\"$oid\":\"5c75cdcb315a090012010bc2\"}}",
    "event" : "created",
    "auditable_id" : "5c75cdcb315a090012010bc2",
    "auditable_type" : "App\\Entities\\Metadata",
    "user_id" : null,
    "user_type" : null,
    "url" : "http://metadata.obada.io/?",
    "ip_address" : "167.99.112.146",
    "user_agent" : "GuzzleHttp/6.3.3 curl/7.61.1 PHP/7.1.21",
    "tags" : null,
    "updated_at" : ISODate("2019-02-26T23:37:47.000Z"),
    "created_at" : ISODate("2019-02-26T23:37:47.000Z")
}
```

## device_info_collection

### Perpose

Collection contains transactions for obada assets

### Table Schema

#### Columns

| **column_position** | **column_name**       | **column_type** | description                                                  |
| ------------------- | --------------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id                   | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |
| 2                   | asset_id              | String          | *UUID* (Universally Unique Identifier).<br /> Generated with [ramsey/uuid](https://github.com/ramsey/uuid) library |
| 3                   | serial_number         | String          |                                                              |
| 4                   | part_number           | String          |                                                              |
| 5                   | model_number          | String          |                                                              |
| 6                   | manufacturer          | String          |                                                              |
| 7                   | categories            | Array           |                                                              |
| 8                   | condition             | String          |                                                              |
| 9                   | description           | String          |                                                              |
| 10                  | price                 | Double          |                                                              |
| 11                  | currency_code         | String          |                                                              |
| 12                  | location_country_code | String          |                                                              |
| 13                  | updated_at            | Date            | Datetime of last update in UTC format                        |
| 14                  | created_at            | Date            | Datetime of creation in UTC format                           |

#### Indexes

| **index_name** | **index_type**      | **column_name(s)**        | description                                                  |
| -------------- | ------------------- | ------------------------- | ------------------------------------------------------------ |
| ``_id_``       | Default `_id` Index | {<br/>    "_id" : 1<br/>} | More info about [default index](https://docs.mongodb.com/manual/indexes/#default-id-index) |

#### Document example

```javascript
{
    "_id" : ObjectId("5c672189408b1200104fd195"),
    "asset_id" : "9e25d17a-3160-11e9-84b7-0242ac120003",
    "serial_number" : "SN123456",
    "part_number" : "",
    "model_number" : "AP3435646",
    "manufacturer" : "Apple",
    "categories" : [ 
        "phones", 
        "smartphones"
    ],
    "condition" : "A",
    "description" : "",
    "price" : 100.5,
    "currency_code" : "USD",
    "location_country_code" : "US",
    "updated_at" : ISODate("2019-02-15T20:31:05.000Z"),
    "created_at" : ISODate("2019-02-15T20:31:05.000Z")
}
```