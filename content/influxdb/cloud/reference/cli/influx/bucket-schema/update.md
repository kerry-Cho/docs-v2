---
title: influx bucket-schema update
description: The `influx bucket-schema update` command updates a measurement schema for an InfluxDB bucket.
menu:
  influxdb_cloud_ref:
    name: influx bucket-schema update
    parent: influx bucket-schema
weight: 201
related:
  - /influxdb/cloud/organizations/bucket-schema
---

The `influx bucket-schema update` command updates the measurement schema of a
bucket in InfluxDB.

`bucket-schema update` requires a bucket with an [`explicit` schema-type](/influxdb/v2.0/reference/cli/influx/bucket/create/#create-a-bucket-with-custom-bucket-schema)
and an existing measurement schema.

## Usage

```sh
influx bucket-schema update [flags]
```

##### Supported operations
- Adding new columns to a schema

##### Unsupported operations
- Modify existing columns in a schema
- Delete columns from a schema

## Flags

| Flag |                     | Description                                                           | Input type | {{< cli/mapped >}}    |
| :--- | :------------------ | :-------------------------------------------------------------------- | :--------: | :-------------------- |
| `-c` | `--active-config`   | CLI configuration to use for command                                  |   string   |                       |
| `-n` | `--bucket`          | Bucket name (mutually exclusive with `--bucket-id`)                   |   string   |                       |
| `-i` | `--bucket-id`       | Bucket ID (mutually exclusive with `--bucket`)                        |   string   |                       |
|      | `--columns-file`    | Path to column definitions file. For more information, see [Create a columns file](/influxdb/cloud/reference/cli/influx/bucket-schema/create/#create-a-columns-file).                                                        |   string   |                       |
|      | `--columns-format`  | Columns file format (`csv`, `ndjson`, `json`, default: `auto`)        |   string   |                       |
|      | `--configs-path`    | Path to `influx` CLI configurations (default `~/.influxdbv2/configs`) |   string   | `INFLUX_CONFIGS_PATH` |
| `-x` | `--extended-output` | Print column information for each measurement schema (default: false)        |            |                       |
| `-h` | `--help`            | Help for the `create` command                                         |            |                       |
|      | `--hide-headers`    | Hide table headers (default `false`)                                  |            | `INFLUX_HIDE_HEADERS` |
|      | `--host`            | HTTP address of InfluxDB (default `http://localhost:8086`)            |   string   | `INFLUX_HOST`         |
|      | `--json`            | Output data as JSON (default `false`)                                 |            | `INFLUX_OUTPUT_JSON`  |
| `-n` | `--name`            | Measurement name                                                      |   string   |                       |
| `-o` | `--org`             | Organization name (mutually exclusive with `--org-id`)                |   string   | `INFLUX_ORG`          |
|      | `--org-id`          | Organization ID (mutually exclusive with `--org`)                     |   string   | `INFLUX_ORG_ID`       |
|      | `--skip-verify`     | Skip TLS certificate verification                                     |            |                       |
| `-t` | `--token`           | Authentication token                                                  |   string   | `INFLUX_TOKEN`        |

## Examples

{{< cli/influx-creds-note >}}

- [Update a schema using the influx CLI](#update-a-schema-using-the-influx-cli)
- [Update a schema and print column information](#update-a-schema-and-print-column-information)
- [Update a schema, specifying the columns format](#update-a-schema-specifying-the-columns-format)

## Update a schema using the influx CLI

```sh
influx bucket-schema update \
  --bucket example-bucket \
  --name temperature \
  --columns-file columns.csv
```

## Update a schema and print column information
```sh
influx bucket-schema update \
  --bucket example-bucket \
  --name cpu \
  --columns-file columns.csv \
  -extended-output
```

## Update a schema, specifying the columns format
```sh
influx bucket-schema update \
  --bucket example-bucket \
  --name cpu \
  --columns-file columns.json \
  --columns-format ndjson
```