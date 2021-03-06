## Output plugin : Clickhouse

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/waterdrop
* Version: 1.1.0

### Description

Write Rows to ClickHouse via [Clickhouse-jdbc](https://github.com/yandex/clickhouse-jdbc). You need to create the corresponding table in advance.


### Options

| name | type | required | default value |
| --- | --- | --- | --- |
| [bulk_size](#bulk_size-number) | number| no |20000|
| [database](#database-string) | string |yes|-|
| [fields](#fields-list) | list | yes |-|
| [host](#host-string) | string | yes |-|
| [password](#password-string) | string | no |-|
| [table](#table-string) | string | yes |-|
| [username](#username-string) | string | no |-|

#### bulk_size [number]

The number of Rows written to ClickHouse through [ClickHouse JDBC](https://github.com/yandex/clickhouse-jdbc). Default is 20000.

##### database [string]

ClickHouse database.

##### fields [list]

Field list which need to be written to ClickHouse。

##### host [string]

ClickHouse hosts, format as `hostname:port`

##### password [string]

ClickHouse password, only used when ClickHouse has authority authentication.

##### table [string]

ClickHouse table name.

##### username [string]

ClickHouse username, only used when ClickHouse has authority authentication.

### Note

Before the data is written to ClickHouse, all fields need to be converted to the type corresponding to the table structure in ClickHouse.

It should be noted that the corresponding field of the **Date** needs to be converted to String with format of `yyyy-MM-dd` and the corresponding field of the **DateTime** needs to be converted to String with format of `yyyy-MM-dd HH:mm:ss`.

### Examples

```
clickhouse {
    host = "localhost:8123"
    database = "nginx"
    table = "access_msg"
    fields = ["date", "datetime", "hostname", "http_code", "data_size", "ua", "request_time"]
    username = "username"
    password = "password"
    bulk_size = 20000
}
```

