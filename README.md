# My workspace (2016.07)

## Installed

### languages

- Ruby
- Node.js
- Python(2&3)
- Erlang
- Elixir
<!-- - Golang -->
- PHP
- Haskell

### Databases

- SQLite
- PostgreSQL
- MariaDB
- Redis
- MongoDB

## How to use
### add client hosts

```conf
10.10.10.10 php.workspace
```

### create & run vm

```bash
# ansible automatic run
$ vagrant up
```

### ...and sync work directory start

```bash
# run on other terminal window
$ vagrant rsync-auto
```

### access to workspace

```bash
$ vagrant ssh
```

#### access to db some tools

- PostgreSQL: 10.10.10.10:5432
- Redis: 10.10.10.10:6379
- MongoDB: 10.10.10.10:27017
- Memcached: 10.10.10.10:11211

## My guide

- [docker-composeを使って最高の開発環境を手に入れた](http://blog.muuny-blue.info/7d128c1d4a33165a8676d1650d8ff828.html)
- [Dockerを使って開発環境を構築する](https://moneyforward.com/engineers_blog/2015/07/09/docker/)
