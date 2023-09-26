## Steps
1. Run Docker compose command to build and run applications in containers

## Install Magento2 
## Once containers are in running mode, run below commands to get apache container shell install Magento
2. docker exec -it <containerId> /bin/bash
2. su - magento
3. php /var/www/html/bin/magento setup:install --base-url=http://www.devopsrealtime.com --db-host=mysql --db-name=magentodb --db-user=magentoadmin --db-password=magentopassword --admin-firstname=magento --admin-lastname=magento --admin-email=dptrealtime@gmail.com --admin-user=magento --admin-password=Hello$$Pass@2d --language=en_GB --currency=GBP --timezone=Europe/London --use-rewrites=1 --backend-frontname=admin --elasticsearch-host=elasticsearch --elasticsearch-port=9200

## Help
visit https://www.devopsrealtime.com for more details