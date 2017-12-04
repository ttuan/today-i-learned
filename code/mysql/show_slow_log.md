# Detect slow log in mysql

Mysql provides a way to detect slow log. You can config it in folder:
`/etc/mysql/mysql.conf.d/mysqld.cnf`.

```
slow_query_log		= 1
slow_query_log_file	= /var/log/mysql/mysql-slow.log
long_query_time = 2
log-queries-not-using-indexes
```

btw, we have some gem in Rails, which can help you detect slow queries too, such
as `rack-mini-profiler`, `bullet`, ...
