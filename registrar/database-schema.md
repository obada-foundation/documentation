# Registar Database Specification



## General Information

| Database Name | **Database Version** | **Database Engine** | Collections                                                  |
| ------------- | -------------------- | ------------------- | ------------------------------------------------------------ |
| MongoDB       | 3.6                  | Wired Tiger         | * users_collection <br />* settings_collection <br />* migrations |



## users_collection

### Perpose

Contains users registered by registrar.

### Table Schema

#### Columns

| **column_position** | **column_name**   | **column_type** | description                                                  |
| ------------------- | ----------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id               | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |
| 2                   | obada_user_id     | String          | *UUID* (Universally Unique Identifier).<br /> Generated with [ramsey/uuid](https://github.com/ramsey/uuid) library |
| 3                   | name              | String          | The name of registrar user.                                  |
| 4                   | compliance_status | Int32           | At this moment has only two statuses: <br /> * 0 is not compaint<br /> * 1 is compaint |
| 5                   | created_at        | Date            | Datetime of creation in UTC format                           |
| 6                   | updated_at        | Date            | Datetime of last update in UTC format                        |

#### Indexes

| **index_name** | **index_type**      | **column_name(s)**        | description                                                  |
| -------------- | ------------------- | ------------------------- | ------------------------------------------------------------ |
| ``_id_``       | Default `_id` Index | {<br/>    "_id" : 1<br/>} | More info about [default index](https://docs.mongodb.com/manual/indexes/#default-id-index) |

#### Document example

```javascript
{
    "_id" : ObjectId("5c9cde80dac5af001427f923"),
    "obada_user_id" : "6889ad66-5168-11e9-bb7a-0242ac120003",
    "name" : "internal_id-mar28_TEST",
    "compliance_status" : 0,
    "updated_at" : ISODate("2019-03-28T14:47:28.000Z"),
    "created_at" : ISODate("2019-03-28T14:47:28.000Z")
}
```



## settings_collection

### Perpose

Contains settings for registrar setup. For example private and public keys for creating and verifying JWT tokens. For this collection there is no type of schema, the idea is to store any random documents structure required for utility ojectives.

### Schema

| **column_position** | **column_name** | **column_type** | description                                                  |
| ------------------- | --------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id             | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |

#### 

### Document example

```javascript
{
    "_id" : ObjectId("5c3fb8d0d2e01300070ffb42"),
    "private_key" : "-----BEGIN PRIVATE KEY-----\nMIIJ...IpJEau2TgH7ee\nB1NSbKGtlS2Ruyeb3qwPEEqziupbEA==\n-----END PRIVATE KEY-----\n",
    "public_key" : "-----BEGIN PUBLIC KEY-----\nMIICIjANBgkqhkiG9w0BAQE...MCAwEAAQ==\n-----END PUBLIC KEY-----\n",
    "registrar_id" : "9db60b865c6859d6853d0b623c823a26",
    "updated_at" : ISODate("2019-01-16T23:05:52.000Z"),
    "created_at" : ISODate("2019-01-16T23:05:52.000Z")
}
```



## migrations

### Perpose

https://laravel.com/docs/5.8/migrations

### Schema

#### 

| **column_position** | **column_name** | **column_type** | description                                                  |
| ------------------- | --------------- | --------------- | ------------------------------------------------------------ |
| 1                   | _id             | Object          | Internal MongoDB identifier.<br />Read more information [here](https://docs.mongodb.com/manual/reference/method/ObjectId/) . |
| 2                   | migration       | String          |                                                              |
| 3                   | batch           | Int32           |                                                              |

### Document example

```javascript
{
    "_id" : ObjectId("5c98fa50dac5af001f5847a2"),
    "migration" : "2019_03_25_155133_change_compliant_property_to_compliance_status",
    "batch" : 1
}
```









