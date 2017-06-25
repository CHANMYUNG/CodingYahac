# 0613(~로그인 기능 만들기)

## 자바스크립트로 로그인 기능 구현하기 (7_prompt.php)

prompt()를 이용해 비밀번호를 입력받고, 조건문을 이용해 판별  

```js
password = prompt("비밀번호를 입력하세요");
if(password='1111') document.write("안녕하세요 주인님");
else document.write("누구슈");
```

## PHP로 로그인 기능 구현하기 (8-1_LoginPage.php, 8-2_Login.php)

HTML &lt;form&gt;태그의 action 속성을 통해 요청 url을 지정할 수 있다.  

**GET 방식으로 들어온 요청을 핸들링하기 위한 PHP 코드**  
**8-2_Login.php**  
```php
<?php
    $password = $_GET["password"];
    if($password == "1111"){
        echo "주인님 환영합니다";
    } else {
        echo "뉘신지?";
    }
   ?>
```
