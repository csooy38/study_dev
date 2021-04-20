# CSS(Cascading Style Sheet)
HTML이 웹 페이지의 "뼈대"라고 한다면 CSS는 "살"이라고 할 수 있다. 즉, HTML이 웹 페이지의 정보를 표현한다면, CSS는 HTML을 좀 더 보기 좋게 디자인하는 역할을 한다.	

* CSS 특징
	* Cascading Style Sheet
	* HTML 문서에 스타일(디자인)을 적용하는 언어
	* CSS 사용 방법 
		* 인라인 방식(태그에 직접 적용) : 번거로우므로 사용빈도가 낮다.
		* head 영역 선언
		* 외부 파일(*.css) 링크
	 
1. CSS 형식 : 선택자 { 속성: 값; }
2. 선택자 : body 태그에서 선언한 태그
3. 하위태그 지정 : 상위태그 하위태그 { 속성: 값; }
4. 둘 이상의 요소에 같은 스타일을 적용하는 방법 : 태그1, 태그2 { 속성: 값; }
	
## link 
현재 문서와 외부 리소스(*.css) 파일과의 관계를 명시.
* rel="stylesheet" : ```<link>``` 태그로 연결하는 파일이 외부에 있는 스타일시트 파일이란 뜻을 가지고 있다.
* href : 이 속성은 링크된 리소스의 url 경로를 참고한다.
* 외부에 스타일시트 파일로 선언하고 사용할 때의 장점은 모든 HTML 파일에 동일하게 적용이 가능하다는 점이다.

#### 예제 1 CSS 사용 방법 : 외부 파일(*.css) 링크 방식
```html
<head>
<link rel="stylesheet" href="css/main.css"> // 헤더 안에서 선언
</head>

<body>
<p>link 방식으로 스타일 지정하기</p>
</body>
```

```css
// html 파일에서 선언한 링크 "css/main.css" 주소에 파일을 만들었다.

// 링크된 html의 <p>태그에 적용되는 css
p {
	color: blue; 		/* 글자 색상 */
	font-size: 20px; 	/* 글자 크기 */
	font-weight: bold;  /* 글자 굵기 */
	text-align: center; /* 글자 위치 */
	font-family: 궁서체   /* 글꼴(글자체) */
}

// 링크된 html의 <body> 태그에 적용되는 css
body {		
	background-color: pink;	/* 문서 전체 배경 색상 변경 */
	
	/* 배경 이미지를 지정하는 속성 */
	background-image: url("../images/beauty.jpg");
	
	/* 배경 이미지를 한 번만 표시하는 속성 */
	background-repeat: no-repeat;
	
	/* 배경 이미지를 웹 브라우저의 가운데 배치하는 속성 */
	background-position: center;
}

```
엄청난 게 만들어졌다. 정말 beauty한 화면이다.    
헤더 밑에서 선언한 링크(css/main.css)의 코드에 따라 p태그와 body태그의 디자인이 결정되었다.    
<img src="./images/210420/34.png">  


#### 예제 2 CSS 사용 방법 : head 영역 선언 방식

```<head>``` 영역에서 원하는 태그의 스타일을 지정한다.

* 하위 태그 지정 : '상위태그 하위태그 { 속성: 값;}'
* 둘 이상의 요소에 같은 스타일을 적용하는 방법 : 태그1, 태그2 { 속성: 값; }

```html
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<style type="text/css">

	ul li{ // ul태그의 하위 태그인 li태그의 스타일 정의 
		font-size: 18px;
		font-weight: bold;
		color: red;
	}
	
	h1, h2 { // 둘 이상의 태그를 한 번에 스타일 정의
		font-style: italic;
		font-weight: bold;
		text-decoration: underline; /* 텍스트에 밑줄 적용*/
	}
	
</style>
</head>
<body>

	<h3>음료 종류</h3>
	
	<hr>
	
	<ul>
		<li>콜라</li>
		<li>사이다</li>
		<li>환타</li>
		<li>생과일주스</li>
	</ul>
	
	<h1>나보다 동료의 생각이 더 옳을 수 있다는 믿음을 가집니다.</h1>	
	<h2>Trust to Trust</h2>

</body>
```
  
```<head>```에서 정의한 스타일이 li, h1, h2 태그에 각각 적용되어 출력된다.     
<img src="./images/210420/35.png">  


## 선택자의 종류
* 태그 선택자 : 특정 태그를 사용한 요소에 스타일 적용.
* id 선택자 : 특정 부분에 스타일 적용.
	* 웹 문서에서 고유한 식별자를 정의할 때 사용한다.
	* 대체적으로 큰 골격의 이름에 사용하는 것이 좋다.
	* 같은 id 이름을 중복해서 사용하지 못한다. 하나의 요소에 여러 개의 id를 동시에 사용하지 못한다. 
	* 대체적으로 상단 헤더, 왼쪽 메뉴, 가운데 컨텐츠 영역, 하단 footer 영역에 사용한다.
	* 예) id="title" ==> #title
* class 선택자 : 특정 부분에 스타일 적용.
	* 같은 클래스의 이름을 여러 요소에 중복하여 적용할 수 있다.
	* 주로 class 선택자를 많이 사용한다.
	*  예) class="main_text" ==> .main_text

#### 예제 3 id 선택자 & class 선택자
id 선택자는 헤더영역에서 '#'을 선택자 이름 앞에, class 선택자의 이름은 헤더영역에서 '.'을 선택자 이름 앞에 붙여서 선언한다.
* id 선택자는 중복해서 사용할 수 없음에 주의한다.
* class 선택자는 중복해서 사용가능하므로 넓은 영역에서 사용 가능하다.
```html
<head>
<style type="text/css">

	#title { // id 선택자
		color: blue;
	}
	
	.main_text { // class 선택자
		font-weight: bold;
		font-size: 20px;
		color: red;
	}
	
</style>
</head>
<body>

	// id 선택자 title 적용
	<h1 id="title">제목1</h1>
	<h1>제목2</h1>
	<hr>
	
	// class 선택자 main_text 적용
	<p class="main_text">본문1</p>
	<p>본문2</p>
	<p class="main_text">본문3</p>
	<p>본문4</p>
	<p class="main_text">본문5</p>


</body>
```

'제목2'는 id 선택자 title의 스타일이 적용되었으며,
'본문1', '본문3', '본문4'는 class 선택자 main_text의 스타일이 적용되었다.    

<img src="./images/210420/36.png">  


## 블록레벨 요소와 인라인 레벨 요소
1. 블록 레벨 요소
	* 주요 태그 : div, hn, p
	* 사용 가능한 최대 가로 너비를 사용한다.
	* 크기를 지정할 수 있다.
	* (default) width:100%, heigh:0%로 시작
	* 수직으로 쌓인다.
	* margin, padding의 속성에 상하좌우로 사용이 가능하다.
	* 레이아웃을 설정하는 용도로 사용이 된다.
			
2. 인라인 레벨 요소
	* 주요 태그 : span, img
	* 필요한 만큼만의 너비를 사용한다.
	* 크기를 지정할 수 없다.
	* (default) width:0%, height:0%로 시작
	* 수평으로 쌓인다.
	* margin, padding의 속성에 상하좌우로 사용이 불가능하다.
	* 텍스트를 설정하는 용도로 사용이 된다.
	
### div 태그
특별한 의미가 없는 태그로, 주로 구분 용도로 사용된다. 즉, 영역 설정 용도. 

#### 예제4 블록레벨요소 & 인라인 레벨 요소
	
```
	<p>블록 레벨 요소 : p태그</p>
	<span>인라인 레벨 요소 : span</span>
```
겉보기엔 별다를 게 없어보이는 p태그와 span 태그로 작성한 문장이지만    
<img src="./images/210420/37.png">  
개발자모드(F12)로 보면 p태그는 작성하지 않은 가로 넓이 끝까지 블록이 지정되어 있으며,    
<img src="./images/210420/38.png">
반면에 span 태그는 작성한 영역만 소숫점 단위로 너비가 지정되어 있음을 알 수 있다.
<img src="./images/210420/39.png">    
	

	


	
	
	