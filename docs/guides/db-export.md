---
metaTitle: Exporting SQL Databases | Lando
description: Learn how to export your MySQL, MariaDB or Postgres databases from Lando.
---

# SQL Export

<GuideHeader />

Lando ships with a helper `db-export` script that is available in all our `LAMP` and `LEMP` based recipes. Used in the recipe context it should export a database dump `DATABASE.TIMESTAMP.gz` into the `/app` directory.

You can also export databases from other services.

## Usage

At the command line execute:

```bash
lando db-export
```

### Examples

```bash
# Export to a file named `DATABASE.TIMESTAMP.gz`
lando db-export

# Export to a file called dump.sql.gz
lando db-export dump.sql

# Export from a secondary database
lando db-export --host db2

# Dump the result to stdout
lando db-export --stdout
```

### Options

```bash
Options:
  --host, -h      The database service to use                  [default: "database"]
  --stdout        Dump database to stdout
```

## Adding the `db-export` command

If you are not using one of our LAMPy [recipes](./../config/recipes.md) you can add the `db-export` command and default options to the ['tooling'](./../config/tooling.md) section of your [Landofile](./../config/lando.md).

```yaml
tooling:
  'db-export [file]':
    service: :host
    description: Exports database from a database service to a file
    cmd: /helpers/sql-export.sh
    user: root
    options:
      host:
        description: The database service to use
        default: database
        alias:
          - h
      stdout:
        description: Dump database to stdout
```

<GuideFooter repo="https://github.com/lando/lando/tree/master/examples/sql-export" />
<Newsletter />
