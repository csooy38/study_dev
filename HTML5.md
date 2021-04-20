# 웹 표준 
W3C에서 제안한 웹 관련 표준을 의미한다. 웹에서 표준으로 사용되는 기술이나 규칙을 의미하며, 이는 특정 브래우저에서만 사용되는 비 표준화된 기술은 배제하고, W3C의 토론을 통해서 나온 권고안을 사용하는 것을 말한다.  문서의 구조(HTML5)와 표현(CSS3), 그리고 동작(JavaScript, JQuery)을 구분해서 사용하는 것을 뜻한다.
 
* HTML5 : 웹 문서의 구조 작성
* CSS3 : 웹 문서의 디자인 적용(담당)
* JQuery : 웹 문서의 동적인 기능 담당 (JavaScript 최신 버전)
    
    
# HTML5와 CSS(Cascading Style Sheet)를 배우는 이유
	
1. 게시판이나 블로그를 좀 더 자유롭게 꾸밀 수 있음.
2. 웹 사이트 제작을 위해서는 HTML5와 CSS3가 필수적임.
3. 인터렉티브한 웹 사이트를 만들 수 있음.
4. 플래시 플러그(가장 큰이유)인이 없이도 멀티미디어 콘텐츠 제작이 가능.
5. 반응형 웹 사이트를 만들 수 있음.
6. 모바일용 앱을 만들 수 있음.
 	
[참고사이트] : http://w3schools.com <a href="http://w3schools.com">[사이트 이동]</a>
	
 
    
# HTML5의 태그
* ```<b>``` : 볼드체.
* ```<strong>``` : 볼드와 같은 역할.
* ```<mark>``` : 글자 배경색을 노란색 처리. style="background-color:yellow; 와 동일.

```html
<b>볼드체</b> <br>
<strong>스트롱</strong> <br>
<mark>mark 적용</mark> <br>
```
적용하면 아래와 같이 출력된다.    
<b>볼드체</b><br>
<strong>스트롱</strong><br>
<mark>mark 적용</mark><br>


### span 태그 ```<span> </span>```
span 태그 안에 폰트의 스타일을 사전에 정의한 후 호출하여 사용한다. 
* 일반적으로 타이틀 태그 아래에서 스판 태그를 선언한다.
* 일괄적인 스타일 변경 시 유용하다.

```html
<title>타이틀</title>
<style type="text/css">

	span {
		font-size: 20px;
		font-weight: bold;
		color: red;
	}

</style>
</head>
<body>

	<p>이제 <span>웹 표준</span>의 역할은 아주 <span>중요</span>합니다.</p>
	
</body>
```

- 코드 실행시 다음과 같이 출력된다.    
<img src="./images/210420/01.png">

- span 태그 내의 color: 를 color: blue; 로 변경시 다음과 같이 출력된다.    
<img src="./images/210420/02.png">


## 용어를 정의하고 용어를 설명하는 태그
dl 태그 안에 dt 태그와 dd 태그가 존재한다.
- dt 태그 : 용어
- dd 태그 : 용어를 설명하는 태그. dt 태그보다 들여쓰기가 된다.

```html
<h3>용어 정의 목록</h3>
	 <dl>
	 	<dt><b>키보드</b></dt>
	 		<dd>컴퓨터에 문자를 입력하는 장치이다.</dd>
	 
	 	<dt>마우스</dt>
	 		<dd>화면의 커서를 요리조리 움직이고 버튼을 눌러서 선택하는 장치이다.</dd>
	 
	 	<dt>노트북</dt>
	 		<dd>휴대하면서 영화를 보거나 웹 서핑이 가능한 장치이다.</dd>
	 		<dd>작고 가벼운 컴퓨터이다.</dd>
	 </dl>
```
* 코드 실행시 다음과 같이 출력된다.
<img src="./images/210420/03.png">


## form 태그 (☆)
사용자에게 입력을 받을 데이터 양식을 설정하는 태그.
		
## input 태그 속성
- autocomplate : 사용자가 이전에 입력한 값으로 자동완성기능을 사용할 것인지 여부. on(default) or off

- autofocus : 페이지가 로드될 때 자동으로 포커스를 이동할지 여부 확인.

- checked : 양식이 선택되었음을 표시할 지 여부 확인. type 속성 값이 radio, checkbox인 경우만 사용 가능.

- disabled : 양식을 비활성화할지 여부 확인.

- max : 지정 가능한 최대값 설정. type 속성이 number일 경우만 사용 가능. min 속성보다 큰 값만 허용.

- min : 지정 가능한 최소값 설정. type 속성이 number일 경우만 사용 가능. max 속성보다 작은 값만 허용.

- maxlength : 입력 가능한 최대 문자 수 설정. type 속성 값이 text, email, password, tel, url일 경우만 허용.

- multiple : 둘 이상의 값을 입력할 수 있는지 여부 설정. type 속성 값이 email, file일 경우만 허용 가능. email 경우 ,로 구분.

- name : 양식의 이름을 지정.

- placeholder : 사용자가 입력할 값의 힌트 설정. type 속성 값이 text, search, tel, url, email일 경우만 허용.

- readonly : 수정 불가능한 읽기 전용 설정.

- step : 유효한 증감 숫자 간격의 설정. type 속성 값이 number, range일 경우만 허용.

- src : 이미지의  url 설정. type 속성 값이 image일 경우만 허용.

- alt : 이미지의 대체 텍스트 설정. type 속성 값이 image일 경우만 허용. 
                   
- type : 입력 받을 데이터의 종류 설정. 아래에 type에 대한 내용 기재.

- value : 양식의 초기 값 설정.       
		        
		        
## 데이터의 종류(type)의 값(value)
- button : 일반 버튼. onClick 속성은 자바스크립트 함수를 호출할 때 사용.

- checkbox : 체크 박스. 여러 개 중 동시에 선택, 비선택 가능. 배열로 값이 전달됨.

- color : 색상 선택. IE 지원 불가.

- date : 날짜 선택. IE 지원 불가. 

- email : 이메일 선택.  
         
- file : 파일 선택.

- hidden : 보이지 않지만 전송할 양식 설정. 양식에는 보이지 않지만 값이 전달될 때는 값이 전달되는 양식.

- image : 이미지 제출 버튼.

- number : 숫자 선택. IE 지원 불가.

- password : 비밀번호 입력 가능. 입력된 내용이 안 보이는 형식.

- radio : 라디오 버튼. 여러 개 중 하나만 선택됨.

- range : 범위 컨트롤 지정. max, min, step, value(기본값) 속성 사용 가능. 

- reset : 초기화 하는 버튼. 해당 form 범위 내의 모든 양식 값이 초기화됨.

- search : 검색 기능.

- submit : 제출 버튼 기능. form 태그 속성 중 action 페이지로 해당 값들을 전송.

- tel : 전화번호 입력 기능. 

- text : 일반 텍스트 입력 기능.

- url : 절대 url 입력 기능.



## 시맨틱 태그의 태그 종류
- 시맨틱(semantic) : 의미론적인의 뜻을 가지고 있음. 즉, 의미가 있는 태그라는 뜻.
- HTML5에 도입된 시맨틱 태그는 개발자와 브라우저에게 의미가 있는 태그를 제공함.

1. header 태그 : 브라우저의 상단에 존재하는 태그. 회사의 로고, 회원가입, 로그인 버튼들을 나타내는 태그.

2. footer 태그 : 브라우저의 하단에 존재하는 태그. 일반적으로 저작권, 회사의 주소에 대한 정보를 나타내는 태그.

3. article 태그 : 일반적으로 웹 문서의 본문에 해당하는 내용을 작성하는 태그.

4. section 태그 : 문서의 일반적인 영역을 설정하는 태그. article 태그 사용이 가능함.

5. aside 태그 : 문서의 별도 컨텐츠 영역, 보통 광고나 기타 링크 등의 사이드 바를 설정하는 태그.

6. nav 태그 : 다른 페이지 링크를 제공하는 영역. 보통 메뉴(home, content 등등) 설정 시 사용함.