# 0627 (~라이브러리 1)

## 라이브러리?
중복되는/자주 사용되는 코드를 하나의 파일로 분리해 불러서 사용하는 것  
Node.js의 require, Java의 import 등이 예시  


## php - require

require('경로')를 통해 다른 파일을 불러들여 사용할 수 있음  

**db.php**  

```php
<?php
function db_init($host, $duser, $dpw, $dname){
  $conn = mysqli_connect($host, $duser, $dpw);
  mysqli_select_db($conn, $dname);
  return $conn;
}
?>
```
  
**config.php**  

```php
<?php
$config = array(
  "host"=>"localhost",
  "duser"=>"root",
  "dpw"=>"111111",
  "dname"=>"opentutorials"
);
?>
```
  
**index.php**  

```php
<?php
require("config/config.php");
require("lib/db.php");
$conn = db_init($config["host"], $config["duser"], $config["dpw"], $config["dname"]);
$result = mysqli_query($conn, "SELECT * FROM topic");
?>
<!DOCTYPE html>
<html>
<head>
     <meta charset="utf-8">
  <link rel="stylesheet" type="text/css" href="http://localhost/style.css">
</head>
<body id="target">
    <header>
    <img src="https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/course/94.png" alt="생활코딩">
        <h1><a href="http://localhost/index.php">JavaScript</a></h1>
  </header>
    <nav>
        <ol>
    <?php
    while( $row = mysqli_fetch_assoc($result)){
      echo '<li><a href="http://localhost/index.php?id='.$row['id'].'">'.htmlspecialchars($row['title']).'</a></li>'."\n";
    }
    ?>
        </ ol>
    </nav>
  <div id="control">
    <input type="button" value="white" onclick="document.getElementById('target').className='white'"/>
    <input type="button" value="black" onclick="document.getElementById('target').className='black'" />
    <a href="http://localhost/write.php">쓰기</a>
  </div>
  <article>
  <?php
  if(empty($_GET['id']) === false ) {
      $sql = "SELECT topic.id,title,name,description FROM topic LEFT JOIN user ON topic.author = user.id WHERE topic.id=".$_GET['id'];
      $result = mysqli_query($conn, $sql);
      $row = mysqli_fetch_assoc($result);
      echo '<h2>'.htmlspecialchars($row['title']).'</h2>';
      echo '<p>'.htmlspecialchars($row['name']).'</p>';
      echo strip_tags($row['description'], '<a><h1><h2><h3><h4><h5><ul><ol><li>');
  }
  ?>
  </article>
</body>
</html>
```

이렇게 사용하면 require부분에 해당 파일의 내용이 들어가는듯한 효과가 생김  

이런 식으로  
```php
<?php
// config.php의 내용
$config = array(
  "host"=>"localhost",
  "duser"=>"root",
  "dpw"=>"111111",
  "dname"=>"opentutorials"
);

// db.php의 내용
function db_init($host, $duser, $dpw, $dname){
  $conn = mysqli_connect($host, $duser, $dpw);
  mysqli_select_db($conn, $dname);
  return $conn;
}

$conn = db_init($config["host"], $config["duser"], $config["dpw"], $config["dname"]);
$result = mysqli_query($conn, "SELECT * FROM topic");
?>
<!DOCTYPE html>
<html>
<head>
     <meta charset="utf-8">
  <link rel="stylesheet" type="text/css" href="http://localhost/style.css">
</head>
<body id="target">
    <header>
    <img src="https://s3.ap-northeast-2.amazonaws.com/opentutorials-user-file/course/94.png" alt="생활코딩">
        <h1><a href="http://localhost/index.php">JavaScript</a></h1>
  </header>
    <nav>
        <ol>
    <?php
    while( $row = mysqli_fetch_assoc($result)){
      echo '<li><a href="http://localhost/index.php?id='.$row['id'].'">'.htmlspecialchars($row['title']).'</a></li>'."\n";
    }
    ?>
        </ ol>
    </nav>
  <div id="control">
    <input type="button" value="white" onclick="document.getElementById('target').className='white'"/>
    <input type="button" value="black" onclick="document.getElementById('target').className='black'" />
    <a href="http://localhost/write.php">쓰기</a>
  </div>
  <article>
  <?php
  if(empty($_GET['id']) === false ) {
      $sql = "SELECT topic.id,title,name,description FROM topic LEFT JOIN user ON topic.author = user.id WHERE topic.id=".$_GET['id'];
      $result = mysqli_query($conn, $sql);
      $row = mysqli_fetch_assoc($result);
      echo '<h2>'.htmlspecialchars($row['title']).'</h2>';
      echo '<p>'.htmlspecialchars($row['name']).'</p>';
      echo strip_tags($row['description'], '<a><h1><h2><h3><h4><h5><ul><ol><li>');
  }
  ?>
  </article>
</body>
</html>
```

