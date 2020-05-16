Different approaches to get file extentions by PHP

```php
http://cowburn.info/2008/01/13/get-file-extension-comparison/
$filename = 'mypic.gif';
```

1. The "explode/end" approach
```php
$ext = end(explode('.', $filename));
```

2. The "strrchr" approach
```php
$ext = substr(strrchr($filename, '.'), 1);
```

3. The "strrpos" approach
```php
$ext = substr($filename, strrpos($filename, '.') + 1);
```

4. The "preg_replace" approach
```php
$ext = preg_replace('/^.*\.([^.]+)$/D', '$1', $filename);
```

5. The “pathinfo” approach
```php
$filename = 'mypic.gif';
$ext = pathinfo($filename, PATHINFO_EXTENSION);
```
