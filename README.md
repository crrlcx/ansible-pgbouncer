# About

Ansible role `ansible-pgbouncer` installs **[PGBouncer](https://www.pgbouncer.org/)** from PostgreSQL [apt repository](http://apt.postgresql.org).

PGBouncer is Lightweight connection pooler for PostgreSQL.

## Requirements

- postgresql
- systemd

## Role variables

### Defaults

```yaml
# Package name and version
pgbouncer_package: pgbouncer
pgbouncer_version: latest

# Files and process owner
pgbouncer_user: postgres
pgbouncer_group: postgres

# Systemd service configuration
pgbouncer_memlock_enabled: false
pgbouncer_max_open_files: 65536
pgbouncer_max_threads: 65536
pgbouncer_service_state: restarted

# Where handle connections
pgbouncer_listen_addr: 127.0.0.1
pgbouncer_listen_port: 6432

# Log place
pgbouncer_log_dir: /var/log/pgbouncer

# Socket and PID files
pgbouncer_unix_socket_dir: /var/run/postgresql

# PostgreSQL connection
pgbouncer_databases:
  - selector: "*"
    host: 127.0.0.1
    port: 5432

# PGBouncer users list
pgbouncer_auth_users:
  - name: postgres
    auth_hash: md5hash
```

### Override

All variables from this groups will be combined with same `_config` groups in `vars/main.yml`.

```yaml
# Administrative settings
pgbouncer_administrative_override: []

# Authentication settings
pgbouncer_authentication_override: []

# Pooler personality questions
pgbouncer_pooler_override: []

# Connection limits
pgbouncer_connection_override: []

# Logging
pgbouncer_logging_override: []

# Timeouts
pgbouncer_timeouts_override: []

# Low-level tuning options
pgbouncer_tuning_override: []

# Random stuff
pgbouncer_random_override: []
```

## Dependencies

-

## Example playbook

```yaml
- hosts: servers
  roles:
    - role: ansible-pgbouncer
```

## License

MIT
