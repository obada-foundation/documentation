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

| _id                                  | obada_user_id                        | name                   | compliance_status | created_at               | updated_at               |
| ------------------------------------ | ------------------------------------ | ---------------------- | ----------------- | ------------------------ | ------------------------ |
| ObjectId("5c9cde80dac5af001427f923") | 6889ad66-5168-11e9-bb7a-0242ac120003 | internal_id-mar28_TEST | 0                 | 2019-03-28T14:47:28.000Z | 2019-03-28T14:47:28.000Z |



## settings_collection

### Perpose

### Schema

## migrations

### Perpose

### Schema





