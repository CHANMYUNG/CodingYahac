# 0626 (~보안)

## html special characters
"&lt;script&gt;alert(123);&lt;/script&gt;"라는 문장을 작성하고 싶을 때 
html special characters를 이용해 표현하면 됨  

그냥 썼을 때 :  
```html
<script>alert(123);</script>
```
_화면에 출력되지 않고 팝업창이 뜸_  
  
html special characters를 이용했을 때 :  
```html
&lt;script&gt;alert(123);&lt;script/&gt;
```

php에서는 자체적으로 함수를 제공함

[htmlspecialchars](http://php.net/manual/kr/function.htmlspecialchars.php)
  
  
**별도의 소스 예제를 굳이 만들 필요 없음**