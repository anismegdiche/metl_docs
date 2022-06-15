# config.yml file reference

## Reference and guidelines
`config.yml` is the Metl configuration file, a YAML file to configure sources,schemas,plans...These topic describes version 1 of the config.yml file format.


## **config.yml file structure and example**

A `config.yml` looks like this:
//TODO: change to postgres provider
```
version: '1.0'
sources:
  provider1:
    driver: mssql
    host: localhost
    port: 1433
    user: sa
    password: Azerty123!
    database: SampleDB
schemas:
  schema1:
    source: provider1
```

-----

## `version`
Defines the version used for the configuration. At this stage, only version `1.0` is allowed:

**Example:** 
```
version '1.0'
```
---
## `users`

//TODO: Not implemented/documented

---
## `sources`

A source definition contains configuration that is applied to each data source end-point connection, much like connection string as used in development.

This section contains a list of all configuration options supported by a source definition.

### driver

`driver` is used to define the database provider.

Example:
If we want to declare a source named `db1` using MS SQL Server provider, we write:

```
sources:
  postgresql-db1:
    driver: postgres
```

The table below describes the different values that can be configured in `driver` :

| Value | Provider | Supported versions |
|-|-|-|
| `mssql` | Microsoft SQL Server | |
| `postgres` | PostgresSQL | |
| `mongodb` | MongoDB | |

Each driver has it's own parameters as described below:

#### Microsoft SQL Server driver

`mssql` is used to specify a connection to a database hosted with Microsoft SQL Server:

**Example:**
```
sources:
  ms-sql-db1:
    driver: mssql
    host: 192.168.1.123
    port: 1433
    user: sa
    password: Azerty123!
    database: SampleDB
```

| Parameter | Usage | Example |
|-|-|-|
| `host` | Server to connect to. You can use 'localhost\instance' to connect to named instance | `host: 192.168.1.123` |
| `port` | Server port | `port: 1433` |
| `user` | SQL user | `user: sa` |
| `password` | SQL user password | `password: Azerty123!` |
| `database` | Database to connect to | `database: SampleDB` |
| `options` | Options passed to TDS Driver. See:  |  |



#### PostgreSQL driver

`postgres` is used to specify a connection to a database hosted with a PostgreSQL Server:

**Example:**
```
sources:
  postgresql-db1:
    driver: postgres
    host: 192.168.1.113
    port: 5433
    user: root
    password: Azerty123!
    database: sampledb
```

| Parameter | Usage | Example |
|-|-|-|
| `host` | Server host | `host: 192.168.1.113` |
| `port` | Server port | `port: 5433` |
| `user` | SQL user | `user: root` |
| `password` | SQL user password | `password: Azerty123!` |
| `database` | Database to connect to | `database: sampledb` |

#### `MongoDB` driver

`mongodb` is used to specify a connection to a database hosted with a MongoDB Server:

**Example:**
```
sources:
  db2:
    driver: postgres
    host: 192.168.1.113
    port: 5433
    user: root
    password: Azerty123!
    database: sampledb
```

| Parameter | Usage | Example |
|-|-|-|
| `host` | Server host | `host: 192.168.1.113` |
| `port` | Server port | `port: 5433` |
| `user` | SQL user | `user: root` |
| `password` | SQL user password | `password: Azerty123!` |
| `database` | Database to connect to | `database: sampledb` |

---
## `schemas`

This section is used to declare virtual schemas.

Virtual schemas are the main access point, in other meaning if you want to allow access to a database or a combination of databases, you must declare here your schemas to expose them to the API.

> :fa-info-circle: **Note**:
If there's no `schemas` delaration in `config.yml` Metl will not expose anything to the APIs 

**Example:**
```
schemas:
  sql:
    source: mssql
```

### `source`
### `tables`
### `plan`


---
## `plans`

Example:
```
  plan1:
    plan: etl1

```
