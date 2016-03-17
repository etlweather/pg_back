`pg_back`
=================================================

`pg_back` is a simple backup script for PostgreSQL.

## Features

`pg_back` uses `pg_dumpall` to dump roles and tablespaces, and `pg_dump` 
to dump each selected database to a separate file. The custom format of 
`pg_dump` is used by default.

A configuration file, by default `/etc/postgresql/pg_back.conf`, can
hold the configuration to automate the backup. All options can be
overridden on the command line.

Databases to dump can be specified in the configuration file or on the
command line.  A list fo databases can also be excluded. Database
templates can be included, with the exception of template0, because
connection to it are forbidden by default.

The purpose of the script is to allow unattended backups, thus a purge
time can be configured to avoid running out of disk space in the
backup directory. It is set to 30 days by default.

## Usage

It is best to run it as the postgres user. For example :

```
pg_back -b /var/lib/pgsql/9.3/backups
```

See the help with `pg_back -?`.


## Credits

This project was originally made by [Nicolas Thauvin](https://github.com/orgrim).
The original source code is available on github: https://github.com/orgrim/pg_back
under a classic 2 clauses BSD license. See license block in the script.

This version extends the original script with additional features.
