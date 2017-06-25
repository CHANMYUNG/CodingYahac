# 0615(~UI vs API)

## 함수

### 함수의 기본 문법 (12_basicGrammarOfFunction.php)

**JS, PHP 공통 : function 키워드를 이용해 선언, { } 바디 안에 실행 내용 기재**  

*Javascript*  
```javascript

// 선언
function A(){
    document.write("FUNCTION A");
}

// 호출
A();
```
  
*PHP*
```php
<?php

    // 선언 
    function B(){
        echo "FUNCTION B";
    }

    // 호출
    B();

?>
```


### 함수의 입력과 출력 (13_IO_in_Function)

함수를 선언할 때 받을 인자값을 지정할 수 있음  

또한 함수 바디 내에선 **return 값** 구문을 작성해 함수 수행을 멈추고, 값을 반환할 수 있음  

*Javascript*
```javascript

// 선언
function A(input){  // 함수를 호출할 때 인자값을 하나 넘겨주겠다!
    return input+77; // 인자값에 77을 더해 반환한다!
}

// 호출
result = A(22); // 22+77인 99가 반환됨

document.write(result);

```

*PHP*
```php
<?php

    // 선언
    function B(input){ // 함수를 호출할 때 인자값을 하나 넘겨주겠다!
        return input+77; // 인자값에 77을 더해 반환한다!
    }

    // 호출
    result = A(22); // 22+77인 99가 반환됨

    echo result;
?>
```

## UI vs API

### UI
**User Interface**  
이해는 했는데...참 *V*  

### API
**Application Programming Interface**  
이해는 했는데 설명을 못하겠다. *V*  