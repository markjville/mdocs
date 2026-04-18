#MySQL commands

##Connect to DB:

`mysql -u root -p`

##To show databases:

`show databases;`

##To backup a database:

`mysqldump -u root -p database_name > file.sql`

##To restore database:

`mysql -u username -p database_name < file.sql`
