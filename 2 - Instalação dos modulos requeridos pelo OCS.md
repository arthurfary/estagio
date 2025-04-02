# Instalação do modulos requeridos pelo OCS

Com o Ubuntu Server rodando, vamos realizar a instalação do OCS Inventory.

De antemão vamos realizar a atualização e upgrade do sistema:

```shell
$ sudo apt-get update && sudo apt-get upgrade
```

Com o sistema atualizado, vamos iniciar os preparativos para o download do OCS.

O OCS tem 4 requerimentos:

1. Apache 2.2^
2. PHP 7^
3. PERL 5.6^
4. MariaDB 10.3^ (ou MySQL 8^)

Realizando a instalação:

```shell
$ sudo apt-get install apache2 php perl mariadb-server mariadb-common mariadb-client
```

Ao fazer a instalação, o MariaDB vem sem nenhum configuração de segurança. Para remediar isto basta rodar o script (e seguir os prompts em tela):

```shell
$ sudo mysql_secure_installation
```

Ativar mariadb:
```shell
$ sudo systemctl enable mariadb
$ sudo systemctl start mariadb
```

Configurar mariadb:

- Abra o mariadb com o comando:
```shell
$ sudo mysql -u root
```

- Coloque uma senha para o root (substitua 'SUASENHA'):
```sql
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('SUASENHA')
```

- Crie a banco de dados e configure o usuário:
```sql
CREATE DATABASE ocsweb;
CREATE USER 'ocs'@'localhost' IDENTIFIED BY 'ocs';
GRANT ALL PRIVILEGES ON ocsweb.* TO 'ocs'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

## Instalando pacotes requeridos pelos modulos

No [guia de instalação do OCS](https://wiki.ocsinventory-ng.org/03.Basic-documentation/Setting-up-a-OCS-Inventory-Server/#setting-up-ocs-inventory-server), eles indicam o uso deste comando para baixar os modulos necessários:

### Modulos requeriods pelo "Communications Server"

```shell
$ sudo apt apt install libxml-simple-perl libdbi-perl libdbd-mysql-perl libapache-dbi-perl libnet-ip-perl libsoap-lite-perl libarchive-zip-perl make build-essential

$ sudo cpan install XML::Entities Mojolicious::Lite Switch
```
### Modulos requeriods pelo "Administration console"

```shell
$ apt install php-pclzip make build-essential libdbd-mysql-perl libnet-ip-perl libxml-simple-perl php php-mbstring php-soap php-mysql php-curl php-xml php-zip php-gd
```


