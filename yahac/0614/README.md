# 0614(~배열)

## 반복문 (9_Loop.php)
일반적인 프로그래밍 언어와 다르지 않음  

## 배열 

### 배열 (10_Array.php)

#### Javascript

**배열 생성**  

```js
list = new Array("one", "two", "three");
```
  
**길이 : 배열.length**  
**P.s : length()가 아님**  
  
*접근법은 다른 언어와 다르지 않음*  

####  PHP

**배열 생성**  

```php
$list = array("one", "two", "three");
```

**길이 : count($배열)**  
  
*접근법은 다른 언어와 다르지 않음*  

### 배열과 반복문 (11_Array_in_Loop.php)

#### Javascript

```js
list = new Array("one", "two", "three");
i = 0;

while(i < list.length){
    document.write("<li>"+list[i]+"</li>");
    i = i + 1;
}
```

#### PHP

```php
$list = array("최진혁", "최유빈", "한이람", "한이은");
$i = 0;

while($i < count($list)){
    echo "<li>".$list[$i]."</li>";
    $i = $i + 1;
}
```