# Mysql User Management Basics
## Working with Mysql shell
- \sql : to activate sql
- \connect root@localhost : to connect to the server with user root and host as localhost

## User Management
### View existing Users with host
syntax : select user, host from mysql.user; 
### Create New User
syntax: create user 'username'@'host' identified by 'password';
### View grants / privileges
syntax: show grants for username@host ;
### Grant Privileges
syntax : grant privilege_name on dbname.tablename to username@host;

examples :
- Grant select privilege :
  - grant select on *.* to user@host; // all databases and all tables
  - grant select on db.tb to user2host; // database db having table tb
- Grant update on single column :
  - grant update (col) on db.tb to user@host;

### Revoke Privileges
syntax : revoke privilege_name on dbname.tablename from user@host; <br>
privilege must be first granted only then it could be revoked <br> 
Only those granted privileges can be revoked. 

view currently running users <br> 
select id, users from information_schema.processlist;

to disconnect a existing user connection from root account <br>
kill \<id\>; //id given in the previos table i.e processlist <br>

### Different types of

- 'username'@'localhost'
  - 'pooja'@'localhost' : pooja can only access it through localhost
- 'username'@'192.25.1.2'
  - 'pooja'@'192.25.1.2' : pooja can only access through server 192.25.1.2
- 'username'
  - 'pooja' : username without specifying host will enable it to access from anywhere
