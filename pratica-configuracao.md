## SQL 4 - PRATICA CONFIGURACAO DB

---

### Exercício 1

**1) Crie um novo usuário MySQL com a seguinte configuração**

- Nome de usuário:  ml_app_user1  
- Servidor:  localhost     
- Password:  ml_app_user1     
- Base de dados para o usuário:  ml_app_consultorio    
- Charset/collation:  utf8_spanish_ci    
- Sem privilégios globais       

CREATE database ml_app_consultorio CHARACTER SET utf8 COLLATE utf8_spanish_ci;

CREATE USER 'ml_app_user1'@'localhost' IDENTIFIED BY 'ml_app_user1';

GRANT ALL PRIVILEGES ON ml_app_consultorio.* To 'ml_app_user1'@'localhost';

**2) Depois que o usuário for criado, faça login como um usuário ml_app_user1 e verifique se o banco de dados foi criado ml_app_consultorio.**

mysql> show databases;    
+--------------------+    
|   Database         |    
+--------------------+    
| information_schema |    
| ml_app_consultorio |    
+--------------------+    

**3) Como usuário ml_app_user1, verifique se você não pode excluir o banco de dados, nem criar outro banco de dados (por exemplo, o banco de dados ml_app_1_bd1).**

mysql> drop database ml_app_consultorio;
Query OK, 0 rows affected (0.01 sec)

mysql> create database ml_app_1_bd1;
ERROR 1044 (42000): Access denied for user 'ml_app_user1'@'localhost' to database 'ml_app_1_bd1'



---

### Exercício 2

**1) Crie um novo usuário MySQL com a seguinte configuração**

- Nome de usuário:  ml_app_user2  
- Servidor:  localhost     
- Password:  ml_app_user2     
- Base de dados para o usuário:  ml_app_consultorio 
- Com todos os privilégios       

mysql> CREATE database ml_app_consultorio;
Query OK, 1 row affected (0.00 sec)

mysql> CREATE USER 'ml_app_user2'@'localhost' IDENTIFIED BY 'ml_app_user2';
Query OK, 0 rows affected (0.01 sec)

mysql> GRANT ALL PRIVILEGES ON ml_app_consultorio.* To 'ml_app_user2'@'localhost';
Query OK, 0 rows affected, 1 warning (0.00 sec)

**2) Depois que o usuário for criado, faça login como um usuário ml_app_user2 e verifique se você tem todos os privilégios do banco de dados ml_app_consultorio.**

mysql> show grants for 'ml_app_user2'@'localhost';

| GRANT APPLICATION_PASSWORD_ADMIN,AUDIT_ADMIN,BACKUP_ADMIN,BINLOG_ADMIN,BINLOG_ENCRYPTION_ADMIN,CLONE_ADMIN,CONNECTION_ADMIN,ENCRYPTION_KEY_ADMIN,FLUSH_OPTIMIZER_COSTS,FLUSH_STATUS,FLUSH_TABLES,FLUSH_USER_RESOURCES,GROUP_REPLICATION_ADMIN,INNODB_REDO_LOG_ARCHIVE,INNODB_REDO_LOG_ENABLE,PERSIST_RO_VARIABLES_ADMIN,REPLICATION_APPLIER,REPLICATION_SLAVE_ADMIN,RESOURCE_GROUP_ADMIN,RESOURCE_GROUP_USER,ROLE_ADMIN,SERVICE_CONNECTION_ADMIN,SESSION_VARIABLES_ADMIN,SET_USER_ID,SHOW_ROUTINE,SYSTEM_USER,SYSTEM_VARIABLES_ADMIN,TABLE_ENCRYPTION_ADMIN,XA_RECOVER_ADMIN ON *.* TO `ml_app_user2`@`localhost` |
| GRANT ALL PRIVILEGES ON `ml_app_consultorio`.* TO `ml_app_user2`@`localhost`  

**3) Como usuario ml_app_user2, verifique se você tem todos os privilégios.**


mysql> show grants for 'ml_app_user2'@'localhost';
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Grants for ml_app_user2@localhost                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, RELOAD, SHUTDOWN, PROCESS, FILE, REFERENCES, INDEX, ALTER, SHOW DATABASES, SUPER, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, REPLICATION SLAVE, REPLICATION CLIENT, CREATE VIEW, SHOW VIEW, CREATE ROUTINE, ALTER ROUTINE, CREATE USER, EVENT, TRIGGER, CREATE TABLESPACE, CREATE ROLE, DROP ROLE ON *.* TO `ml_app_user2`@`localhost`
|
| GRANT APPLICATION_PASSWORD_ADMIN,AUDIT_ADMIN,BACKUP_ADMIN,BINLOG_ADMIN,BINLOG_ENCRYPTION_ADMIN,CLONE_ADMIN,CONNECTION_ADMIN,ENCRYPTION_KEY_ADMIN,FLUSH_OPTIMIZER_COSTS,FLUSH_STATUS,FLUSH_TABLES,FLUSH_USER_RESOURCES,GROUP_REPLICATION_ADMIN,INNODB_REDO_LOG_ARCHIVE,INNODB_REDO_LOG_ENABLE,PERSIST_RO_VARIABLES_ADMIN,REPLICATION_APPLIER,REPLICATION_SLAVE_ADMIN,RESOURCE_GROUP_ADMIN,RESOURCE_GROUP_USER,ROLE_ADMIN,SERVICE_CONNECTION_ADMIN,SESSION_VARIABLES_ADMIN,SET_USER_ID,SHOW_ROUTINE,SYSTEM_USER,SYSTEM_VARIABLES_ADMIN,TABLE_ENCRYPTION_ADMIN,XA_RECOVER_ADMIN ON *.* TO `ml_app_user2`@`localhost` |
| GRANT ALL PRIVILEGES ON `ml_app_consultorio`.* TO `ml_app_user2`@`localhost`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
3 rows in set (0.00 sec)

### Exercício 3

**1) Crie um novo usuário MySQL com a seguinte configuração**

- Nome de usuário:  ml_app_user3  
- Servidor:  localhost     
- Password:  ml_app_user3     
- Base de dados para o usuário:  ml_app_consultorio 
- Com privilégios SELECT**       

mysql> CREATE USER 'ml_app_user3'@'localhost' IDENTIFIED BY 'ml_app_user3';
Query OK, 0 rows affected (0.01 sec)

mysql> GRANT SELECT ON ml_app_consultorio.* To 'ml_app_user3'@'localhost';
Query OK, 0 rows affected, 1 warning (0.00 sec)

**2) Depois que o usuário for criado, faça login como um usuário ml_app_user3 e verifique se você tem privilégios de seleção para o banco de dados ml_app_consultorio.**
 
mysql> show grants for 'ml_app_user3'@'localhost';
+----------------------------------------------------------------------+
| Grants for ml_app_user3@localhost                                    |
+----------------------------------------------------------------------+
| GRANT USAGE ON *.* TO `ml_app_user3`@`localhost`                     |
| GRANT SELECT ON `ml_app_consultorio`.* TO `ml_app_user3`@`localhost` |
+----------------------------------------------------------------------+
2 rows in set (0.00 sec)
