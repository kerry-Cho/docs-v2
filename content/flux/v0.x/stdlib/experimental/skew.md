---
title: experimental.skew() function
description: >
  The `experimental.skew()` function outputs the skew of non-null values in the
  `_value` column for each input table.
menu:
  flux_0_x_ref:
    name: experimental.skew
    parent: experimental
weight: 302
aliases:
  - /influxdb/v2.0/reference/flux/stdlib/experimental/skew/
  - /influxdb/cloud/reference/flux/stdlib/experimental/skew/
related:
  - /flux/v0.x/stdlib/universe/skew/
flux/v0.x/tags: [transformations, aggregates]
introduced: 0.107.0
---

The `experimental.skew()` function outputs the skew of non-null values in the
`_value` column for each input table as a float.

```js
import "experimental"

experimental.skew()
```

## Examples
```js
import "experimental"

from(bucket: "example-bucket")
  |> range(start: -5m)
  |> filter(fn: (r) =>
    r._measurement == "example-measurement" and
    r._field == "example-field"
  )
  |> experimental.skew()
```