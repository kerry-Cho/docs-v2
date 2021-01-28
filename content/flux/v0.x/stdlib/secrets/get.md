---
title: secrets.get() function
description: >
  The `secrets.get()` function retrieves a secret from the InfluxDB secret store.
aliases:
  - /influxdb/v2.0/reference/flux/functions/secrets/get/
  - /influxdb/v2.0/reference/flux/stdlib/secrets/get/
  - /influxdb/cloud/reference/flux/stdlib/secrets/get/
menu:
  flux_0_x_ref:
    name: secrets.get
    parent: InfluxDB Secrets
weight: 202
introduced: 0.41.0
---

The `secrets.get()` function retrieves a secret from the
[InfluxDB secret store](/influxdb/v2.0/security/secrets/).

_**Function type:** Miscellaneous_

```js
import "influxdata/influxdb/secrets"

secrets.get(key: "KEY_NAME")
```

## Parameters

### key
The secret key to retrieve.

_**Data type:** String_

## Examples

### Populate sensitive credentials with secrets
```js
import "sql"
import "influxdata/influxdb/secrets"

username = secrets.get(key: "POSTGRES_USERNAME")
password = secrets.get(key: "POSTGRES_PASSWORD")

sql.from(
  driverName: "postgres",
  dataSourceName: "postgresql://${username}:${password}@localhost",
  query:"SELECT * FROM example-table"
)
```