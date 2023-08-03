# Ansible Role: postgres

Install & create PostgreSQL database on Debian GNU/Linux.

## Requirements
The role is designed for [Debian GNU/Linux](https://debian.org).

## Role Variables

```
postgres:
  username: user-to-create
  password: your-strong-password
  database: database-to-create
# optional
  repository: debian|official
  version: 11
```

Setting `postgres.repository` == `offical` means that [offical repository of PostreSQL](https://www.postgresql.org/download/linux/debian/) project is being used, remove it or set to `debian` to use Debians version of the package.

When `postgres.version` is not present, then default version for respective Debian distribution is installed. When `postgres.version` is not available, the role will fail.

THe Role is chechcing for other versions of the PostreSQL installed on the target system and if finds a different version, then fails. If you want to get rid of this feature and install another version, use `--skip-tags postgres_check4other`.

## Example Playbook
```
- hosts: localhost
  connection: local

  roles:
    - role: postgres
```
