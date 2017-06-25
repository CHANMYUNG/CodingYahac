# 0619(~PHP실습)

## HTTP 메소드 파라미터 가져오는 방법!

HTTP 메소드 방식 중 하나인 GET 방식 파라미터를 받아오는 방법  
  
$_GET['파라미터 이름']  
  
**1.php**  
```php

<?php
echo $_GET['name'].",".$_GET['id']
?>
```

**접근 : http://localhost:8001/yahac/0619/1.php?id=132&name=Mr_yun**  



## 파일 읽어들이기

GET 메소드 인자로 넘어온 name 파라미터와 동일한 이름의 텍스트파일 읽어오는 방법  
  
file_get_contents($_GET['id'].".txt");  
  
**2.php**  
```html
<html>
  <head>
    <title></title>
  </head>
  <body>
    <?php
      echo file_get_contents($_GET['id'].".txt");
    ?>
  </body>
</html>
```