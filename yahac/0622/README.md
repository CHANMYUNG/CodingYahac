# 0622 (~mysql 실습)

## mysql connection

```php
<?php
$conn = mysqli_connect("localhost", "root", 111111);
?>
```
conn이라는 변수에 mysql connection 객체를 담음


## mysql select db

```php
<?php
mysqli_select_db($conn, "opentutorials");
?>
```

opentutorials라는 db를 선택  
_(mysql에서의 use opentutorials와 비슷함)_  

## mysql select query
```php
<?php
$result = mysqli_query($conn, "SELECT * FROM topic");
?>
```
쿼리문을 실행하고 result라는 변수에 결과 객체를 저장  
_조회된 열이 저장됨(복수일 수도 있음)_  

## mysql row
```php
<?php
$row = mysqli_fetch_assoc($result)
?>
```
row에 조회된 열을 하나 씩 가져옴  
이를 활용할 수 있음  

```php
<?php
while( $row = mysqli_fetch_assoc($result)){
      echo '<li><a href="http://localhost:8001/yahac/0622/index.php?id='.$row['id'].'">'.$row['title'].'</a></li>'."\n";
    }
?>
```

