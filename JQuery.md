# 0. 제이쿼리(JQuery)?
바스크립트 언어를 간편한게 사용할 수 있도록 단순화시킨 오픈 소스 기반의 자바스크립트 라이브러리.  
제이쿼리는 자바스크립트 DOM을 좀 더 쉽게 작업하기 위한 라이브러리 덩어리.
제이쿼리를 이용하면 문서 객체 모델(DOM)과 이벤트에 관한 처리를 손쉽게 구현할 수 있다.
	
* 제이쿼리를 사용하는 이유
	- 제이쿼리는 주요 웹 브라우저의 구버전을 포함한 대부분의 브라우저에서 지원된다.
	- 동적으로 HTML DOM을 손쉽게 조작할 수 있으며, CSS 스타일도 간단히 적용 가능하다.
	- 생산성 있게 아주 짧고 간결하게 코딩이 가능하여 불필요한 소스를 줄일 수 있다.
	- 애니메이션 효과나 대화형 처리를 간단하게 적용할 수 있다.
	- 같은 동작을 하는 프로그램을 더욱 짧은 코드로 구현할 수 있다.
	- 다양한 플러그인과 참고할 수 있는 문서가 많이 존재한다.
	- 오픈 라이센스를 적용하여 누구나 자유롭게 이용할 수 있다.
	      
# 1. 제이쿼리 사용 방법
1. 제이쿼리 라이브러리를 다운을 받아서 사용하는 방법
	- https://code.jquery.com/ 에서 라이브러리를 다운로드 받아 프로젝트에 복사 붙여넣기한다. `<head>` 태그 안에서 다음과 같이 선언한다. 
	- `<script type="text/javascript" src="js/jquery-3.6.0.js"></script>`
		
2. 인터넷을 이용하여 파일을 연동시켜 사용하는 CDN 방식을 이용하는 방법 
	* (CDN : Content Delivery Network - 사용자가 요청한 컨텐츠를 사용자와 가장 가까운 곳에 위치한 서버에게 전달해 주는 방식)
	* `<script type="text/javascript" src="https://code.jquery.com/jquery-3.6.0.js"></script>`

# 2. 제이쿼리를 이용하여 DOM을 조작하는 방법
제이쿼리 라이브러리를 먼저 연동 후 코드를 작성한다.  


## * 2.1. 제이쿼리 동작 방법
* 형식) $("선택자").동작함수("속성", "값");
1. `JQuery(document).ready(function() {	});`
2. `JQuery(function(){ 	});`
3. `$(document).ready(function() {		});` (표준)
4. `$(function() {	});`
	
```javascript
// h2 태그의 글자색을 빨강으로 변경
$(document).ready(function(){
	$("h2").css("color", "red");
})
```
* `$` : `window.jQuery = window.$ = jQuery;`


같은 태그에 동작사항을 추가하고 싶으면 아래에 이어 작성 후,  
가장 마지막 문장 위에 세미콜론(`;`)을 붙이면 된다.    

```javascript
$(document).ready(function(){
	$("h2").css("color", "red")
	       .css("border", "3px solid blue");
	       .css("background-color", "yellow");
})
```


## 2.2. 선택자 사용 방법
1. 직접 선택자
	- 전체 선택자 `$("*")` : 모든 요소(태그)를 선택한다.
		- 예) `$("*").css("border", "1px solid red");`
	- 아이디 선택자 `$("#아이디이름")` : id 속성에 지정된 값을 가진 요소를 선택한다.
		- 예) `$("#title").css("background-color", "gray");`
	- 클래스 선택자 `$(".클래스이름")` : class 속성에 지정된 값을 가진 요소를 선택한다.
		- 예) `$(".content").css("background-color", "blue");`
	- 요소 선택자 `$("요소(태그)명")` : 지정된 요소(태그)명과 일치하는 요소들만 선택한다.
		- 예) `$("h1").css("border", "1px solid red");`
	- 그룹 선택자 `$("선택1, 선택2, ... , 선택n")` : 선택1, 선택2, ... , 선택n 에 지정된 모든 요소를 한번에 선택한다.
		- 예) `$("h1, h2").css("color", "blue");`
	    
2. 인접 관계 선택자
	- 부모 요소 선택자 `$("요소 선택").parent()` : 선택한 요소의 부모 요소를 선택한다.
		- 예) `$(".second").parent().css("border", "1px solid red");`
	- 상위 요소 선택자 `$("요소 선택").parents()` : 선택한 요소의 상위 요소들 모두를 선택한다.
	- 하위 요소 선택자 `$("요소선택  하위요소")` : 선택한 요소에 지정한 하위 요소를 선택한다.
		- 예) `$(".wrap li").css("color", "blue");`
	- 자식 요소 선택자 `$("요소선택 > 자식요소")` : 선택한 요소를 기준으로 자식 관계에 지정한 요소만 선택한다.
		- 예) `$(".wrap > li").css("color", "red");`
	- 자식 요소들 선택자 `$("요소선택").children()` : 선택한 요소의 모든 자식 요소(자식의 자식, 그 자식의 자식까지 등 그 밑의 모든 관계)를 선택한다.
	- 형제(이전) 선택자 `$("요소선택").prev()` : 선택한 요소의 바로 이전 요소를 선택한다.
		- 예) `$(".content").prev().css("color", "tomato");`
	- 형제(이전) 요소들 선택자 `$("요소선택").prevAll()` : 선택한 요소의 바로 이전 요소 모두를 선택한다.
	- 지정 형제(이전) 요소들 선택자 `$("요소선택").prevUntil("요소명")` : 선택한 요소로부터 지정한 요소 이전까지의 요소 선택한다.
	- 형제(다음) 요소 선택자 `$("요소선택").next()` : 선택한 요소의 다음 요소를 선택한다.
	- 형제(다음) 요소들 선택자 `$("요소선택").nextAll()` : 선택한 요소의 다음 요소 모두를 선택한다.
		- 예) `$(".content").next().css("border", "1px solid blue");`
		- 예) `$(".content").nextAll().css("color", "blue");`
	- 형제 요소들 선택자 `$("요소 선택").siblings()` : 선택한 요소를 제외하고 선택한 형제의 모든 요소를 선택한다. 
		- 예) `$(".content").siblings().css("color", "red");`


## 2.3. 제이쿼리 탐색 선택자
제이쿼리 탐색 선택자를 이용하면 직접 선택자를 이용해 선택한 요소 중 원하는 요소를 한 번 더 탐색해서 정확히 선택할 수 있는 장점이 있다.
* 탐색 선택자의 종류
	1. 위치 탐색자 : 선택한 요소 중 위치를 기준으로 선택한다.
	2. 속성 탐색 선택자 : 요소의 지정된 속성을 기준으로 선택한다.
	3. 콘텐츠 탐색 선택자 : 요소 내에서 콘텐츠의 포함 여부를 따져서 선택한다.
	4. 필터링 선택자 : 선택한 요소를 한 번 더 필터링하여 선택한다.

### 2.3.1. 위치 탐색자
1. 첫번째 요소 선택 : 전체 요소 중에서 첫번째 요소만 선택한다.
	* 형식) `$("요소선택:first")`, `$("요소선택").first()`
		- 예) `$(".menu li:first").css("color", "red");`
		- 예) `$(".menu li").first().css("color", "red");`
2. 마지막 요소 선택 : 전체 요소 중에서 마지막 요소만 선택한다.
	* 형식) `$("요소선택:last")`, `$("요소선택").last()`
		- 예) `$(".menu li:last").css("color", "blue");`
		- 예) `$(".menu li").last().css("color","blue");`
3. 짝수 번째(홀수 인덱스) 요소 선택 : 전체 요소 중에서 짝수 번째(홀수 인덱스) 요소만 선택한다.
	* 형식) `$("요소 선택:odd")`
	* 예) `$(".menu li:even").css("background-color", "while");`
4. 홀수 번째(짝수 인덱스) 요소 선택 : 전체 요소 중에서 홀수 번째(짝수 인덱스) 요소만 선택한다.
	* 형식) `$("요소 선택:even")`
	* 예) `$(".menu li:odd").css("background-color", "lightgray");`
5. 전체 요소 중 특정 숫자 번째 요소만 선택
	* 형식) `$("요소선택:nth-child(숫자)")`
	* 예) `$("li:nth-child(2)").css("color", "red");`
6. 전체 요소 중 특정 배수의 요소만 선택
	* 형식) `$("요소선택:nth-child(숫자n)")`
	* 예) `$("li:nth-child(3n)").css("color", "blue");`
	* 예) `$("li:nth-child(3n+1)").css("color", "green");`
	


### 2.3.2. 탐색 선택자
1. eq(index) 선택자 : 지정한 인덱스가 참조하는 요소만 선택한다.
	* 예) `$("li:eq(3)").css("background-color", "pink");`
2. lt(index) 선택자 : 지정한 인덱스보다 작은(less then) 요소만 선택한다.
	* 예) `$("li:lt(3)").css("background-color", "yellow");`
3. gt(index) 선택자 : 지정한 인덱스보다 큰(grater then) 요소만 선택한다. 
	* 예) `$("li:gt(3)").css("background-color", "skyblue");`



### 2.3.3. 속성 탐색 선택자 
속성 탐색 선택자는 요소의 지정된 속성을 기준으로 선택한다.
1. 요소[속성] : 속성이  있는 요소 가져오기 .
	* 예) `$("a[title]").css("border", "1px solid red");`
2. 요소[속성=값] : 속성과 값이 일치하는 요소 가져오기.
	* 예) `$("a[href='http://www.naver.com']").css("background-color", "pink");`
3. 요소[속성^=값] : 값으로 시작하는 요소 가져오기.
	* 예) `$("a[href^='mailto']").css("background-color", "aqua");`
4. 요소[속성$=값] : 값으로 끝나는 요소 가져오기.
	* 예) `$("a[href$='net']").css("background-color", "lightgray");`
5. 요소[속성*=값] : 값을 포함하는 요소 가져오기.
	* 예) `$("a[href*=daum]").css("border", "1px solid red");`
6. `요소[속성=값][속성=값]` : and 조건으로 조건 2개의 속성과 값을 모두 만족하는 요소 가져오기.
	* 예) `$("a[href^='mailto'][href$='net']").css("background-color", "green");`



### 2.3.4. 요소 조작 메서드 
요소 조작 메서드는 요소를 생성, 복사, 삭제, 속성 변환과 관련된 메서드를 제공한다.
#### 1. 속성 조작 메서드
* `html()` : 선택한 요소에 포함되는 하위 요소를 불러오거나 새 요소로 바꿀 때 사용한다.

```javascript
// h1태그의 요소내용을 불러와 alert 창으로 출력
alert($("h1").html());	

// h1태그의 요소를 "" 안에 작성한 내용으로 변경
$("h1").html("<a href='#'>HTML 메서드</a>");	
```


* `text()` :  선택한 요소 내의 텍스트를 불러오거나 텍스트를 바꿀 때 사용한다.

```javascript
// h1태그의 텍스트를 불러와 alert 창으로 출력
alert($("h1").text());

// h1태그의 텍스트 내용을 "텍스트 메서드"로 변경
$("h1").text("텍스트 메서드");
```



* `attr("속성")` / `attr("속성", "값")` : 선택한 요소에 새 속성을 추가하거나, 기존의 속성을 변경할 때 사용한다.
```javascript
$(".wrap img").attr("width", "200");
$(".text").text($(".wrap img").attr("src"));
```

* `removeAttr("속성")` : 선택한 요소에서 기존의 속성을 삭제할 때 사용한다.
```javascript
$(".wrap img").removeAttr("width");
``` 


* `addClass()` : 선택한 요소에 클래스 선택자를 생성할 때 사용한다.
```javascript
$("#p1").addClass("p1_class");
```

* `removeClass()` : 선택한 요소에 지정된 클래스 선택자를 삭제할 때 사용한다.
```javacsript
$("#p1").removeClass("p1_class");
```
	
	
* `val()` / `val(값)` : 입력 요소에 있는 value 값을 가져오거나 변경할 때 사용한다.

```javascript
// id="user_name" 인 요소의 value값을 alert로 출력
alert($("#user_name").val());

// id="user_name" 인 요소의 value값을 id="my_name"인 요소에 지정
$("#my_name").val($("#user_name").val());
```





#### 2. 수치 조작 메서드




#### 3. 요소 편집 메서드
요소 편집 메서드는 선택한 요소를 복제하거나 새 요소를 생성하는 메서드이다.  
복제하거나 새로 생성한 요소를 의도한 위치로 삽입하고 선택한 요소를 삭제하는 기능을 한다.  

* `before()` : 선택한 요소 이전 위치에 새 요소를 추가하는 메서드.
	* 형식) `형식) $("요소선택").before("새 요소")`
* `after()` : 선택한 요소 다음 위치에 새 요소를 추가하는 메서드.
	* 형식) `$("요소선택").after("새 요소")`

```javascript
// class="myList" 앞에 새로운 내용 추가
$(".myList").before("<li>새로운 내용 추가1</li>");

// class="myList" 뒤에 새로운 내용 추가
$(".myList").after("<li>새로운 내용 추가2</li>");
```




* `append()` : 선택한 요소의 마지막 위치에 새 요소를 추가하는 메서드.
	* 형식) `$("요소선택").append("새 요소")`
* `appendTo()` : 선택한 요소의 마지막 위치에 새 요소를 추가하는 메서드.
	* 형식) `$("새 요소").appendTo("요소 선택")`
* `prepend()` : 선택한 요소의 맨 앞 위치에 새 요소를 추가하는 메서드.
	* 형식) `$("요소선택").prepend("새 요소")`
* `prependTo()` : 선택한 요소의 맨 앞 위치에 새 요소를 추가하는 메서드.
	* 형식) `$("새 요소").prependTo("요소선택")`


```javascript
// class="myList"의 앞과 뒤에 각각 새로운 내용 1, 2를 추가
$(".myList").append("<li>새로운 내용1</li>");
$(".myList").prepend("<li>새로운 내용2</li>");

// 이렇게 작성해도 된다.
$("<li>새로운 내용1</li>").appendTo(".myList");
$("<li>새로운 내용2</li>").prependTo(".myList");
```



* `insertBefore()` : 선택한 요소의 이전 위치에 새 요소를 추가하는 메서드.
	* 형식) `$("새 요소").insertBefore("요소선택")`
* `insertAfter()` : 선택한 요소의 다음 위치에 새 요소를 추가하는 메서드.
	* 형식) `$("새 요소").insertAfter("요소선택")`
* `clone()` : 선택한 요소를 복사하는 메서드.
	* 형식) `$("요소선택").clone(true or false)`
	- `true` : 하위 요소까지 모두 복사.
	- `false` : 선택한 요소만 복사.
	

```javascript
// class="myList" 이전 위치에 새로운 내용 추가
$("<li>새로운 내용</li>").insertBefore(".myList");

// class="myList"를 복사해서 my_clone이라는 변수에 저장
let my_clone = $(".myList").clone();

// 복사한 요소를 class="myList" 다음 위치에 추가
$(my_clone).insertAfter(".myList");
```




* `empty()` : 선택한 요소의 하위 내용들을 모두 삭제하는 메서드. 선택한 요소 자체는 삭제되지 않는다.
	* 형식) `$("요소선택").empty()`
* `remove()` : 선택한 요소를 삭제하는 메서드. 
	* 형식) `$("요소선택").remove()`
	
```javascript
// class="line_1"인 요소의 하위 내용만 삭제. 
$(".line_1").empty();

// class="line_2"의 요소를 모두 삭제. 아예 사라진다.
$(".line_2").remove();
```

	



* `replaceWith()` : 선택된 요소만 새 요소로 교체하는 메서드.
	* 형식) `$("요소선택").replaceWith("새 요소")`
* `replaceAll()` : 선택 요소 전체를 새 요소로 교체하는 메서드.
	* 형식) `$("요소선택").replaceAll("새 요소")`

```javascript
// <h2>태그로 작성된 모든 내용을 <h3>태그로 작성된 내용으로 교체
$("h2").replaceWith("<h3>replaceWith() 메서드</h3>");

// <p>태그로 작성된 모든 내용을 <h2> 태그의 "replaceAll"으로 내용 변경
$("<h2>내용변경</h2>").replaceAll("p");
```

	
