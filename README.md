# MarioDB-on-Synology

ssh wwszol@192.168.0.179
wwszol@192.168.0.179's password: 

Synology strongly advises you not to run commands as the root user, who has
the highest privileges on the system. Doing so may cause major damages
to the system. Please note that if you choose to proceed, all consequences are
at your own risk.

wwszol@UloziskoNAS:~$ mysql -u root -p
Enter password: 
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 43
Server version: 10.3.32-MariaDB Source distribution

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| testDev            |
+--------------------+
4 rows in set (0.003 sec)

MariaDB [(none)]> use mysql;
Database changed
MariaDB [mysql]> show tables;
+---------------------------+
| Tables_in_mysql           |
+---------------------------+
| column_stats              |
| columns_priv              |
| db                        |
| event                     |
| func                      |
| general_log               |
| gtid_slave_pos            |
| help_category             |
| help_keyword              |
| help_relation             |
| help_topic                |
| host                      |
| index_stats               |
| innodb_index_stats        |
| innodb_table_stats        |
| plugin                    |
| proc                      |
| procs_priv                |
| proxies_priv              |
| roles_mapping             |
| servers                   |
| slow_log                  |
| table_stats               |
| tables_priv               |
| time_zone                 |
| time_zone_leap_second     |
| time_zone_name            |
| time_zone_transition      |
| time_zone_transition_type |
| transaction_registry      |
| user                      |
+---------------------------+
31 rows in set (0.001 sec)

MariaDB [mysql]> select user,host from user;
+--------+-------------+
| user   | host        |
+--------+-------------+
| root   | 127.0.0.1   |
| wwszol | 192.168.0.% |
| root   | ::1         |
| root   | localhost   |
+--------+-------------+
4 rows in set (0.001 sec)

//------- AT this point you need to add user with address / range you want to grant access with ------//

MariaDB [mysql]> create user 'githubuser'@'192.168.21.%' identified by 'GIThubdummy0/';
Query OK, 0 rows affected (0.075 sec)

MariaDB [mysql]> select user,host from user;
+------------+--------------+
| user       | host         |
+------------+--------------+
| root       | 127.0.0.1    |
| wwszol     | 192.168.0.%  |
| githubuser | 192.168.21.% |
| root       | ::1          |
| root       | localhost    |
+------------+--------------+
5 rows in set (0.001 sec)

finito
