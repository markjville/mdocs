# Install MariaDB and Ghost

## 1. Install MariaDB:
`dnf install mariadb-server`

## 2. Make persistent:
`systemctl enable --now mariadb`

## 3. Harden MariaDB database server security:
`mysql_secure_installation`
	
## 4. Verify install:
`mysql -u root -p`
