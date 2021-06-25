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

----------------------------------------------

# 1. 자바 스크립트의 기본
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


## 1.1.자바 스크립트에서 데이터를 출력시키는 방법 3가지
1. console.log()를 이용하는 방법
2. document.write()를 이용하는 방법
3. alert()를 이용하는 방법


### 1.1.1. console.log()를 이용하는 방법
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




### 1.1.2. document.write()를 이용하는 방법
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


### 1.1.3. alert()를 이용하는 방법.
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


## 1.2. 자바 스크립트에서의 입출력 대화상자 3가지 
1. 알림창(경고창) `alert` : 특정 정보를 사용자에게 메시지 창으로 알려주기 위해 주로 사용한다.
	- `window.alert("알림 내용 또는 경고 내용");`
	- `alert("알림 내용 또는 경고 내용");`
		
2. 확인창 `confirm` : `window.confirm("문자열");` `confirm("문자열");`
3. 입력창 `prompt` : `window.prompt("문자열", 초기값);` `prompt("문자열", 초기값);`


### 1.2.1. 알림창(경고창) `alert`
특정 정보를 사용자에게 메시지 창으로 알려주기 위해 주로 사용한다.

```javascript
alert("alert()를 이용하는 방법");
```
실행하면 아래와 같이 새 창에 바로 알림창이 열린다.  
<p align="center"><img src="./images/210422/05.png"></p> 


### 1.2.2. 확인창 `confirm`
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


### 1.2.3. 입력창 `prompt`
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



---------------------------------
#  2. 변수 Variable
## 2.1. 변수
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

		
## 2.2. 상수
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
		
				
		
## 2.3. 자바스크립트에서의 자료형
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
	

## 2.4. 변수명 작성 규칙
1. 영문 대/소문자, 숫자, _ 또는 $ 만을 사용할 수 있다.
2. 변수명의 첫 글자로는 숫자가 오면 안 된다.
3. 변수명은 대소문자를 구분함. 예) `SUM`과 `sum`은 다른 변수명으로 인식.
4. 변수명 작성 시 소문자로 시작한다.
5. 공백이 들어가면 안 된다.
6. 변수명을 사용 시 되도록 의미를 부여해서 작성하는 것이 좋다.
7. 자바스크립트 예약어를 사용할 수 없다. 예) `document`, `do`, `for`, `var` 등
8. 두 단어 이상을 결합해서 변수명을 사용하는 경우 낙타봉 표기법(camelCase)을 권장한다. 예) `resultOfHap`


--------------------------------------
# 3. 연산자 Operator
기본적으로 java의 연산자와 비슷하다.


## 3.1. 기본 연산자 `+` `-` `*` `/` `%`
기본적으로 java의 연산자와 동일하다.
- `+` : 덧셈.
- `-` : 뺄셈.
- `*` : 곱셈.
- `/` : 나눗셈.
- `%` : 나머지.
	- 홀수, 짝수 판별할 때 많이 사용.
	- 배수 판별시에도 사용. 


## 3.2. 대입 연산자 `=`
좌항에 우항의 데이터를 대입하는 연산자.


## 3.3. 관계(비교) 연산자 `>=` `>` `<=` `<` `==` `!=` `===`
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

   
## 3.4. 논리 연산자 `&&` `||` `!`
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




## 3.5. 단항 연산자(증감 연산자) `++` `--`
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



## 3.6. 삼항 연산자
* 형식) `(조건) ? 참인 경우 실행문 : 거짓인 경우 실행문;`
* java와는 달리, 참인 경우 실행문과 거짓인 경우 실행문의 자료형이 달라도 된다.

```javascript
let num = 27;
	
let result = (num > 20) ? "참" : false;
	
document.write("(num > 20) ? "참" : false >>>" + result);
```

<p align="center"><img src="./images/210423/01.png"></p> 


## 3.7. 복합대입연산자  `+=` `-=` `*=` `/=` `%=`
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




--------------------------------------
# 4. 제어문 Control
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


## 4.1. 조건문
조건을 제시하여 참이면 실행하고, 거짓이면 무시하는 문장.
* 조건문의 종류
	- if문 
	- if~else문 
	- 다중 if~else문
	- switch~case문   
	

### 4.1.1. 조건문 - if문
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


### 4.1.2. 조건문 - if~else문
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


### 4.1.3. 조건문 - 다중 if~else문
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



### 4.1.4. 조건문 - 다중 switch~case문
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



## 4.2. 반복문
특정 구문을 여러 번 반복해서 실행하고자 할 때 사용하는 제어문.  
조건식을 비교하여 참인 경우 계속해서 반복 실행문을 실행하고, 조건식이 거짓인 경우에는 반복문을 빠져나가는 문장이다.

* 반복문의 종류
	- while문
	- for문
	

### 4.2.1. 반복문 - while문
주로 무한 반복하거나 반복 횟수가 정해지지 않은 경우에 사용한다.
* 형식

```
while(조건식-관계연산자) {
	조건식이 참인 동안 반복 실행되는 문장;
}
```

#### [예] while문 : 1부터 100까지의 수를 홀수는 빨간색, 짝수는 파란색으로 출력해 보자.

```javascript
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


### 4.2.2. 반복문 - for문
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



-----------------------------------------
# 5. 배열 Array
자바 스크립트에서 배열은 모든 데이터 타입(자료형)을 다 담을 수 있다.  
java에서의 Object 배열과 같다고 보면 된다.  


## 5.1. 자바스크립트에서 배열 객체 생성 방법 3가지
1. let 배열명 = new Array(원소1, 원소2, ... , 원소n);
2. let 배열명 = [원소1, 원소2, ... , 원소n];
3. let 배열명 = new Array();


### 5.1.1. let 배열명 = new Array(원소1, 원소2, ... , 원소n);

```javascript
let arr1 = new Array("가나다", "ABC", 123, true);
let arr1 = new Array('가나다', 'ABC', 123, true);	
// "" 나 '' 모두 동일하다.

document.write(arr1 + "<br>"); 	// 전체요소 출력

document.write(arr1[2]);		// 특정 요소 출력
```

<p align="center"><img src="./images/210423/30.png"></p>



### 5.1.2. let 배열명 = [원소1, 원소2, ... , 원소n];
```javascript
let arr2 = ["가나다", "ABC", 123, true];
let arr2 = ['가나다', 'ABC', 123, true];
// "" 나 '' 모두 동일하다.
```

<p align="center"><img src="./images/210423/32.png"></p>


### 5.1.3. let 배열명 = new Array();
```javascript
let arr3 = new Array();
arr3[0] = "가나다";
arr3[1] = "ABC";	//또는 'ABC'도 가능.
arr3[2] = 123;
arr3[3] = true;
```

<p align="center"><img src="./images/210423/32.png"></p>



이때 값이 없는 인덱스를 호출하면 `undefined`가 출력된다.

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


## 5.2. 배열에 요소를 다루는 방법

* `push(요소)` : 배열에 데이터를 추가하는 방법. 맨 뒤에 요소를 추가한다.

```javasript
let arr = [10, 20, 30];
document.write(arr+"<br>");

arr.push(40);
document.write(arr);
```

<p align="center"><img src="./images/210423/34.png"></p>


* `concat()` : 배열에 복수 개의 데이터를 추가하는 방법.
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




-----------------------------------
# 6. 함수 Function
함수는 기능을 정의해놓은 것으로, 하나의 로직을 재사용할 수 있도록 하는 것으로 코드의 재사용성을 높여준다.  

## 6.1. 함수를 정의하는 방법 
* 형식)

```javascript
function 함수명(매개변수, 매개변수2, ...) {
	함수 호출 시 실행문;
	return 반환값;
}
```

* 매개변수
매개변수는 변수의 종류로, 일종의 외부 데이터를 함수 내부로 전달하는 매개체의 역할을 한다. 함수 내부에는 포장이 되어 있기 때문에 한 번 실행이 되면 외부에서 접근이 불가능하다. 함수 외부에서 함수 내부로 값을 전달하기 위해 매개변수를 이용한다. 


* 반환값(return)
반환값은 매개변수와는 반대되는 개념이다.  
매개변수 값이 함수 외부에서 함수 내부로 들어오는 값이라면, 반환값은 함수 내부에서 처리된 결과값을 함수 외부로 전달하기 위해 사용되는 일종의 출력값을 의미한다. 이 때 사용되는 키워드가 return이다. 리턴값이라고도 한다.  
 

* 함수 사용 시 장점
	1. 코드의 중복 제거 및 코드 재사용 가능
	2. 유지보수 용이성
		
		
* 자바스크립트 함수의 종류
	1. 사용자 정의 함수 : 사용자가 직접 만들어 놓은 함수.
	2. 내장 함수 : 자바스크립트에서 자체적으로 제공해 주는 함수.

#### [예] 함수 : 매개변수 없는 사용자 정의 함수를 작성해 보자.

```javascript
function hello() {	// 함수 정의
	alert("안녕하세요. 반갑습니다.");
}
	
hello();	// 정의한 함수 호출
```

<p align="center"><img src="./images/210426/00.png"></p>


#### [예] 함수 : 매개변수가 있는 함수를 호출하는 코드를 작성해 보자.

```javascript
function adder(num1, num2) {	// 입력한 두 수를 매개변수로 받아서

	// 두 수의 합을 브라우저에 표시한다.
	document.write("두 수의 합 >>> " + (num1 + num2) + "<br>");
}

let su1 = parseInt(prompt("첫번째 숫자 입력"));
let su2 = parseInt(prompt("두번째 숫자 입력"));

adder(su1, su2);
```

두 수를 입력하면   
<p align="center"><img src="./images/210426/01.png"></p>
<p align="center"><img src="./images/210426/02.png"></p>


사용자 정의 함수에 따라 두 수의 합이 자동으로 출력된다.   
<p align="center"><img src="./images/210426/03.png"></p>



#### [예] 함수 : 반환값이 있는 함수를 호출하는 코드를 작성해 보자.

```javascript
// num1, num2를 매개변수로 받아서 num1+num1를 반환한다.
function sum(num1, num2) {
	return num1 + num2;
}

let su1 = parseInt(prompt("첫번째 숫자 입력"));
let su2 = parseInt(prompt("두번째 숫자 입력"));

// num1+num1가 반환되어 result 변수에 저장된다.
let result = sum(su1, su2);

document.write(su1 + " + " + su2 + " = " + result + "<br>");
```


<p align="center"><img src="./images/210426/04.png"></p>
<p align="center"><img src="./images/210426/05.png"></p>
<p align="center"><img src="./images/210426/07.png"></p>



## 6.2. 함수를 정의하는 방법 - 무명함수(익명함수)
무명함수는 이름이 없는 함수를 말한다. 이벤트 처리 등에 자주 사용이 된다.  
주로 함수를 재사용하지 않는 경우에 함수를 무명으로 만든다.

```javascript
let numbering = function() {
	for(let i=1; i<=10; i++) {
		document.write("i >>> " + i + "<br>");
	}
}

numbering();
```

let 변수에는 함수도 저장이 가능하다.   
따라서 let 변수를 함수와 같이 `numbering()`로 호출하면 자동으로 `function()`이 실행된다.   


<p align="center"><img src="./images/210426/06.png"></p>



#### [예] 함수

```javascript
function sample() {
	
	let sum = 0, count = 1;
	
	while(true) {
		let value = parseInt(prompt("수 입력"));
		
		if(value == 0) { // 0이 입력되면 함수가 종료된다.
			document.write("종료합니다. <br>");
			return; // 함수를 탈출하는 명령어. 
		}
		
		sum += value;
		
		// 입력된 값을 출력을 해 보자.
		document.write(count + " : " + sum + "<br>");
		
		count++;
	}		
} // sample() 함수 end

sample();
```

<p align="center"><img src="./images/210426/04.png"></p>
<p align="center"><img src="./images/210426/05.png"></p>
<p align="center"><img src="./images/210426/08.png"></p>
<p align="center"><img src="./images/210426/09.png"></p>
<p align="center"><img src="./images/210426/10.png"></p>




-------------------------------------
# 7. 객체 Object
## 7.1. 객체 생성 방법
### 7.1.1. 객체 생성 방법 1
객체 생성과 동시에 키와 데이터를 객체에 입력하는 방법.  

```javascript

// member라는 변수를
// name, age, addr이라는 키와 각각의 데이터를 입력하여 생성
// name(키): '홍길동'(데이터)
let member = {name: '홍길동', age:27, addr: '서울시 마포구'};

document.write("회원 이름 >>> " + member['name'] + "<br>");

// member의 키가 k로 넘어온다.
// 따라서 member[k]를 호출하면 각각의 키에 저장된 데이터가 출력된다.
for(let k in member) {
	document.write(k+"의 value >>> " + member[k] + "<br>");
}
```

<p align="center"><img src="./images/210426/11.png"></p>



### 7.1.2. 객체 생성 방법 2
객체를 먼저 생성한 후, 각각의 키마다 데이터 값을 입력한다. 

```javascript
let member = {};
member['name'] = '홍길동';	// 
member['age'] = 27;
member['addr'] = '서울시 마포구';

for(let k in member) {
	document.write(k+"의 value >>> " + member[k] +"<br>");
}
```

<p align="center"><img src="./images/210426/12.png"></p>



## 7.2. 내장 객체
자바 스크립트에서 제공하는 객체.

### * `Date()`
`Date()`는 날짜와  시간과 관련된 정보를 제공하는 객체다.   

```javascript
let date = new Date();
	
document.write("현재 년도 : " + (date.getYear()+1900) + "년<br>");
document.write("현재 년도 : " + date.getFullYear() + "년<br>");
document.write("현재 월 : " + (date.getMonth()+1) + "월<br>");
document.write("현재 일 : " + date.getDate() + "일<br>")
```
* `getYear()` : 1900년을 기준으로 하여 입력년도와의 차를 출력. 예) 1901년 ==> 1년
* `getFullYear()` : 전체 년도를 출력.
* `getMonth()` : 0부터 달을 출력. 예) 0 ==> 1월, 1 ==> 2월.
* `getDate()` : 입력한 날(일)을 출력.


`getYear()`를 사용할 경우 +1900을 해줘야 입력 년도가 정확하게 출력된다.  
`getMonth()`를 사용할 경우 +1을 해줘야 입력 달(월)이 정확하게 출력된다.  
<p align="center"><img src="./images/210426/13.png"></p>



```javascript
let date = new Date();
let day = date.getDay();

switch(day) {
	case 0 : 
		document.write("현재 요일은 일요일입니다.<br>");
		break;
	case 1 : 
		document.write("현재 요일은 월요일입니다.<br>");
		break;
	case 2 : 
		document.write("현재 요일은 화요일입니다.<br>");
		break;
	case 3 : 
		document.write("현재 요일은 수요일입니다.<br>");
		break;
	case 4 : 
		document.write("현재 요일은 목요일입니다.<br>");
		break;
	case 5 : 
		document.write("현재 요일은 금요일입니다.<br>");
		break;
	case 6 : 
		document.write("현재 요일은 토요일입니다.<br>");
		break;
}
```
* `getDay()` : 현재 요일 ==> 정수값 반환(0:일요일 ~ 6:토요일)

오늘 요일인 월요일이 제대로 출력된다.
<p align="center"><img src="./images/210426/14.png"></p>


```javascript
document.write("현재 시간 : " + date.getHours() + " : ");
document.write(date.getMinutes() + " : ");
document.write(date.getSeconds() + " : ");
```

* `getHours()` : 시를 출력.
* `getMinutes()` : 분을 출력.
* `getSeconds()` : 초를 출력.

<p align="center"><img src="./images/210426/15.png"></p>



### * Math()
`Math()`는 수학과 관련된 연산을 하는 함수다.
* `Math()` 내장 객체와 관련된 함수(메서드)
	- abs(숫자) : 숫자의 절대값을 반환하는 함수
	- max(숫자1, ... , 숫자n) : 숫자 중 가장 큰 값을 반환하는 함수.
	- min(숫자1, ... , 숫자n) : 숫자 중 가장 작은 값을 반환하는 함수.
	- pow(숫자, 제곱값) : 숫자의 거듭제곱한 값을 반환하는 함수.
	- random() : 0 ~ 1 사이의 난수를 발생시키는 함수.
	- round(숫자) : 소수점 첫째 자리에서 반올림하여 정수를 반환하는 함수.
	- ceil(숫자) : 소수점 첫째 자리에서 무조건 올림해서 정수를 반환하는 함수.
	- floor(숫자) : 소수점 첫째 자리에서 무조건 내림해서 정수를 반환하는 함수.
	- sqrt(숫자) : 숫자의 제곱근 값을 반환하는 함수.


```javscript
document.write("최대값 >>> " + Math.max(30, 47, 8, 95, 81) + "<br>");
	document.write("최소값 >>> " + Math.min(30, 47, 8, 95, 81) + "<br>");
	
document.write("<br>");
	
let num = 2.5234;
	
document.write("2.5234의 round() : " + Math.round(num) + "<br>");
document.write("2.5234의 ceil() : " + Math.ceil(num) + "<br>");
document.write("2.5234의 floor() : " + Math.floor(num) + "<br>");
```

<p align="center"><img src="./images/210426/16.png"></p>





-------------------------------------
# 8. BOM(Browser Object Model : 브라우저 객체 모델) 
BOM은 브라우저 내에 내장된 객체를 의미한다.  
BOM 객체의 최상위 내장 객체는 `window` 객체로, 생략가능하다.  
 
## 8.1. window 객체
* `window` 객체의 주요 메서드
	- `open()` : 새로운 창을 띄우고자 할 때 사용하는 메서드.
	- `alert()` : 경고 창을 띄울 때 사용하는 메서드.
	- `prompt()` : 질의/응답 창을 띄울 때 사용하는 메서드.
	- `confirm()` : 확인/취소 창을 띄울 때 사용하는 메서드.
	- `moveTo()` : 창의 위치를 이동시킬 때 사용하는 메서드.
	- `resizeTo()` : 창의 크기를 변경시킬 때 사용하는 메서드.
	- `setInterval()` : 일정 간격으로 지속적으로 실행문을 실행시킬 때 사용하는 메서드.
	- `setTimeout()` : 일정 간격으로 한번만 실행문을 실행시킬 때 사용하는 메서드.
	

## 8.2. screen 객체
사용자의 모니터 정보(속성)를 제공해 주는 객체. 
 * `screen` 객체의 주요 속성  
	- `screen.width` : 화면의 너비값을 반환하는 속성.
	- `screen.height` : 화면의 높이값을 반환하는 속성.
	- `screen.availWidth` : 작업표시줄을 제외한 화면의 너비값을 반환하는 속성.
	- `screen.availHeight` : 작업표시줄을 제외한 화면의 높이값을 반환하는 속성.
	- `screen.colorDepth` : 사용자 모니터가 표현 가능한 컬러 bit를 반환하는 속성.


```javascript
document.write("화면 너비 >>> " + screen.width + "<br>");
document.write("화면 높이 >>> " + screen.height + "<br>");
document.write("작업표시줄을 제외한 화면 너비 >>> " + screen.availWidth + "<br>");
document.write("작업표시줄을 제외한 화면 높이 >>> " + screen.availHeight + "<br>");
document.write("표현가능한 컬러 bit >>> " + screen.colorDepth + "<br>");
```

실제 컴퓨터 해상도와 일치하는 가로너비와 세로높이가 출력된다.  
<p align="center"><img src="./images/210426/17.png"></p>


화면 높이와 작업표시줄을 제외한 화면 높이를 비교해보면 작업표시줄의 높이는 40px임을 짐작해볼 수 있다.      
<p align="center"><img src="./images/210426/18.png"></p>



## 8.3. location 객체
`location` 객체는 자바스크립트가 실행되고 있는 현재 브라우저의 주소창에 표시된 주소 값에 관련된 내용을 다룬다. 사용자 브라우저의 주소 창의 url에 대한 정보(속성)와 새로고침 기능을 제공하는 객체.  
* `location` 객체의 주요 속성 및 메서드
	- `location.href` : 브라우저 창의 url 값을 반환하는 속성.
	- `location.reload()` : 브라우저 창의 새로고침이 일어나게 하는 메서드.

```javascript
document.write("url 정보 >>> " + location.href);
```

현재 브라우저의 url 값이 그대로 출력되었다.
<p align="center"><img src="./images/210426/19.png"></p>


## 8.4. history 객체
`history` 객체는 브라우저가 페이지를 변경한 이력이 클라이언트에 저장되어 있는 객체이다. 사용자가 방문한 사이트 중 이전에 방문한 사이트와 다음 방문한 사이트로 다시 돌아갈 수 있는 속성과 메서드를 제공한다.

* `history` 객체의 속성과 메서드
	- `length` : 방문 기록에 저장된 목록의 개수를 반환하는 속성. 
	- `history.back()` : 이전에 방문한 웹 페이지로 이동하는 메서드.
	- `history.forward()` : 다음에 방문한 웹 페이지로 이동하는 메서드.
	- `history.go(숫자)` : 이동 숫자만큼 페이지로 이동하는 메서드.
		- 숫자가 해당 수만큼 양수이면 앞으로, 음수이면 해당 수만큼 뒤로 이동한다.

다음과 같은 페이지 3개를 만들어 `history` 객체의 메서드를 살펴 보자.   
첫번째 페이지)

```html
<body>
	<h1>첫번째 페이지</h1>
	
	<a href="Exam_02.html">두번째 페이지</a>
	
	<hr>
	
	<button onclick="history.back()">이전 페이지</button>
	<button onclick="history.forward()">다음 페이지</button>
</body>
```

<p align="center"><img src="./images/210426/20.png"></p>


두번째 페이지)

```html
<body>
	<h1>두번째 페이지</h1>
	<a href="Exam_03.html">세번째 페이지</a>
	
	<hr>
	
	<button onclick="history.back()">이전 페이지</button>
	<button onclick="history.forward()">다음 페이지</button>	
</body>
```

<p align="center"><img src="./images/210426/21.png"></p>


세번째 페이지)
세번째 페이지는 `history.go()`메서드를 이용하여 만들었다.  
* `history.go(-1)` : 1번 뒤로 가기
* `history.go(-2)` : 2번 뒤로 가기 (= 앞으로)

```html
<body>
	<h1>세번째 페이지</h1>
	<a href="Exam_01.html">첫번째 페이지</a>
	
	<hr>

	<button onclick="history.go(-1)">이전 페이지</button>
	<button onclick="history.go(-2)">다음 페이지</button>
</body>
```

<p align="center"><img src="./images/210426/22.png"></p>


다음과 같이 실행된다. 
<p align="center"><img src="./images/210426/00.gif"></p>



---------------------------------------
# 9. DOM(Document Object Model : 문서 객체 모델)
DOM은 웹 화면에 보이는 요소를 조작하기 위한 기능으로 가득 찬 라이브러리 덩어리로, 웹 브라우저가 HTML 페이지에 접근하는 방법을 정의한 API이다.  


DOM에서 제공하는 일반적인 기능은 여러 개의 DOM 객체로 나눠 구성되어 있다. DOM은 정의부분(명세서)와 구현부분으로 나누어져 있다.  
정의부분인 명세서에는  웹 페이지 문서를 조작할 때 지켜야 할 약속(규칙, 규약)이 명시되어 있는 문서일 뿐 실제 동작하는 구현 소스코드는 전혀 존재하지 않는다. 텅 빈 상자와도 같다. 이 명세서를 만드는 곳이 바로 웹 관련 표준을 정의하는 협회인 W3C이다. 구현부분은 바로 브라우저 내부에 존재한다.  


브라우저 제작사(IE, Chrome, Firefox, Safari)는 DOM에 명시되어 있는 인터페이스에 맞춰 자신들만의 특화된 고유 기술을 이용해 독자적으로 기능을 구현한다.
- IDL(Interface Definition Language) : DOM의 정의부분을 만들 때 사용하는
    인터페이스 정의 전용 언어이다. 프로그래밍 언어 중 하나이며, 고유의 문법이 있다. (참고 : http://www.w3.org/TR/DOM-Level-2-HTML/html.html#ID-22445964) 그렇다고 IDL을 배우는 것은 아니고, 그냥 DOM 문서는 인터페이스 정의 문서로 되어 있다는 정도만 알고 있으면 된다.
    
		
눈에 보이진 않지만 사실 브라우저에 출력된 웹 페이지는 온통 DOM 객체로 구성되어 있다. DOM 객체는 텍스트와 이미지, 하이퍼링크, 폼 엘리먼트 등의 각 문서 엘리먼트를 나타낸다. 자바스크립트 코드에서는 동적인 HTML을 만들어내기 위해 DOM 객체에 접근하여 조작할 수 있다.  
- 문서 객체 : 자바스크립트에서 이용할 수 있는 객체.


* 노드 : HTML 웹 페이지 구성 요소의 가장 작은 단위. 
	- 문서를 이루는 모든 요소를 통합해서 부르는 용어. 즉, HTML 페이지의 각 요소(태그)들. 주석도 노드에 속한다.
	- 브라우저는 이런 노드로 가득찬 웹 페이지를 읽어들여 해석한 후, 각 노드에 접근해 제어할 수 있는 DOM 객체를 생성한다.
* 요소(element) : `<시작태그>텍스트</끝태그>`
* 텍스트 노드 : 요소 안에 있는 글자. `innerHTM`L과 관계가 있다.
	- 노드, 스타일, 속성, 이벤트, 위치 및 크기들을 다룰 수 있는 다양한 기능이 포함되어 있다.
	- DOM 객체가 생성되는 순서를 자세히 살펴 보면, 웹브라우저는 가정 먼저 최상위에 해당하는 `HTMLDocument` 클래스의 객체를 생성한다. 이후에 생성되는 모든 DOM 객체는 `HTMLDocument` 객체의 자식 객체로 만들어진다. 
	- 보통 DOM 방식은 트리 구조이다. 브라우저가 웹 페이지를 처리하는 과정을 살펴보면 먼저 브라우저는 문서 정보에 쉽게 접근하고 조작하고자 HTML 웹 페이지를 읽은 후 파싱 단계를 거친다. 이 후 DOM 객체로 변환(트리구조) 후 화면에 출력을 한다.
	- 예) 웹 페이지에 `<img src="test.jpg">` 태그 노드가 있다면 브라우저에 의해 `HTMLImageElement`라는 DOM 객체가 생성된다. 이 객체는 다른 DOM 객체와는 다르게 이미지를 읽어들이는 특별한 기능이 있어서 실행 시에 "test.jpg" 라는 외부 이미지 파일을 읽어 들이게 된다. 즉, 문서 상의 노드는 "브라우저이군. 이 노드를 보고 알맞은 DOM 객체를 생성해 주세요." 라는 의미일 뿐, 모든 작업은 이제 브라우저에서 만들어낸 DOM 객체로 처리하게 된다.

	 
* 브라우저가 웹 페이지를 처리하는 과정
	1. 웹 페이지 읽기 : 먼저 브라우저는 HTML 페이지를 읽는다.
	2. 파싱 단계 : 이어서 파싱(parsing) 단계를 거쳐서 웹 페이지 내용을 해석한다.
		- 이 때 작성한 마크업 태그와 1:1 매칭이 되는 DOM 클래스 객체를 생성한다. 이렇게 생성된 객체는 저마다 고유한 기능을 하게 된다.
		- 좀 더 자세하게 설명을 한다면 웹 브라우저가 HTML 페이지를 읽은 후 파싱 단계에서 `div` 태그를 만나게 되면 `HTMLDivElement` 라는 클래스의 인스턴스(객체)를 생성하게 되고, `img` 태그를 만나면 `HTMLImageElement` 라는  클래스의 인스턴스를 생성하게 된다는 의미이다.
		- 정리를 한다면 HTML 페이지에 작성하는 마크업은 웹브라우저에게 알려주는 일종의 DOM 클래스의 메타 정보이다. 브라우저는 이 마크업 태그와 1:1로 매칭되는 DOM 클래스의 객체를 생성해서 보관을 하고 있게 된다.
	3. 출력 : 마지막으로 웹 브라우저는 생성한 DOM 객체를 가지고 우리가 보고 있는 웹 페이지 화면을 만든다.
	  

* Node 객체 : Node 객체는 노드를 조작하기 위한 가장 기본적인 프로퍼티와 메서드가 정의되어 있는 Node 인터페이스를 구현한 객체이다. 
	- Node 객체에서 제공하는 기능을 이용하면 노드 타입을 파악하거나 부모, 형제 그리고 자식 노드를 알아내서 접근하거나, 또는 자식 노드를 추가, 삭제, 교체를 할 수 있다. 
	- 좀 더 자세히 설명을 한다면 Node 객체는 DOM 객체 가운데 가장 최상위 객체이자 모든 하위 노드 객체들이 상속을 받는 객체이다.
	
	  		
* Element 객체 : Element는 노드 중 주석 노드와 텍스트 노드를 제외한 나머지 노드를 통합해서 부르는 용어이다. 
	- Element 객체 역시 노드의 한 종류이며 Element 인터페이스를 구현한 객체임. 또한 Element 객체는 Node 객체의 자식이므로 Node 객체가 가지고 있는 기능을 모두 사용할 수 있다.
	- Element 객체의 주요 기능으로는 태그 이름이 담긴 프로퍼티와 속성(Attribute)을 알아내고 설정하는 기능과 이벤트를 추가하거나 삭제하거나 발생시키는 기능이 있다.
	  	           
	  	    
* HTMLElement 객체 : HTMLElement는 오직 HTML 문서에만 있는 노드를 통합해서 부르는 말이다.
	- HTMLElement 객체에는 Element 객체의 기능 외에도 오직 HTML 페이지의 `p`, `div` 태그와 같은 HTML 태그에서만 쓸 수 있는 공통적인 속성과 기능이 포함이 되어 있다.
	- HTMLElement 객체는 `HTMLDivElement`, `HTMLImageElement`, `HTMLBodyElement`와 같은 객체의 부모 객체이기도 하다.
	  	    

* Document 객체 :  Document 객체 역시 Node 객체의 하위 객체이며 HTML 문서와 xml 문서의 루트 객체로 엘리먼트 노드와 이벤트, 속성 노드, 텍스트 노드, 주석 등의 노드를 생성하는 기능, 그리고 많이 사용하게 될 `id`, `className`, `tagName`으로 특정 노드를 찾는 기능 그리고 여기에 이벤트를 발생시키고 등록시키는 이벤트 기능까지 갖춘 아주 중요한 객체이다.
	  	    

* HTMLDocument 객체 : HTMLDocument 객체는 HTML 문서 전용 Document 객체이다. 
	- body와 같은 HTML 문서 전용 프로퍼티와 메서드가 포함되어 있다. HTML 페이지 로딩 후 파싱 단계에서 만들어진 `html`, `head`, `body` 객체를 비롯해서 페이지에 작성된 태그와 일대일로 매칭되는 모든 Node 객체를 가지고 있는 객체이기도 함. 
	   
	   		
* DOM을 공부하면서 알아야 할 내용
1. 노드 다루기
	- 문서에서 특정 태그 이름을 지닌 노드 찾기
	- 특정 노드의 자식 노드에서 특정 태그 이름을 지닌 노드 찾기
	- 문서에서 특정 클래스가 적용된 노드 찾기
	- 문서에서 특정 id를 가진 노드 찾기
	  		   
	- 자식 노드 찾기
	- 부모 노드 찾기
	- 형제 노드 찾기
	   		   
	- `document.createElement()` 메서드를 사용해서 노드 생성 및 추가하기
	- `HTMLElement.innerHTML` 프로퍼티를 사용해서 노드 생성 및 추가하기
	- `Node.cloneNode()` 메서드를 사용해서 노트 생성 및 추가하기
	- 노드 삭제하기
	- 노드 이동시키기
	   		   
	- 텍스트 노드 생성 및 추가하기
	- 텍스트 노드 내용 변경하기
	   		   
2. 스타일 다루기
	- 스타일 속성값 구하기
	- 스타일 속성값 설정하기
	- 스타일 속성 제거하기
	   		   
3. 속성 다루기
	- 속성값 구하기
	- 속성값 설정하기
	- 속성 제거하기
	   		   
4. 이벤트 다루기
	- 이벤트 리스너 추가하기
	- 이벤트 리스너 삭제하기
	- 이벤트 발생시키기
	- 사용자 정의 이벤트 만들기
	    

#### [예] `document.createElement()` 메서드를 사용해서 노드 생성 및 추가하기 1

```javascript
// 현재 문서의 body 태그를 읽고 난 후에 자바 스크립트를 실행하라는 의미.
window.onload = function() {
	
	// 요소(태그)를 생성하는 방법
	// 형식) createElement(tagName);
	// 형식) createTextNode(text); : 텍스트 노드를 생성하는 메서드
	let h1_element = window.document.createElement("h1");
	
	let textNode = window.document.createTextNode("Hello, DOM!");
	
	// 텍스트 노드를 h1태그에 자식으로 추가
	h1_element.appendChild(textNode);
	
	// 이제 실제로 문서의 body에 h1 요소를 추가하면 된다.
	window.document.body.appendChild(h1_element);
}
```

`<script>` 영역에 트리 구조로 요소를 쌓았다.  
`<body>` 태그에는 아무것도 작성하지 않았음에도 텍스트 노드에 작성한 내용이 `<h1>`태그로 작성되어 출력된다.  
<p align="center"><img src="./images/210426/23.png"></p>


개발자 모드로 확인하면 `<body>` 태그에 작성한 것과 동일하게 나온다.  
<p align="center"><img src="./images/210426/24.png"></p>




#### [예] `document.createElement()` 메서드를 사용해서 노드 생성 및 추가하기 2 : 이미지 출력하기
`window`는 생략 가능하므로 생략하였다.

```javascript
onload = function() {
	
	// 이미지 태그를 만들어 보자.
	let imgNode = document.createElement("img");
	
	// 이미지 태그에 이미지를 넣으려면 src 속성이 지정되어야 한다.
	imgNode.src = "../images/mango.jpg";
	imgNode.width = "200";
	imgNode.height = "200";
	
	// 해당 이미지 노드를 문서의 본문에 추가하자.
	document.body.appendChild(imgNode);
}
```

src 속성 지정을 아래와 같이 작성해도 동일한 결과가 나온다.  

```javascript
imgNode.setAttribute("src", "../images/mango.jpg");
imgNode.setAttribute("width", 200);
imgNode.setAttribute("height", 200);
```


지정한 사이즈인 200*200 크기의 망고 이미지가 출력되었다.  
<p align="center"><img src="./images/210426/25.png"></p>


## 9.1. 문서의 요소를 가져오는 방법 
### 9.1.1. 문서의 요소를 가져오는 방법 : getElementById(id) 를 이용하는 방법


```html
<script type="text/javascript">

	onload = function() {
		let header1 = document.getElementById("header_1");
		
		// 문서 객체의 속성을 변경해 보자.
		header1.innerHTML = "header_1 id를 가진 요소";
		header2.innerHTML = "header_2 id를 가진 요소";
	}
</script>
</head>
<body>
	<h1 id="header_1">Header 1</h1>
	<h1 id="header_1">Header 2</h1>
</body>
```

* `innerHTML` : 해당 텍스트 요소를 변경해준다.




`<body>` 태그에서 'Header 1', 'Header 2'라고 설정하였으나,  
각각 'header_1 id를 가진 요소', 'header_2 id를 가진 요소'로 내용이 변경되었다.
<p align="center"><img src="./images/210426/26.png"></p>



### 9.1.2. 문서의 요소를 가져오는 방법 : getElementsByTagName(tagName)을 이용하는 방법
* `getElementsByTagName(tagName)` : tagName과 일치하는 요소를 배열로 가져오는 메서드. 즉 tagName이 여러개 있을 경우 사용.

```html
<script type="text/javascript">
	onload = function() {

		// header 변수는 h1과 일치하는 요소가 여러 개이므로 배열이 된다.
		let headers = document.getElementsByTagName("h1");
		
		headers[0].innerHtml = "getElementsByTagName() 0";
		headers[1].innerHtml = "getElementsByTagName() 1";		
	}
</script>
</head>
<body>
	<h1>Header1</h1>
	<p>header1 내용</p>
	
	<hr>
	
	<h1>Header2</h1>
	<p>header2 내용</p>
</body>
```

아래와 같이 for문을 이용해서 출력할 수도 있다.

```javascript
for(let i=0; i<headers.length; i++){
	headers[i].innerHTML = "getElementsByTagName() 2"+i;
}
```

기존 출력문)  
<p align="center"><img src="./images/210426/31.png"></p>

DOM 적용 후)
<p align="center"><img src="./images/210426/28.png"></p>



### 9.1.3. 문서의 요소를 가져오는 방법 : querySelector(선택자)를 이용하는 방법
* `querySelector(선택자)` : 선택자로 가장 처음 선택되는 문서의 요소를 가져오는 메서드.
* `querySelectorAll(선택자)` : 선택자로 선택된 문서의 요소 전체를 배열로 가져오는 메서드.

```javascript
onload = function() {
	let header1 = document.querySelector("#header_1");
	let header1 = document.querySelector("#header_2");
		
	header1.innerHTML = "header_1 id를 가진 요소";
	header1.innerHTML = "header_2 id를 가진 요소";
	}
```

<p align="center"><img src="./images/210426/27.png"></p>



## 9.2. 글자의 스타일 바꾸기  

```javascript
onload = function() {
	let header = document.getElementById("header");
		
	// h1 태그의 문서의 요소를 바꾸어 보자.
	header.style.border = "1px solid red";
	header.style.color = "blue";
	header.style.fontStyle = "Italic";
	header.innerHTML = "반갑습니다.";
}
```

<p align="center"><img src="./images/210426/29.png"></p>



## 9.3. 특정 요소를 제거하는 방법
아래와 같이 작성시 id가 "header_2"인 태그는 제거되어 출력되지 않는다.

```javascript
onload = function() {
	let header2 = document.getElementById("header_2");		
		
	document.body.removeChild(header2); 
}
```


## 9.4. 이벤트 처리 작업

```javascript
onload = function() {
	document.getElementById("header");
			
	header.onclick = function() {
		alert("글자를 클릭하셨습니다!");		}
}
```

<p align="center"><img src="./images/210426/01.gif"></p>



#### [예] 버튼을 클릭했을 때 이벤트 처리

```html
<script type="text/javascript">

	document.getElementById("btnChannel1").onclick = function() {
		let myDiv = document.getElementById("myDiv");
		myDiv.style.backgroundColor = "yellow";
		myDiv.style.width = "100px";
			
		document.getElementById("str").style.color = "red";
		}
	}
	
	function go_change() {
		alert("이벤트 예제입니다.");
	}
	
</script>
</head>
<body>

	<div id="myDiv" style="height: 100px;">
		<span id="str">안녕</span>하세요!
	</div>
	
	<input type="button" id="btnChannel1" value="스타일변경1">
	<input type="button" id="btnChannel2" value="스타일변경2" onclick="go_change()">

</body>
```


<p align="center"><img src="./images/210426/02.gif"></p>



#### [예] 복사하기
```html
<script type="text/javascript">

	onload = function() {
		let button = document.getElementById("btn");
		button.onclick = function() {
			let text = document.getElementById("text1").value; // text1 에 입력된 값
			
			if(text == "") { // text1에 입력된 값이 없다면
				alert("내용을 입력하세요.");
			}else {
				document.getElementById("text2").value = text; // text2 에 text를 넣어라.
			}		
		}
	}
</script>
</head>
<body>

	<div align="center">
		<h2>[문제] 버튼을 클릭하면 첫번째 테스트 창에 입력된 내용을 
			두번째 텍스트 창으로 복사해 보자.</h2>
			
		<input type="text" id="text1"><br>
		<input type="text" id="text2"><br>
		<input type="button" id="btn" value="복사"><br>
	</div>

</body>
```

<p align="center"><img src="./images/210426/03.gif"></p>


## 9.5. 자바스크립트 내장 함수
자바스크립트에서 자체적으로 제공해 주는 함수.
* `setInterval()` : 일정한 시간마다 주기적으로 특정한 함수를 호출한다. 반드시 개발자가 종료(clearInterval())를 시켜주어야 한다.
* 형식) `setInterval(호출할 함수 이름, 시간(ms));`


#### [예] 일정 시간마다 글자색 바꾸기

```html
<script type="text/javascript">

	let id;	// 전역 변수
	
	function change_go() {	// 1초마다 flashText 호출
		id = setInterval(flashText, 1000);
	}
	
	// target의 글자색이 red면 blue로, blue면 red로 바꾸는 함수
	function flashText() {	
		let target = document.getElementById("target");
		target.style.color = (target.style.color == "red") ? "blue" : "red";
	}
	
	function stop_go() {	// setInterval()종료
		clearInterval(id);
	}
	
</script>
</head>
<body>

	<div id="target">
		<p>여기는 텍스트 영역입니다......</p>	
	</div>
	
	<button onclick="change_go()">시작</button>
	<button onclick="stop_go()">종료</button>

</body>
```


<p align="center"><img src="./images/210426/04.gif"></p>



#### [예] 유효성 검사 : 회원가입 입력창 입력 여부 확인하기
```html
<title>유효성 검사</title>
<script type="text/javascript">

	function check() {
	/* 	// 아이디 입력창 입력 여부
		if(document.getElementById("id").value == "") {
			alert("아이디를 입력하세요.");
			document.getElementById("id").focus();
			return false;	// 액션 페이지로의 데이터 전송이 차단됨.
		} */
		
		// form의 name이 f인 곳의 id의 value
		if(f.id.value == "") {
			alert("아이디를 입력하세요.");
			f.id.focus();
			return false;	// 액션 페이지로의 데이터 전송이 차단됨.
		}
		
		// 비밀번호 입력창 입력 여부
		if(document.getElementById("pwd").value == "") {
			alert("비밀번호를 입력하세요.");
			document.getElementById("pwd").focus();
			return false;	// 액션 페이지로의 데이터 전송이 차단됨.
		}
		
		// 이름 입력창 입력 여부
		if(document.getElementById("name").value == "") {
			alert("이름을 입력하세요.");
			document.getElementById("name").focus();
			return false;	// 액션 페이지로의 데이터 전송이 차단됨.
		}
		
		// 주소 입력창 입력 여부
		if(document.getElementById("addr").value == "") {
			alert("주소를 입력하세요.");
			document.getElementById("addr").focus();
			return false;	// 액션 페이지로의 데이터 전송이 차단됨.
		}
	}

</script>
</head>
<body>

	<div align="center">
		<form name="f" action="http://www.google.com" onsubmit="return check()">
			<table border="1" cellspacing="0">
				<tr>
					<th>아이디</th>
					<td> <input type="text" name="id" id="id"></td>
				</tr>
				
				<tr>
					<th>비밀번호</th>
					<td> <input type="password" name="pwd" id="pwd"></td>
				</tr>
				
				<tr>
					<th>이  름</th>
					<td> <input type="text" name="name" id="name"></td>
				</tr>
				
				<tr>
					<th>주  소</th>
					<td> <input type="text" name="addr" id="addr"></td>
				</tr>
				
				<tr>
					<td colspan="2" align="center">
						<input type="submit" value="가입">
						&nbsp;&nbsp;&nbsp;
						<input type="reset" value="취소">
					</td>			
			</table>
		</form>
	</div>

</body>
```

<p align="center"><img src="./images/210426/05.gif"></p>



### * getElementsByTagName()
`getElementsByTagName()`의 결과값은 검색된 모든 노드를 NodeList라는 객체에 담아서 반환이 된다. 	NodeList는 자주 사용하는 배열과 비슷한 일종의 ArrayList 컬렉션 객체로 DOM 객체 중 하나이다. NodeList 객체에서 제공하는 프로퍼티와 메서드는 아래와 같다.
- length : 결과값의 전체 개수 정보가 담겨져 있다. 
- item : 결과값을 항목별로 접근할 때 사용한다.


* 문서에서 특정 태그 이름을 지닌 노드 찾기

```javascript
onload = function() {
	// 문서에서 태그 이름이 div인 노드를 찾아보자.
	// div 태그가 여러 개이므로 배열 형태로 저장된다.
	let divs = document.getElementsByTagName("div");
		
	alert("문서 내의 div 태그 개수 >>> " + divs.length);
		
	for(let i=0; i<divs.length; i++) {
		// item() : 찾은 노드에서 n번째 노드에 접근하는 메서드.
		let div = divs.item(i);
		div.style.border = "1px solid red";
	}
}
```


* 특정 노드의 자식 노드에서 특정 태그 이름을 지닌 노드 찾기

```javascript
onload = function() {
		let divs = document.getElementsByTagName("div");
		
		// 찾은 노드 가운데 3번째(2번째 인덱스) 노드를 찾아 보자.
		let div2 = divs[2]; 
		
		let div2Child = div2.getElementsByTagName("div");
		
		for(let i=0; i<div2Child.length; i++) {
			div2Child[i].style.border = "3px solid red";
		}
	}
```


* 문서에서 특정 클래스가 적용된 노드를 찾기

```javascript
onload = function() {
	// 클래스도 중복해서 사용할 수 있으므로, 배열 형태로 저장된다.
	let content = document.getElementsByClassName("content_data");	
		
	alert("content_data 요소 개수 >>> " + content.length);
		
	for(let i=0; i<content.length; i++) {
		content[i].style.border = "3px solid blue"
	}
}
```


* 문서에서 특정 ID를 가진 노드를 찾기

```javascript
onload = function() {
		
	let page = document.getElementById("sample_page");
	let nodes = page.childNodes;	// page의 자식노드(복수)
		
	let header = document.getElementById("header");
	let footer = document.getElementById("footer");
		
	header.style.border = "3px solid red";
	footer.style.border = "3px soild red";
}
```


* 문서에서 자식 노드를 찾기

```javascript
onload = function() {
	let page = document.getElementById("sample_page");
	let nodes = page.childNodes;	// page의 자식노드(복수)
		
	alert("#sample_page의 자식 노드 개수 >>> " + nodes.length);
		
	// 자식 노드 중에서 첫번째 자식 노드 접근
	let firstChild = page.firstChild;
		
	// 텍스트 노드는 스타일을 적용할 수 없다.
	// firstChild.style.border = "3px solid red";
		
	// 자식 노드 중에서 첫번째 자식 노드 접근
	let lastChild = page.lastChild;
		
	// 텍스트 노드는 스타일을 적용할 수 없다.
	// lastChild.style.border = "3px solid red";
}
```


* 문서에서 부모 노드 찾기

```javascript
onload = function() {
	// #header인 노드의 부모 노드 찾기
	let header = document.getElementById("header");
		
	let parent = header.parentNode;
	parent.style.border = "3px solid blue";
		
	// 이렇게도 쓸 수 있다.
	// header.parentNode.style.border = "3px solid blue";
		
	// [문제] id="data_1" 노드의 부모 노드를 찾아서 스타일을 적용해 보기.
	let data = document.getElementById("data_1");
	data.parentNode.style.border = "3px solid red";
	
}
```


* 문서에서 형제 노드를 찾기

```javascipt
onload = function() {
	let content = document.getElementById("content");
		
	// 내 위치에서 이전 형제 노드를 찾는 방법
	let pre = content.previousSibling.previousSibling;
		
	pre.style.border = "3px solid red";
		
	// 내 위치에서 이후 형제 노드를 찾는 방법
	let next = content.nextSibling.nextSibling;
		
	next.style.border = "3px solid blue";
}
```


* `document.createElement()` 메서드를 이용하여 노드 생성 및 추가하기

```javascript
onload = function() {
	// 1. 추가(p태그 추가)
	let page = document.getElementById("sample_page");
		
	// 기준 노드를 찾아 보자.
	let firstChild = page.firstChild;
		
	// <p>태그를 동적으로 생성(실행될 때 생성된다)
	let pNode = document.createElement("p");
		
		// 텍스트 노드도 동적으로 생성
		let textNode = document.createTextNode("추가내용1");
		
		// p태그의 자식노드로 텍스트 노드를 추가
		pNode.appendChild(textNode);
		
		pNode.style.border = "3px solid red";
		
		page.insertBefore(pNode, firstChild);
		
		
		
		// 2. 추가(div 태그 추가)
		let content = document.getElementById("content");
		let div1 = document.createElement("div");
		
		let textNode1 = document.createTextNode("생성할 노드가 많은 경우, ");
		let span1 = document.createElement("span");
		let textNode2 = document.createTextNode("어떤 방법을 ");
		span1.appendChild(textNode2);
		let textNode3 = document.createTextNode("사용해야 할까요?");
		
		// div 태그에 자식노드로 텍스트노드와 span태그를 추가해야 한다.
		div1.appendChild(textNode1);
		div1.appendChild(span1);
		div1.appendChild(textNode3);
		
		div1.style.border = "3px solid blue";
		
		// 생성된 div 태그를 content id의 위쪽에 추가
		page.insertBefore(div1, content);
		
		
		// 3. 추가(p태그 추가)
		let p2Node = document.createElement("p");
		let textNode4 = document.createTextNode("추가내용2");
		p2Node.appendChild(textNode4);
		p2Node.style.border = "3px solid red";
		
		page.appendChild(p2Node);
		
	}
```


* `Node.cloneNode()` 메서드를 이용하여 노드 생성

```javascript
onload = function() {
	let page = document.getElementById("sample_page");
	
	let first = page.firstChild;
	
	let pNode = document.createElement("p");
	
	let textNode = document.createTextNode("추가내용1");
	
	pNode.appendChild(textNode);
	
	pNode.style.border = "3px solid red";
	
	page.insertBefore(pNode, first);
}
```


* 문서에서 노드 삭제하기 

```javascript
onload = function() {
	// 지우려고 하는 노드가 포함된 부모 노드
	let page = document.getElementById("sample_page");	
	
	// 지우려는 노드를 찾자.
	let content = document.getElementById("content");
	
	// 부모 노드의 removeChild() 메서드를 이용하면 된다.
	page.removeChild(content);
	
}
```


* 노드 이동시키기
```javascript
onload = function() {
	// 이동시킬 노드를 찾아보자.
	let header = document.getElementById("header");
	
	// 이동 위치의 노드를 구해보자.
	document.getElementById("content");
	
	// header를 content의 자식 노드로 이동
	content.appendChild(header);
		
	header.style.border = "3px solid blue";
}
```

