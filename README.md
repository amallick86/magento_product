# magento_product
1. Install any version of magento in your local device.
2. Create a new module to add custom fields(priority(int), vendor_name(varchar)) in product
3. Programmatically show those 2 newly added fields on frontend.

## Setup - Magento v2.4.4 in Local Device
1. install xampp v8.1.12
2. install composer v2
3. download elastic search v7.16.3
4. open xampp server start Apache and Mysql 
5. go to phpadmin pannel and create db on Mysql for magento ex:- db_name: "db_magento2"
6. if you wanna create a user then create it with password for security otherwise go throug username: "root" and passwor:""
7. unzip archived file elastic search at the  to xampp/htdocs =>go to  elasticSearch7.16.3/bin 
select elasticsearch and run as administrator
To ensure if Elasticsearch is running on your system, in your browser type: localhost:9200
8. through xampp server => in Apache click on config and select php.ini
> search for 
;extension=gd
;extension=intl
;extension=soap
;extension=xsl
;extension=sockets
;extension=sodium

> and remove ; from above lines

> Again search for 
max_execution_time=
max_input_time=
memory_limit=

> and edit to 
max_execution_time=18000
max_input_time=1800
memory_limit=4G
>
9. clone this repo to xampp/htdocs/
10.open xampp\apache\conf\extra\httpd-vhosts.conf 
>Add below text to bottom of the file

><VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs/magento2/pub"
    ServerName shopping.magento.com
</VirtualHost>
<VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs"
    ServerName localhost
</VirtualHost>
11. open C:\Windows\System32\drivers\etc\hosts and add 
>127.0.0.1  shopping.magento.com
11. restart xampp server and start Apache and Mysql
12. open terminal on xampp/htdocs/magento2>

php bin/magento setup:install --base-url="http://shopping.magento.com/" --db-host="localhost" --db-name="db_magento2" --db-user="root" --db-password="" --admin-firstname="admin" --admin-lastname="admin" --admin-email="user@example.com" --admin-user="admin" --admin-password="Admin@123456" --language="en_US" --currency="USD" --timezone="America/Chicago" --use-rewrites="1" --backend-frontname="admin" --search-engine=elasticsearch7 --elasticsearch-host="localhost" --elasticsearch-port=9200

Replace these values:

–base-url: http://shopping.magento.com/
–db-name: your database name 
–db-password: your database password 