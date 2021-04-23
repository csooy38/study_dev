# 자바스크립트(JavaScript)?
- 자바스크립트는 HTML 페이지와 어울어져서 웹 페이지 내의 여러 가지 요소를 다이나믹하게 제어하는 기술.
- 자바스크립트는 개발자가 만든 문서에 방문자가 방문하여 어떤 동작을 취했을 때, 그 동작에 대응하여 반응이 일어날 수 있도록 해 주는 언어.
- 자바스크립트는 웹 브라우저에서 사용하기 위해서 만들어진 프로그래밍 언어. 이 언어는 90년대부터 주로 웹 브라우저 상에서  UI를 동적으로 보여주기 위해서 사용을 해 왔다.
- 기존에는 브라우저에서만 사용해 왔던 언어인데, 이제는 단순히 웹 페이지에서만 국한되지 않고 서버 쪽에서도 사용되는 언어로 발전되고 있다. 


* 서버 쪽 주요 언어: JSP, ASP, PHP, Spring 등등
* 클라이언트 측 주요 언어
	- HTML : 홈페이지를 구현하기 위한 뼈대가 되는 핵심적인 기술인 마크업 언어.
	- 자바스크립트 : 로컬 브라우저에서 실행되는 인터프리터 방식의 프로그래밍 언어.
	- CSS : HTML은 뼈대이고, 자바스크립트가 기능이라면, CSS는 꾸미기 위한 옷의 기능.
	- JQuery : 자바스크립트의 코드가 길어지면 사용이 복잡해지는 단점을 파격적으로 개선한 자바스크립트 기반의 라이브러리.
                              
                              
## 자바스크립트 언어의 특징
1. 자바스크립트는 인터프리터 언어이다.
	- 코드가 작성된 순서대로 윗줄부터 순차적으로 구문을 분석하여 실행을 한다.
 	-  코드에 문제가 생기면 에러가 발생한 행 이전까지만 구문을 분석하여 실행을 하고, 에러가 발생한 다음 줄 부터는 구문을 분석하지 않는다.
2. 자바스크립트는 클라이언트 스트립트 언어이다.
	- 자바스크립트는 서버에서 실행되는 것이 아니라, 사용자(방문자) 컴퓨터에서 실행이 된다. 따라서 서버의 부하를 줄여줄 수 있다.
3. 객체 기반 언어이다.
	- 자바스크립트는 객체를 기반으로 한 언어이다. 다양한 객체가 존재하며, 그에 해당하는  다양한 기능(메서드-함수)들이 존재한다.
4. 공개된 언어이다.
	- 최근에 자바스크립트의 활용 범위가 넓어지면서 이미 개발된 코드를 단순히 복사하고 붙여 넣는 것이 아니라 검색을 하면 다양한 소스들이 오픈이 되어 있다.
5. 다양한 라이브러리를 활용할 수 있다.
	- 자바스크립트의 대표적인 라이브러리 언어는 제이쿼리(JQuery). 자바스크립트를 이용하여 다양한 기능들을 쉽게 구현할 수 있도록 만들어 놓은 함수들의 집합을 이용하면 쉽게 구현이 가능하다.


# 자바 스크립트의 기본
`<head>` 태그 안에 `<script>` 태그를 열고 그 안에 내용을 입력하여 사용한다.  
```javascript
<script type="text/javascript">
	// 스크립트 내용 입력
</script>
```


### * 주석 처리
기본적으로 java와 비슷하다.

```javascript
// 한 줄 주석

/*
	여러 줄 주석
*/
```


## 자바 스크립트에서 데이터를 출력시키는 방법 3가지
1. console.log()를 이용하는 방법
2. document.write()를 이용하는 방법
3. alert()를 이용하는 방법


### 1. console.log()를 이용하는 방법
`console.log()`는 콘솔 창에 로그를 출력하는 명령어로, 주로 디버깅 시에 필요한 정보를 출력할 때 사용한다. ==> 전문 디버깅 도구.  
크롬과 사파리 브라우저에서만 사용 가능하다.

```html
console.log("Hello, JavaScript");
```

`<body>`태그에 아무 내용을 작성하지 않았으므로 깨끗한 창이 열리지만  
<p align="center"><img src="./images/210422/00.png"></p>  


개발자모드(F12)로 보면 콘솔창에 입력된 데이터가 잘 출력되어 있다.
<p align="center"><img src="./images/210422/01.png"></p>  


`console.log()`는 `html`태그 밖, `head`태그 안, `body`태그 안에서 선언이 가능하다.  
다만 관례상 `head` 태그 안에서 사용하는 것을 권장한다.  

```html
<!DOCTYPE html>

	<script type="text/javascript">

		console.log("html 태그 밖에서 선언했습니다.");
	
	</script>

<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<script type="text/javascript">

	// 관례상 head 태그 안에서 사용하는 것을 권장.
	console.log("head 태그 안에서 선언했습니다.");

</script>
</head>
<body>

	<script type="text/javascript">
	
		console.log("body 태그 안에서 선언했습니다.");	
	
	</script>

</body>
</html>
```

마찬가지로 창에는 아무것도 출력되지 않지만,  
개발자모드의 콘솔창에서 각각의 태그에서 입력한 데이터가 출력되었음을 알 수 있다.  
<p align="center"><img src="./images/210422/02.png"></p>  




### 2. document.write()를 이용하는 방법
`<script>`태그에서 선언하면 자동으로 HTML 문서의 body 영역에 괄호 안의 내용을 출력하는 함수.  
자동 줄바꿈이 안 되므로 html 태그인 `<br>`를 괄호 안에 넣어 활용한다.  

```javascript
document.write("document.write()를 이용하는 방법<br>");
document.write("자바 스크립트");
```
`<br>`을 넣었더니 줄바꿈이 잘 적용되었다.  
<p align="center"><img src="./images/210422/03.png"></p> 


이외에도 html 문법을 괄호 안에 넣어 다양하게 활용 가능하다.

```javascript
document.write("<h4 style='color: red;'>document.write()와 html문법</h4><br>");
```

<p align="center"><img src="./images/210422/04.png"></p> 



테이블도 만들 수 있다.
```javascript
let tab = "<table border='1' cellsapcing='0'>";
tab += "<tr>";
tab += "<td>"+(num1+num2)+"</td><td>"+(num1-num2)+"</td>"+
		"<td>"+(num1*num2)+"</td><td>"+(num1/num2)+"</td>";
tab += "</tr>";
tab += "</table>"
	
document.write(tab);
```

<p align="center"><img src="./images/210422/06.png"></p> 


### 3. alert()를 이용하는 방법.
`alert()`는 알림창(경고창)의 형식으로 데이터를 출력한다.

```javascript
alert("alert()를 이용하는 방법");
```
실행하면 아래와 같이 새 창에 바로 알림창이 열린다.  
<p align="center"><img src="./images/210422/05.png"></p> 


### * 디버깅 
개발 시 문법적으로 전혀 문제가 없어도 어떤 경우에는 정상적으로 동작하고, 어떤 경우에는 동작이 제대로 안 되는 경우가 발생한다. 프로그램에서는 이런 것을 논리적인 오류인 버그라고 부르고, 버그를 찾아 없애는 작업을 디버깅이라고 한다.


### * 외부에 있는 자바스크립트 파일을 불러와서 실행하는 방법 
```javascript
<script type="text/javascript" src="../js/console.js"></script>
```


## 자바 스크립트에서의 입출력 대화상자 3가지 
1. 알림창(경고창) `alert` : 특정 정보를 사용자에게 메시지 창으로 알려주기 위해 주로 사용한다.
	- `window.alert("알림 내용 또는 경고 내용");`
	- `alert("알림 내용 또는 경고 내용");`
		
2. 확인창 `confirm` : `window.confirm("문자열");` `confirm("문자열");`
3. 입력창 `prompt` : `window.prompt("문자열", 초기값);` `prompt("문자열", 초기값);`


### 1. 알림창(경고창) `alert`
특정 정보를 사용자에게 메시지 창으로 알려주기 위해 주로 사용한다.

```javascript
alert("alert()를 이용하는 방법");
```
실행하면 아래와 같이 새 창에 바로 알림창이 열린다.  
<p align="center"><img src="./images/210422/05.png"></p> 


### 2. 확인창 `confirm`
확인창은 `확인` 버튼과 `취소`버튼을 선택할 수 있는 창이다.
* `확인` : `true` 반환.
* `취소` : `false` 반환.

```javascript
let type = confirm("현재는 오전인가요?");
	
console.log(type);
console.log(typeof type);
```

실행시 다음과 같이 `확인` 또는 `취소`를 선택할 수 있는 확인창이 자동 실행된다.  
<p align="center"><img src="./images/210422/11.png"></p> 


이중 `확인`을 선택하면 `true`값이,
<p align="center"><img src="./images/210422/12.png"></p> 


`취소`를 선택하면 `false`값이 반환된다.
<p align="center"><img src="./images/210422/14.png"></p> 


### 3. 입력창 `prompt`
입력창은 키보드로부터 데이터를 입력받는 방법이다.  
입력값은 모두 `string`타입, 즉 문자열로 저장된다.  
문자열 이외의 자료형으로 활용하기 위해서는 변환이 필요하다.  
* `parseInt()` : 문자열을 정수로 바꿔주는 코드.
* `Number()` : wrapper클래스 자료형. number로 형변환. 

```javascript
let height = prompt("키를 입력하세요.");
	
console.log(typeof height);	

// 적정 표준 몸무게를 알아보자.
// 적정 표준 몸무게 : (키 - 100) * 0.9
let standWeight = (parseInt(height) - 100) * 0.9;
	
document.write("당신의 적정 몸무게는 " + standWeight + "kg입니다.<br>");
```
`prompt`는 입력값을 모두 문자열로 받으므로,  
연산작성시 `parseInt()` 코드를 활용해 정수형으로 바꾸었다.  
대신 `Number()` 클래스도 쓸 수 있다. 예) `Number(height)`  


실행하면 입력이 가능한 입력창이 자동으로 실행된다.  
요구하는 값을 입력하고 `확인`을 누르면
<p align="center"><img src="./images/210422/15.png"></p> 


기존에 작성한 연산에 따른 적정 표준 몸무게를 출력한다.
<p align="center"><img src="./images/210422/16.png"></p> 


개발자모드로 확인하면 입력값은 `170`으로 정수였음에도 `string`타입으로 저장된 걸 알 수 있다.
<p align="center"><img src="./images/210422/17.png"></p> 




# 자바 스크립트의 변수	 
## 1. 변수
데이터를 저장하는 공간. 데이터가 변할 수 있다.
	* 물건을 보관했다가 필요할 때 다시 꺼내 사용하는 일종의 창고라고 생각하면 된다. 보관하는 내용이 물건 대신 데이터라는 점.
	* 특히 자바스크립트는 변수에 숫자와 문자 뿐만 아니라 함수와 클래스까지 저장이 가능하다.
* 형식1) `var 변수명 = 값;`	
	* 동일한 변수명이 생성가능하여 문제가 발생할 수 있므로 권장하지 않는다.
	* `var`의 의미 : 자바스크립트에서 변수 선언을 의미하는 키워드.
* 형식2) `let 변수명 = 값;` 
	* ES6 버전 이후부터 권장하는 변수 선언 방식.
	
```javascript
var name = "가가가";
console.log(name);
	
var name = "나나나";
console.log(name);
```

동일한 변수명 `name`에 각기 다른 두 값이 모두 입력되어 정상 출력된다.   
지금은 괜찮지만 코드가 길어지고 함수가 복잡해지면 문제가 발생할 수 있으므로 사용을 자제하는 것이 좋다.   
<p align="center"><img src="./images/210422/07.png"></p> 



```javascript
let name = "다다다";
onsole.log(name);
	
let name = "라라라";
console.log(name);
```
반면에 `let` 변수는 동일한 변수명 사용시 error가 발생하여, 동일한 변수명을 사용할 수 없다.  
<p align="center"><img src="./images/210422/08.png"></p> 

		
## 2. 상수
데이터를 저장하는 공간으로, 한 번 초기화된 상수의 데이터는 변할 수 없다.
* 형식) `const 상수명 = 값;`

```javascript
const num = 47;
document.write(num);
```
상수가 선언되어 브라우저에도 잘 출력된다.
<p align="center"><img src="./images/210422/09.png"></p> 
	

이때 상수의 값을 변경해보면 어떻게 될까?
```javascript
num = 150; 
document.write(num + "<br>");
```

위에서 선언한 `47`만 그대로 출력되고, 변경한 `150`은 출력되지 않는다.  
<p align="center"><img src="./images/210422/09.png"></p>  


개발자모드로 확인해보면 error 발생했음을 알 수 있다.  
당연하지만 상수의 값은 변경할 수 없으므로, 강제로 변경시 error가 발생한다.
<p align="center"><img src="./images/210422/10.png"></p> 
		
				
		
## * 자바스크립트에서의 자료형
- 숫자형`number` : 숫자를 표현하는 자료형. 숫자 안에서도 정수, 실수로 구분이 되는데 자바스크립트에서의 숫자 자료형은 그 종류들을 하나로 총괄한다. 십진수와 실수형은 일반적으로 사용하는 숫자. 하지만 16진수는 글자색이나 배경색을 나타낼 때 주로 사용한다.
	* 예) `var age = 30;` (정수 10진수)
	*	`var color = 0xF00;` (빨간색)
- 문자형(string) : 작은 따옴표 또는 큰 따옴표를 양 끝에 두고, 그 안에 한 글자 이상의 기호 또는 숫자가 있는 자료형을 문자형이라고 한다.
	* 예) `var name = "홍길동";`
- 논리형`boolean` : 참`true` 또는 거짓`false` 두 가지 값을 가지는 자료형.
- typeof 연산자 : 해당 변수의 자료형을 알려주는 연산자.
- 함수형`function`
- 클래스`class`
- 클래스 인스턴스`class instance`
- `undefined` : 일반적으로 변수를 만든 후 초기화하지 않은 상태를 말한다.
	* 예) `var data;`
	
```javascript
let data;
document.write("data >>> " + data + "<br>");
```
<p align="center"><img src="./images/210423/11.png"></p> 

- `null` : 아무것도 참조하고 있지 않다는 의미. 주로 객체를 담을 변수를 초기화할 때 많이 사용된다.
- `NaN` : Not A Number. 즉, 숫자가 아닌 데이터를 숫자처럼 사용할 때 나타난다.

```javascript
let a = Number("$1000");
document.write("a >>> " + a + "<br>");
document.write("0/0 >>> " + 0/0);
```
<p align="center"><img src="./images/210423/12.png"></p> 
	

## * 변수명 작성 규칙
1. 영문 대/소문자, 숫자, _ 또는 $ 만을 사용할 수 있다.
2. 변수명의 첫 글자로는 숫자가 오면 안 된다.
3. 변수명은 대소문자를 구분함. 예) `SUM`과 `sum`은 다른 변수명으로 인식.
4. 변수명 작성 시 소문자로 시작한다.
5. 공백이 들어가면 안 된다.
6. 변수명을 사용 시 되도록 의미를 부여해서 작성하는 것이 좋다.
7. 자바스크립트 예약어를 사용할 수 없다. 예) `document`, `do`, `for`, `var` 등
8. 두 단어 이상을 결합해서 변수명을 사용하는 경우 낙타봉 표기법(camelCase)을 권장한다. 예) `resultOfHap`



# 자바 스크립트의 연산자
기본적으로 java의 연산자와 비슷하다.


## 1. 기본 연산자 `+` `-` `*` `/` `%`
기본적으로 java의 연산자와 동일하다.
- `+` : 덧셈.
- `-` : 뺄셈.
- `*` : 곱셈.
- `/` : 나눗셈.
- `%` : 나머지.
	- 홀수, 짝수 판별할 때 많이 사용.
	- 배수 판별시에도 사용. 


## 2. 대입 연산자 `=`
좌항에 우항의 데이터를 대입하는 연산자.


## 3. 관계(비교) 연산자 `>=` `>` `<=` `<` `==` `!=` `===`
결과는 boolean형(`true` `false`)으로 반환된다.  
java의 연산자와 동일하나 자바 스크립트에서는 `==`의 사용법이 달라졌으며, `===`가 새롭게 등장하였다.
- `>=` : 크거나 같다 
- `>` : 크다 
- `<=` : 작거나 같다 
- `<` : 작다
- `!=` : 같지 않다


* `==` : 동등연산자로 비교 대상 값의 자료형이 다른 경우 강제로 형을 바꾼 뒤에 비교한다. 따라서 좌항과 우항의 자료형은 상관없이 **내용만 같으면** `true`값을 반환하고, 내용이 틀리면 `false` 값을 반환한다.
* `===` : 일치연산자로 좌항과 우항의 내용과 자료형이 정확하게 같을 때 true, 다르면 false 반환한다. 즉, 내용뿐만 아니라 자료형까지 비교하여 결과를 반환한다.

```javascript
let su1 = "1000";	// 문자열
let su2 = 1000;		// 숫자
	
document.write(su1 + " == " + su2 + " >>> " + (su1 == su2) + "<br>");	
```

각기다른 자료형에 동일한 데이터를 넣어 비교하여 `==` 연산자로 비교하니  
아래와 같이 `true`값이 반환되었다.  
<p align="center"><img src="./images/210422/18.png"></p> 
참고로 java에서는 `false`값을 반환한다.  


그렇다면 자료형까지 함께 비교하기 위해서는 어떻게 해야 할까?    
이 때는 `===` 연산자를 사용해야 한다.  

```javascript
let su1 = "1000";	// 문자열
let su2 = 1000;		// 숫자

document.write(su1 + " === " + su2 + " >>> " + (su1 === su2) + "<br>");
```

위의 결과와 다르게 좌항과 우항의 자료형이 다르므로 `false`값을 반환한다.
<p align="center"><img src="./images/210422/19.png"></p>

   
## 4. 논리 연산자 `&&` `||` `!`
논리연산자는 우선적으로 관계연산자를 실행한 후에 그 결과값을 가지고 수행한다.
* `&&` : 좌항과 우항이 모두 참이면 `true` 값을, 하나라도 거짓이면 `false`값을 반환한다.
* `||` : 좌항과 우항 중 하나라도 참이면 `true`값을, 이외에는 모두 `false`값을 반환한다.
* `!` : `true`이면 `false`, `false`이면 `true`가 된다.

```javascript
let a = "A";	// 65
let b = "B";	// 66
	
let c = !2 || 3 && !0; 		// false || true && true ==> true
document.write(c+"<br>");
	
c = a < b && a == b;		// true && false ==> false
document.write(c+"<br>");
	
c = a < b || a == b;		// true || false ==> true
document.write(c+"<br>");
```


`!2`는 2가 아닌 값으로, 무조건 0이 된다.  
0은 `false`, 0을 제외한 나머지는 모두 `true`이므로, `!2`는 `false`가 된다.  
<p align="center"><img src="./images/210423/04.png"></p>  




## 5. 단항 연산자(증감 연산자) `++` `--`
- 전위연산자: 단항연산자가 변수명 앞에 온다. 예) `++i` `--i`
	- 변수의 값을 하나 증가 또는 감소 후에 처리한다.
- 후위연산자: 단항연산자가 변수명 뒤에 온다. 예) `i++` `i--`
	- 변수를 처리한 후에 값을 하나 증가 또는 감소한다.

```javascript
let num1 = 10;
let num2 = 20;

document.write("++num1 = " + ++num1 + "<br>"); 
document.write("num1++ = " + num1++ + "<br>");
```

<p align="center"><img src="./images/210423/02.png"></p>


```javascript
let a = 10;
let b = 20;
let c = 3;

document.write("++a = " + ++a + "<br>"); // 11
document.write("a++ = " + a++ + "<br>"); // 11
document.write("c++ = " + c++ + "<br>"); // 3
document.write("++a + b++ = " + ++a + b++ + "<br>"); // 13 + 20 = 33
document.write("++a + ++b = " + ++a + ++b + "<br>"); // 14 + 22 = 36
```

<p align="center"><img src="./images/210423/03.png"></p>



### * 삼항 연산자
* 형식) `(조건) ? 참인 경우 실행문 : 거짓인 경우 실행문;`
* java와는 달리, 참인 경우 실행문과 거짓인 경우 실행문의 자료형이 달라도 된다.

```javascript
let num = 27;
	
let result = (num > 20) ? "참" : false;
	
document.write("(num > 20) ? "참" : false >>>" + result);
```

<p align="center"><img src="./images/210423/01.png"></p> 


## 7. 복합대입연산자  `+=` `-=` `*=` `/=` `%=`
복합대입연산자는 대입연산자`=`와 다른 연산자를 하나로 묶어 간단하게 표현할 때 주로 사용한다.  

```javascript
let a = 10;
	
document.write("a = a + 10 >>> " + (a += 10) + "<br>");
document.write("a = a - 10 >>> " + (a -= 10) + "<br>");
document.write("a = a * 10 >>> " + (a *= 10) + "<br>");
document.write("a = a / 10 >>> " + (a /= 10) + "<br>");
document.write("a = a % 10 >>> " + (a %= 10) + "<br>");
```

<p align="center"><img src="./images/210423/00.png"></p> 



# 제어문
1. 조건문 : 조건을 제시하여 참이면 실행하고, 거짓이면 무시하는 문장.
	- if문 
	- if~else문 
	- 다중 if~else문
	- switch~case문  
	 
2. 반복문 : 조건식을 비교하여 참인 경우 계속해서 반복 실행문을 실행하고,
조건식이 거짓인 경우에는 반복문을 빠져나가는 문장.
	- while문 
	- for문
	- do~while문 (거의 사용하지 않는다)

제어문 블록 안에서 선언된 변수(지역변수)는 블록 밖에서 사용불가능하다.  


## 1. 조건문
조건을 제시하여 참이면 실행하고, 거짓이면 무시하는 문장.
* 조건문의 종류
	- if문 
	- if~else문 
	- 다중 if~else문
	- switch~case문   
	

### 1. 조건문 - if문
if문은 조건을 제시하여 참이면 실행하고, 거짓이면 무시하는 문장이다.
* 형식) `if(조건식) { 조건식이 참일 경우 실행문 };`

```javascript
let name = prompt("방문자의 이름은?");

if(name) {
	document.write(name + "님 환영합니다.");
}
```

<p align="center"><img src="./images/210423/05.png"></p>   
<p align="center"><img src="./images/210423/06.png"></p>   

단, 조건식에 `0`, `null`, `""`, `undefined` 등의 값이 들어가면 `false`를 반환하므로 주의하자.  
입력창에 아무것도 입력하지 않았더니 '님 환영합니다.' 조차 출력되지 않는다.  
if문 자체가 `false`처리 되어 작동하지 않았기 때문이다.  
<p align="center"><img src="./images/210423/07.png"></p> 
<p align="center"><img src="./images/210423/08.png"></p> 


#### [예] if문 : 사용자의 아이디가 "test"일 경우에만 환영문구를 출력해 보자.

```javascript
let userId = prompt("아이디를 입력하세요.");

if(userId == "test"){
	document.write(userId + "님 환영합니다.");
}
```

입력값이 "test"가 아닌 경우 아무것도 출력되지 않는다.  
<p align="center"><img src="./images/210423/09.png"></p> 
<p align="center"><img src="./images/210423/10.png"></p> 


### 1. 조건문 - 2) if~else문
조건식이 참이면 조건식이 참인 경우 실행문을 실행하고 if-else문을 빠져 나온다.  
조건식이 거짓이면 조건식이 거짓인 경우 실행문을 실행하고 if-else문을 빠져 나온다.  
* 형식)
 
```
if(조건식) {
	조건식이 참인 경우 실행문;
}else {
	조건식이 거짓인 경우 실행문;
}
```

#### [예] if~else문 : confirm 창을 활용해 보자.
```javascript
let result = cofirm("정말 탈퇴하시겠습니까?");
	
if(result) {
	document.write("탈퇴 처리하였습니다.");
}else {
	document.write("취소되었습니다.");
}
```

`confirm`에서 `확인`은 `true`를, `취소`는 `false`를 반환하는 것을 이용하여 작성하였다.  
확인 버튼을 누르면 탈퇴처리 메시지가, 취소 버튼을 누르면 취소처리 메시지가 출력된다.  
<p align="center"><img src="./images/210423/13.png"></p> 
<p align="center"><img src="./images/210423/14.png"></p> 
<p align="center"><img src="./images/210423/15.png"></p> 


### 1. 조건문 - 다중 if~else문
여러 개의 조건문 중에 맞는 조건에 해당하는 문장을 실행하는 구조.
* 형식) 

```
if(조건식1) {
	조건식1이 참인 경우 실행문;
}else if(조건식2) {
	조건식1이 거짓이고 조건식2가 참인 경우 실행문;
}else if(조건식3) {
	조건식1, 2이 거짓이고 조건식3이 참인 경우 실행문;
}else {
	조건식1, 2, 3이 모두 거짓인 경우 실행문;
}
```


#### [예] 다중 if~else문 : 성적을 출력해 보자.
```javascript
let kor = parseInt(prompt("국어 점수를 입력하세요."));
let eng = parseInt(prompt("영어 점수를 입력하세요."));
let mat = parseInt(prompt("수학 점수를 입력하세요."));
	
let avg = (kor+eng+mat) / 3;	// 평균
	
let grade;	// 학점을 받을 변수
		
if(avg >= 90) {
	grade = "A학점";
}else if(avg >= 80) {
	grade = "B학점";
}else if(avg >= 70) {
	grade = "C학점";
}else if(avg >= 60) {
	grade = "D학점";
}else {
	grade = "F학점";
}
	
document.write("국어 점수 : " + kor + "점<br>");
document.write("영어 점수 : " + eng + "점<br>");
document.write("수학 점수 : " + mat + "점<br>");
document.write("평  균 : " + avg.toFixed(2) + "점<br>");
document.write("학  점 : " + grade + "<br>");
```
* `toFixed(소숫점길이)` : 숫자에서 원하는 소숫점 길이만큼만 반올림하여 출력하는 함수.


입력창에 국어, 영어, 수학 점수를 각각 입력하면  
<p align="center"><img src="./images/210423/16.png"></p> 
<p align="center"><img src="./images/210423/18.png"></p> 
<p align="center"><img src="./images/210423/17.png"></p>


스크립트에 작성한 if~else문에 따라 학점까지 계산되어 출력된다.  
평균값인 avg를 출력할 때 `toFixed()`를 이용하여 소숫점 아래 두자리까지만 출력되었다.  
<p align="center"><img src="./images/210423/19.png"></p>


만약 `toFixed()`를 쓰지 않고 avg를 그대로 출력할 경우  
avg의 자료형은 실수형이므로 아래와 같이 소숫점 아래 숫자가 길게 출력된다.  
<p align="center"><img src="./images/210423/20.png"></p>



### 1. 조건문 - 다중 switch~case문
식을 사용해서 다중분기하는 명령문.  
* 형식
   
```javascript
switch(식 또는 값) {
	case 값1 :
		값1일 때 실행문;
		break;	 // switch~case 블록 탈출. 생략시 다음 break를 만날때까지 이어서 실행.
	case 값2 :
		값2일 때 실행문;
		break;	 
	case 값3 :
		값3일 때 실행문;
		break;	 
	default :
		값1, 2, 3 외에 다른 값이 들어온 경우 실행문;
)
```

다중 if-else문을 switch-case문으로 변경할 수 있는 경우는 if문 중 조건식이 특정한 값과 일치하는 경우(`==`)뿐이다. 즉, 조건식에 `==`를 사용한 경우를 제외하고 `>=`, `>`, `<=`, `<`, `!=` 과 같은 비교연산자를 사용한 경우에는 switch-case문으로 변경할 수 없다.


#### [예] 다중 switch~case문
```javascript
let site = prompt("네이버, 다음, 구글 중 자주 사용하는 포털 사이트는?");
		
let url;
	
switch(site){
	case "네이버" :
		url = "www.naver.com";
		break;
	case "다음" :
		url = "www.daum.net";
		break;
	case "구글" :
		url = "google.co.kr";
		break;
	default :
		alert("보기 중에 없는 사이트입니다.");
}
	
if(url) {
	location.href="http://"+url;	// 페이지로 이동이 진행됨.	
}else {
	location.reload();	// 현재 페이지 새로고침
}
```


예를 들어 구글을 입력하면 자동으로 구글 사이트로 페이지가 이동된다.  
<p align="center"><img src="./images/210423/21.png"></p>
<p align="center"><img src="./images/210423/22.png"></p>


만약 네이버, 다음, 구글 외의 사이트를 입력하거나 빈 창으로 확인을 누르면  
현재 페이지가 새로고침되어 다시 값을 입력하는 창을 열린다.  
<p align="center"><img src="./images/210423/23.png"></p>
<p align="center"><img src="./images/210423/24.png"></p>



#### [예] 다중 switch~case문 : 난수를 발생시켜 추첨을 통해서 경품을 받게 해 보자.
```javascript
// 1에서부터 10까지의 난수를 발생
let luckyNo = parseInt(Math.random()*10) + 1;
	
switch(luckyNo) {
	case 3 :
		document.write("냉장고에 당첨되었습니다.<br>");
		break;
	case 5 :
		document.write("세탁기에 당첨되었습니다.<br>");
		break;
	case 8 :
		document.write("TV에 당첨되었습니다.<br>");
		break;
	default : 
		document.write(luckyNo + "(이)가 나왔네요...꽝!<br>");
	}
```

* `Math.random()` : 0 이상 1 미만의 랜덤 숫자 발생시키는 함수.

```java
Math.random() 						// 0 <= Math.random() < 1
Math.random()*10					// 0 <= Math.random() < 10
parseInt(Math.random()*10)		// 범위 내의 수를 정수로 형변환. : 0 ~ 9 
parseInt(Math.random()*10)+1	// 1 <= Math.random() < 11 : 1 ~ 10
```

`Math.randome()` 함수를 이용하여 1에서부터 10까지의 난수를 만들어 추첨하는 코드를 작성하였다.  
switch~case문에 따라 발생한 난수가 3, 5, 8이면 경품에 당첨되고, 이외의 숫자는 꽝에 해당한다.  
실행하면 난수값이 변하면서 당첨과 꽝을 오간다. 30% 확률이라 당첨률은 그다지 나쁘지 않다.  
<p align="center"><img src="./images/210423/25.png"></p>
<p align="center"><img src="./images/210423/26.png"></p>



## 2. 반복문
특정 구문을 여러 번 반복해서 실행하고자 할 때 사용하는 제어문.  
조건식을 비교하여 참인 경우 계속해서 반복 실행문을 실행하고, 조건식이 거짓인 경우에는 반복문을 빠져나가는 문장이다.

* 반복문의 종류
	- while문
	- for문
	

### 2. 반복문 - while문
주로 무한 반복하거나 반복 횟수가 정해지지 않은 경우에 사용한다.
* 형식

```
while(조건식-관계연산자) {
	조건식이 참인 동안 반복 실행되는 문장;
}
```

#### [예] while문 : 1부터 100까지의 수를 홀수는 빨간색, 짝수는 파란색으로 출력해 보자.

```javascsript
let num = 1;

while (num <= 100) {	// num이 100보다 작은 동안 반복된다.
	if (num % 2 == 1) {	// 2로 나눈 값이 1 즉, 홀수이면
		document.write("<font color='red'>" + num
				+ "</font>&nbsp;&nbsp;&nbsp;");
	} else {	// // 2로 나눈 값이 1 즉, 홀수가 아니라면
		document.write("<font color='blue'>" + num
				+ "</font>&nbsp;&nbsp;&nbsp;");
	}
	num++;		// 후위연산자로 num 값 1증가
}
```
* `&nbsp;` : html에서 띄어쓰기 한 번만큼 출력되도록 하는 코드. 


`num++`에 의해 1에서 100까지 숫자가 커지는 동안   
while문 안에서 if문이 수행되어 홀수는 빨간색, 짝수는 파란색으로 출력된다.   
<p align="center"><img src="./images/210423/27.png"></p>


### 2. 반복문 - for문
변수의 값을 이용하여 반복 실행하는 명령문. 반복 횟수가 정해진 경우에 사용한다.  
*형식

```
for(초기식; 조건식; 증감식) {
	반복 실행문;
}
```

* for문 실행 순서
	1. 초기식 : 처음에 한 번만 실행됨(변수 선언)
	2. 조건식 : 조건이 참이면 반복되고, 거짓이면 탈출(exit)
	3. 실행문 : 반복 대상인 반복 실행문이 실행됨.
	4. 증감식 : 변수를 대상으로 증가(++) 또는 감소(--) 


#### [예] for문 : 1에서 30까지의 수를 5의 배수는 빨간색, 6의 배수는 파란색, 7의 배수는 초록색으로 출력해 보자.

```javascript
for(let i=1; i<=30; i++) {
	if(i % 5 == 0) {
		document.write("<font color='red'>" + i + "</font>&nbsp;");
	}else if(i % 6 == 0) {
		document.write("<font color='blue'>" + i + "</font>&nbsp;");
	}else if(i % 7 == 0) {
		document.write("<font color='green'>" + i + "</font>&nbsp;");
	}else {
		document.write(i+"&nbsp;");
	}
}
```

출력문에 html언어를 사용하여 출력문의 글자 색상을 변경할 수 있다.  
<p align="center"><img src="./images/210423/28.png"></p>



#### [예] 다중 for문 : 테이블을 만들어 보자.

```javascript
document.write("<table border ='1'; cellspacing = '0'; width='150';");

for(let i=1; i<=5; i++) {
	document.write("<tr>");
	
	for(let j=0; j<5; j++) {
		document.write("<td align='right'>" + (j*5+i) + "</td>");
	}
	document.write("</tr>");	
}

document.write("</table>");
```

<p align="center"><img src="./images/210423/29.png"></p>




# 배열
자바 스크립트에서 배열은 모든 데이터 타입(자료형)을 다 담을 수 있다.  
java에서의 Object 배열과 같다고 보면 된다.  


## 1. 자바스크립트에서 배열 객체 생성 방법 3가지
1. let 배열명 = new Array(원소1, 원소2, ... , 원소n);
2. let 배열명 = [원소1, 원소2, ... , 원소n];
3. let 배열명 = new Array();


### 1. let 배열명 = new Array(원소1, 원소2, ... , 원소n);

```javascript
let arr1 = new Array("가나다", "ABC", 123, true);
let arr1 = new Array('가나다', 'ABC', 123, true);	
// "" 나 '' 모두 동일하다.

document.write(arr1 + "<br>"); 	// 전체요소 출력

document.write(arr1[2]);		// 특정 요소 출력
```

<p align="center"><img src="./images/210423/30.png"></p>



### 2. let 배열명 = [원소1, 원소2, ... , 원소n];
```javascript
let arr2 = ["가나다", "ABC", 123, true];
let arr2 = ['가나다', 'ABC', 123, true];
// "" 나 '' 모두 동일하다.
```

<p align="center"><img src="./images/210423/32.png"></p>


### 3. let 배열명 = new Array();
```javascript
let arr3 = new Array();
arr3[0] = "가나다";
arr3[1] = "ABC";	//또는 'ABC'도 가능.
arr3[2] = 123;
arr3[3] = true;
```

<p align="center"><img src="./images/210423/32.png"></p>



이때 값이 없는 인데스를 호출하면 `undefined`가 출력된다.

```javascript
document.write(arr3[5]);
```

<p align="center"><img src="./images/210423/31.png"></p>



### * length
`length`를 사용하여 for문으로 출력도 사용가능하다. 

```javascript
for(let i=0; i<arr3.length; i++) {
	document.write("arr3[" + "] >>> " + arr3[i] + "<br>");
}
```

<p align="center"><img src="./images/210423/33.png"></p>


### * 배열에 요소를 다루는 방법

* `push(요소)` : 배열에 데이터를 추가하는 방법. 맨 뒤에 요소를 추가한다.

```javasript
let arr = [10, 20, 30];
document.write(arr+"<br>");

arr.push(40);
document.write(arr);
```

<p align="center"><img src="./images/210423/34.png"></p>


* `concat` : 배열에 복수 개의 데이터를 추가하는 방법.
	- 형식: `concat([추가할 원소1, 추가할 원소2, ... , 추가할 원소n]);`

```javascript
arr = arr.concat([50, 60, 70]);
document.write(arr);
```

<p align="center"><img src="./images/210423/35.png"></p>


* `unshift(추가할 요소)` : 배열의 맨 앞(0번째 index)에 추가한다.
	- 기존에 있던 요소들은 인덱스가 하나씩 뒤로 밀린다.

```javascript
arr.unshift('0');
document.write(arr);
```

<p align="center"><img src="./images/210423/36.png"></p>



* `shift()` : 배열의 맨 처음 요소를 제거하는 방법.

```javascript
arr.shift();
document.write(arr);
```

<p align="center"><img src="./images/210423/37.png"></p>



* `pop()` : 배열의 맨 마지막 요소를 제거하는 방법.

```javascript
arr.pop();
document.write(arr);
```

<p align="center"><img src="./images/210423/38.png"></p>


* `sort()` : 배열의 요소를 정렬하는 방법.

```javascript
let arr = ['c', 'd', 'b', 'a', 'e'];
document.write(arr + "<br>");

arr.sort();
document.write(arr + "<br>");
```

<p align="center"><img src="./images/210423/39.png"></p>


* `reverse()` : 배열의 요소를 역순(내림차순)으로 정렬하는 방법.

```javascript
arr.reverse();
document.write(arr + "<br>");
```

<p align="center"><img src="./images/210423/40.png"></p>



