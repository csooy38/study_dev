# JSP

# 웹 프로그래밍
- 웹 프로그래밍이란? ==> 웹 어플리케이션을 만드는 행위.
- 웹 어플리케이션이란? ==> 웹을 기반으로 동작하는 프로그램을 말한다.
- 웹 이란? ==> 인터넷 서비스의 형태를 말한다.
- 인터넷이란? ==> 하나 이상의 네트워크가 연결되어 있는 형태를 말한다.
- 웹 서버? ==> 각 클라이언트에게 서비스를 제공하는 컴퓨터를 말한다. 웹 서버는 정적인 컨텐츠(HTML, CSS, JS)를 제공하는 서버.
- 웹 어플리케이션 서버(WAS)? ==> DB 조회나, 어떤 로직을 처리해야 하는 동적인 컨텐츠를 제공하는 서버를 말한다. 
- 클라이언트? ==> 네트워크로 서버에 접속한 후 서버로부터 서비스를 제공받는 컴퓨터를 말한다.
- HTTP 프로토콜? ==> Hyper Text Transfer Protocol의 약자로 www 서비스를 제공하는 통신규약을 말함. HTML을 비롯해서 이미지, 동영상, XML 문서 등 다양한 데이터를 주고 받을 때 사용하는 일종의 규칙임. 즉, 웹 서버와 클라이언트는 이 프로토콜을 이용해서 정보를 주고 받는다.
- 동적 웹 프로그래밍? ==> 클라이언트의 요청이 있을 때마다 데이터베이스에 접근해서 실시간 정보를 클라이언트에게 제공하는 기능을 처리하는 방식을 말한다.


# CGI 방식과 어플리케이션 서버 방식의 차이점
- 동시에 여러 명의 접속자가 접속을 하여 프로그램을 실행하는 경우
	* CGI 방식은 클라이언트의 요청에 독립된 프로세스를 생성하기 때문에 점유하는 메모리가 많아져 시스템의 부하를 주게 된다. 요청이 발생할 때마다 매번 메모리에 프로그램을 로딩하기 때문에 동시 접속자 수가 많아질수록 이에 비례하여 프로그램 실행을 위한 메모리도 증가하게 된다.
		* 주로 사용되는 언어 : C++
	* 어플리케이션 서버 방식은 동시에 여러 명의 접속자가 동일한 프로그램의 처리를 요청하여도 한 개에 해당하는 메모리만 사용하기 때문에 즉, 스레드 방식으로 처리하기 때문에 CGI 방식에 비해서 메모리 사용량이 적다.
		* 주로 사용되는 언어 : ASP, PHP, JSP 


---------------------------------------------------------
# Servlet 서블릿
- 서버 쪽에서 실행되면서 클라이언트의 요청에 따라 동적으로 서비스를 제공하는 자바 클래스. 
- 서블릿은 자바로 작성되어 있으므로 자바의 일반적인 특징을 모두 가지고 있다.
- 서블릿은 서버에서 실행되다가 웹 브라우저에서 요청을 하면 해당 기능을 수행한 후 웹 브라우저에 결과를 전송한다.
- 서버에서 실행이 되기 때문에 보안과 관련된 기능도 훨씬 안전하게 수행이 가능하다.


## 1. Servlet Life Cycle(서블릿 생명 주기)
* `init()` : 단 한 번만 호출된다.
	- 서블릿이 서비스하기 위해 필요한 초기화 작업을 수행을 한다.  
* `service()` : `init()` 메서드가 `service()` 메서드를 호출한다.
	- 사용자의 요청에 따라 스레드 단위로 실행되는 메서드. (여러번 실행)
	- 각각 `service()` 메서드를 통해서 `doGet()`, `doPost()` 메서드가 호출된다.
	- 파라미터인 HttpServletRequest와 HttpServletResponse를 통해서 사용자의 요청을 처리한다.
* `destroy()` : 서블릿이 종료 요청이 오면 한 번만 호출되는 메서드.
	- 서블릿이 종료되면서 정리할 작업이 있으면 `destroy()` 메서드를 오버라이딩(재정의) 해서 구현한다.
                 
                                    
## 2. Sevlet 동작 과정
- 클라이언트가 요청을 하면 요청하는 서블릿이 메모리에 로딩이 되어 있는지 확인한다.
- 최초의 요청이면 `init()` 메서드를 호출하여 요청하는 클래스의 인스턴스(객체)를 메모리에 로딩한다.
- 그런 다음 `doGet()`이나 `doPost()` 메서드를 호출하여 서비스를 한다.
- 클라이언트가 다시 동일한 서블릿을 요청을 하면 톰캣은 요청하는 서블릿이 메모리에 로딩이 되어 있는지 확인한다.
- 이번에는 메모리에 로딩이 되어 있는 것이 확인이 되므로 바로  `doGet()`이나 `doPost()` 메서드를 호출한다.
    
    
## 3. JSP에서 사용되는 동작 방식 - 2가지
1. Servlet 방식
	- 웹 개발을 위한 표준이 되는 클래스.
	- 웹 브라우저의 요청을 스레드 방식으로 처리하는 기술을 말한다..
	- 서버 쪽에서 실행되면서 클라이언트의 요청에 따라 동적으로 서비스를 제공하는 자바 클래스.
	- 처리해야 할 일들을 기술하는 곳.
	- 서블릿은 일반 자바 프로그램과 다르게 독자적으로 실행되지 못하고 톰캣과 같은 서버에서 실행된다.
	- 서블릿의 특징.
		* 서버 쪽에서 실행되면서 기능을 수행한다.
		* 기존의 정적인 웹 프로그램의 문제점을 보완하여 동적인 여러 가지 기능을 제공한다.
		* **스레드 방식으로 실행된다.** (중요!!)
		* 클라이언트의 요구를 처리하는 기능은 최초 한 번만 메모리로 로딩된다.
		* 클라이언트가 동일한 기능을 요구하면 기존에 사용한 기능을 재사용.
		* 자바로 만들어져서 자바의 특징(객체 지향)을 가지고 있다.
		* 보안 기능을 적용하기 쉽다.
		* 웹 브라우저에서 요청 시 기능을 수행한다.
	- 즉, 서블릿의 기본 기능 - 3가지
		1) 클라이언트로부터 요청을 받는다.
		2) 데이터베이스 연동과 같은 비지니스 로직을 수행한다.
		3) 처리된 결과를 클라이언트에게 돌려준다.
2. JSP 방식    
	- Java Server Page의 약자로 자바 Servlet 기술을 확장시켜 웹 환경  상에서 100% 순수한 자바만으로 개발하기 위한 기술을 말한다. Servlet을 한 차원 더 확장시킨 버전.
	- 동적인 페이지를 생성하기 위한 서버 측 스트립트 언어.
	- 디자이너 입장에서 화면의 수월한 기능 구현과 개발 후 화면의 편리한 유지관리를 목적으로 도입.

## 4. 서블릿의 요청과 응답
* 요청과 관련된 API : javax.servlet.http.HttpServletRequest 인터페이스
* 응답과 관련된 API : javax.servlet.http.HttpServletResponse 인터페이스
1. 클라이언트가 서블릿에 요청을 하면 먼저 톰캣 서버가 해당 요청을 받는다.
2. 그런 다음 사용자의 요청이나 응답에 대한 HttpServletRequest 객체와 HttpServletResponse 객체를 만들게 된다.
3. 그리고 난 후 Servlet의 doGet() 메서드나 doPost() 메서드를 호출하면서 이 객체들을 전달한다.
4. 톰캣이 사용자의 요청에 대한 정보를 모든 HttpServletRequest 객체의 속성으로 담아 메서드로 전달한다. 따라서 각 HttpServletRequest에서 제공하는 메서드들은 매개변수로 넘어온 객체들을 이용하여 사용자가 전송한 데이터를 받아오거나 응답을 할 수 있는 것이다.

  
## 5. 서블릿에서 클라이언트의 요청을 얻는 방법(중요!!)
- HttpServletRequest 클래스에서 `<form>` 태그로 전송된 데이터를  받아 오는데 사용되는 메서드.
	* `getParameter(String name)` => `<form>` 태그의 `name` 속성에 들어간 변수명을 받아서 사용한다. 반환형은 String 타입.
 	* `getParameterValues(String name)` ==> `<form>` 태그의 같은 `name`에 대하여 여러 개의 값을 얻을 때 사용한다. 반환형은 String[] 배열 타입.
 	
#### [예] 체크박스 데이터를 요청할 때
체크박스는 중복으로 선택이 가능하므로 입력한 데이터 값도 복수가 될 수 있다. 따라서 체크박스 데이터를 받아올 때는 배열로 받아와야 한다.   
이 때 `getParameterValues()`를 사용한다. 반환형은 String[] 배열 타입이다.     

```java
// 1단계 : 페이지에서 넘어온 데이터들을 처리해 주자.

String[] major = request.getParameterValues("major");
	
// 2단계 : 웹 브라우저에 요청한 결과를 화면에 보여 주자.
out.println("전공과목 : ");
	
// 배열로 저장된 전공과목 출력
for(int i=0; i<major.length; i++) {
	out.println(major[i] + "&nbsp;&nbsp;&nbsp;");
}
```
            
            
## 6. 서블릿에서 요청 받은 내용을 처리하여 클라이언트에 보내는 방법.
1. HttpServletResponse 객체를 이용하여 응답한다.
2. `doGet()`이나 `doPost()` 메서드 안에서 처리한다.
3. javax.servlet.http.HttpServletResponse 객체를 이용한다.
4. `setContentType()` 메서드를 이용하여 클라이언트에게 전송할 데이터의 종류(MIME-TYPE)를 지정한다.
5. 클라이언트(웹 브라우저)와 서블릿의 통신은 자바 I/O의 스트림을 이용한다.

  
## 7. 웹 브라우저에서 서블릿으로 데이터를 전송하는 방법 
1. get 방식
2. post 방식


### 7.1. get 방식
- 서블릿에 데이터를 전송할 때는 데이터가 url 뒤에 name=value 형태로 전송된다.
- 여러 개의 데이터를 전송할 때는 '&'로 구분하여 전송.
- 보안이 취약하다.
- 전송할 수 있는 데이터는 최대 255자.
- 기본 전송 방식이고 사용이 쉽다.
- 웹 브라우저에 직접 입력해서 전송할 수도 있다.
- 서블릿에서는 `doGet()` 메서드에서 전송된 데이터를 처리한다.   


#### [예] get 방식

```jsp
// jsp 파일 작성

<body>
	<h2>두 수 더하기</h2>
	<%-- 입력된 데이터를 서블릿 매핑 이름이 adder인 서블릿으로 전송하라는 의미 --%>
	<form action="adder" method="get">
		<%-- 텍스트 박스에 입력된 첫번째 숫자를 num1이라는 변수에 저장하여
			서블릿으로 전송하라는 의미 --%>
		<p>첫번째 수 : <input type="text" name="num1"></p>
		<p>두번째 수 : <input type="text" name="num2"></p>
		<input type="submit" value="계산">
	</form>
</body>    
``` 
 
```java
// servlet 파일 작성 
protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	// form 태그에서 method="get"인 경우 실행되는 메서드
	// request : 첫번째 매개변수. 사용자(client)의 요청에 대한 정보를 처리.
	// response : 두번째 매개변수. 요청 정보에 대한 처리 결과를 클라이언트에 응답 처리.
	
	// 1단계 : 클라이언트에서 넘어온 데이터를 받기 - 사용자가 전송한 데이터를 받기
	int num1 = Integer.parseInt(request.getParameter("num1"));
	int num2 = Integer.parseInt(request.getParameter("num2"));
	
	// 응답 시 한글 처리
	response.setContentType("text/html; charset=UTF-8");
	
	// 2단계 : 처리한 결과를 클라이언트 웹 브라우저에 출력하는 작업.
	PrintWriter out = response.getWriter();
	
	out.println("<html>");
	out.println("<head></head>");
	out.println("<body>");
	out.println("<h1>두 수의 합 >>> " + (num1 + num2) + "</h1>");
	out.println("</body>");
	out.println("</html>");
}
```


<p align="center"><img src="../images/210503/01.png"></p>
<p align="center"><img src="../images/210503/02.png"></p>
    


### 7.2. post 방식
- 서블릿에 데이터를 전송할 때는  TCP/IP 프로토콜 데이터의 head 영역에 숨겨진 채 전송된다.
- 보안에 유리한다.
- 전송 데이터의 용량이 무제한.
- 처리 속도가 get 방식보다 느리다.
- 서블릿에서는 doPost() 메서드에서 전송된 데이터를 처리한다.
	

#### [예] post 방식     
```jsp
// jsp 작성

<h2>두 수 더하기(web.xml 등록)</h2>
<%-- 입력된 데이터를 서블릿 매핑 이름이 adder인 서블릿으로 전송하라는 의미 --%>
<form action="adder1" method="post">
	<%-- 텍스트 박스에 입력된 첫번째 숫자를 num1이라는 변수에 저장하여
		서블릿으로 전송하라는 의미 --%>
	<p>첫번째 수 : <input type="text" name="num1"></p>
	<p>두번째 수 : <input type="text" name="num2"></p>
	<input type="submit" value="계산">
</form>
```

```xml
// web.xml 작성

<servlet>
<servlet-name>abc</servlet-name>
<servlet-class>com.sist.Adder1Servlet</servlet-class>
</servlet>
<servlet-mapping>
<servlet-name>abc</servlet-name>
<url-pattern>/adder1</url-pattern>
</servlet-mapping>
</web-app>
```

     
```java
// servlet 작성

protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	// method="post"인 경우 처리하는 메서드
	
	// method="post"인 경우에는 한글 깨짐 현상 발생.
	// 한글이 깨지지 않게 설정을 해야 한다.
	request.setCharacterEncoding("UTF-8");
	
	// 1단계 : 클라이언트에서 넘어온 데이터를 받자. - 사용자가 전송한 데이터 받기
	int su1 = Integer.parseInt(request.getParameter("num1"));
	int su2 = Integer.parseInt(request.getParameter("num2"));
	
	// 응답 시 한글 처리
	response.setContentType("text/html; charset=UTF-8");
	
	// 2단계 : 처리된 내용을 응답하여 웹 브라우저에 출력하는 작업
	PrintWriter out = response.getWriter();
	
	out.println("<html>");
	out.println("<head></head>");
	out.println("<h1>두 수의 합 >>> " + (su1 + su2) + "<h1>");
	out.println("</body>");
	out.println("</html>");
}
```

주소창에 데이터가 표시되지 않아 보안에 유리하다.  
<p align="center><img src="../images/210503/03.png></p>
<p align="center"><img src="../images/210503/04.png"></p>

     
-------------------------------------
### * JSP 주석
* `<%-- --%>` : JSP의 주석. 소스코드 보기에 노출되지 않는다.

```html
<!-- HTML 주석 -->
	
<%-- JSP 주석 : 소스코드보기에 노출되지 않는다. --%>
```

<p align="center"><img src="../images/210503/00.png"></p>





### * 한글 인코딩
* `method="post"` 일 때는 반드시 한글 인코딩 처리를 해야 **입력한 값이 한글일 때** 정상적으로 출력된다.

```java
request.setCharacterEncoding("UTF-8");
```

* **페이지에 작성된 한글**을 정상적으로 출력하기 위해선 다음 코드를 사용한다. 

```java
response.setContentType("text/html; charset=UTF-8");
```



---------------------------------------------
# JSP 

## 1. 지시어(디렉티브) 
디렉티브는 JSP 페이지에 대한 설정 정보를 지정하는 공간을 의미한다.
1. `<%@ page %>` : JSP 페이지에 대한 정보를 지정하는 공간.
	- 어떻게 처리해야 하는지, 전달하기 위한 내용도 담고 있는 공간.
	- 클라이언트의 요청에 JSP 페이지가 실행될 때 필요한 정보를 JSP 컨테이너(톰캣)에 알려주는 역할을 한다.
2. `<%@ include %>` : 현재 페이지에 다른 문서(JSP, HTML)를 가져와서 내용을 컴파일 할 때 사용되는 디렉티브.
	* 형식) <%@ include file="포함할 파일의 url" %>
	- include 지시어를 사용한 JSP 페이지가 컴파일되는 과정에서 include 되는 JSP 페이지의 소스 내용을 그대로 포함해서 컴파일을 진행한다.
	- 즉, 복사&붙여넣기 방식으로 두 개의 파일이 하나의 파일로 구성된 후 같이 컴파일이 된다.
3. `<%@ taglib %>` : 사용할 태그 라이브러리 지정
	- EL / JSTL 언어 사용 시 적용되는 디렉티브(추후 수업 진행 예정)
	
	
### 1.1. 페이지 지시어
`<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>`
- language="java" : 해당 JSP 페이지에서 사용되는 언어(java).
- contentType : 문서의 타입. JSP 페이지의 내용을 어떤 형태로 출력할 지를 웹 브라우저에게 알려주는 역할.
- charset : 문자(한글) 설정(UTF-8, EUC-KR)
- import : 다른 패키지에 있는 클래스를 가져다 사용할 때 지정.
- session : HttpSession 속성의 사용 여부를 지정.
	* 형식) <%@ page session="true" %>
- isErrorPage : 에러 페이지인지의 여부를 지정.
- errorPage : 에러가 발생했을 때 보여 줄 에러 페이지를 지정.
- pageEncoding="UTF-8" : 현재 페이지의 문자(한글) 설정.



### 1.2. JSP 페이지의 구성 요소 
1. 스크립틀릿 : 가장 일반적으로 JSP 페이지에서 많이 쓰이는  스크립트 요소. 주로 프로그래밍의 로직을 기술할 때 많이 사용된다. JSP 페이지에서 자바 코드가 작성되는 공간.
	* 형식) <% 자바 코드; %>

```html
<% 
	Calendar cal = Calendar.getInstance();
	  	
	int year = cal.get(Calendar.YEAR);
	int month = cal.get(Calendar.MONTH)+1;
	int day = cal.get(Calendar.DAY_OF_MONTH);
%>
```


2. 표현식 : 일반적으로 JSP 페이지에서 자바의 System.out.println()과 유사하게 사용된다. 데이터를 출력할 때 주로 사용.
	* 형식) <%=변수명, 수식 %>
	
```html
<%=year%>년  <%=month%>월 <%=day %>일
```


3. 선언문 : 일반적으로 JSP 페이지에서 자바의 멤버변수 또는 멤버 메서드를 선언할 때 사용된다.
	* 형식) <%! 변수 선언 및 메서드 선언; %> 
	
```html
<%
	public int plus(int a, int b){
		return a + b;
	}
%>

<h3>7 + 5 = <%=plus(7, 5) %></h3>	// 웹 페이지에 출력
```


## 2. JSP가 등장하게 된 배경
1. Servlet의 문제점
- 웹 프로그램의 화면 기능이 복잡해지면서 서블릿의 자바 기반으로 화면 기능 구현 시 어려움이 발생한다.
- 디자이너 입장에서 화면 구현 시 자바 코드로 인해 작업이 어렵다. ==> 자바에 대한 지식이 없는 경우
- 서블릿에 비니지스 로직과 화면 구현 기능이 같이 있다 보니 개발 후 유지관리가 어렵다.
2. 해결책
- 서블릿의 비지니스 로직과 결과를 보여주는 화면 기능을 분리한다.
- 비지니스 로직과 화면을 분리함으로써 개발자는 비지니스 로직 구현에 집중하고, 디자이너는 화면 기능 구현에 집중 하게 되었다.
- 개발 후 재사용성과 유지관리가 훨씬 수월해지게 되었다.
   
   
## 3. JSP 동작 방식의 구성 요소
1. `<% 자바코드  %>` : 스크립트릿  ==> 자바 코드를 작성하고 싶을 때 사용.
2. `<%=    %>` : JSP 표현식 ==> 변수나 메서드의 결과값을 출력할 때 사용.
3. `<%!    %>` : JSP 선언부 ==> 변수나 메서드를 선언할 때 사용.
 
  
## 4. 브라우저 전송방식
 서블릿에서는 자바 코드와 함께 원하는 HTML 태그를 사용해서 브라우저로 전송을 하여 화면을 구현했다. 서블릿으로 화면을 구현하려면 화면에 해당하는 HTML 태그를 브라우저로 전송해 주기만 하면 브라우저가 받아서 실시간으로 구현을 해 주었다.
하지만 JSP는 HTML, CSS, JavaScript는 물론이고 JSP에서 제공하는 여러가지 구성 요소가 화면을 구현하는데 사용된다. 그러다 보니 JSP 파일 자체를 브라우저로 전송을 하면 브라우저는 JSP 요소들을 인식을 하지 못하는 현상이 발생한다. 따라서 JSP는 톰켓 컨테이너에 의해 브라우저로 전송되기 전에 실행 단계를 거쳐야 한다.


* 톰켓 컨테이너에서 JSP 변환 과정
1. 변환 단계 : 컨테이너는 JSP 파일을 자바 파일로 변환한다.
2. 컴파일 단계 : 컨테이너는 변환된 자바 파일을 클래스 파일로 변환한다.
3. 실행 단계 : 컨테이너는 클래스 파일을 실행하여 그 결과(HTML, CSS, JavaScript)를 브라우저로 전송한다.


## 5. JSP 내장 객체
- 객체를 생성하지 않고 사용할 수 있는 객체를 의미.
- 내장 객체는 JSP 페이지 내에서 제공하는 특수한 레퍼런스 타입의 변수이다.
- JSP 페이지에서 사용하게 되는 특수한 레퍼런스 타입의 변수가 아무런 선언과 객체 생성 없이 사용할 수 있는 이유는 JSP 페이지가 Servlet으로 변환될 때 JSP 컨테이너가 자동적으로 제공을 해 주고 있기 때문이다.



### 5.1. JSP 내장 객체의 종류
- pageContext : JSP 페이지에 대한 정보를 저장하고 있는 객체.
- request : 웹 브라우저의 요청 정보를 저장하고 있는 객체.
- response : 웹 브라우저의 요청에 대한 응답 정보를 저장하고 있는 객체.
- out : JSP 페이지에 출력할 내용을 저장하고 있는 객체.
- session : 하나의 웹 브라우저의 정보를 유지하기 위한 세션 정보를 저장하고 있는 객체.
- application : 웹 애플리케이션 Context의 정보를 저장하고 있는 객체.


```jsp
<%	
	// 한글 깨짐 처리
	response.setCharacterEncoding("UTF-8");
	response.setContentType("text/html; charset=UTF-8");
	
	String userId = request.getParameter("id").trim();
	String userPwd = request.getParameter("pwd").trim();
%>

<body>
<th>아이디</th>
<td><%=userId %>
				
<th>비밀번호</th>
<td><%=userPwd %>
</body>
```

또는 아래와 같이 바로 `<body>`에 작성할 수도 있다.

```jsp
<body>
<th>아이디</th>
<td><%=request.getParameter("id").trim() %>
				
<th>비밀번호</th>
<td><%=request.getParameter("pwd").trim() %>
</body>
```

* `trim()` : 맨 앞과 맨 뒤의 공백이 있으면 공백을 제거하는 메서드.
	- 아이디나 비밀번호 입력시 공백이 들어가 DB에 저장되는 경우 추후 문제가 발생할 가능성이 크다. 앞뒤로 의미없는 공백을 잘라내어 유의미한 데이터만 저장되도록 한다.



### 5.2. 내장(내부) 객체 사용 시 공통적으로 사용하는 메서드
주어진 key 속성의 값을 value로 지정한다(리턴타입 : void).
- `getAttribute(String key)` : 주어진 key 속성의 값(value)을 얻어낸다(리턴타입 : Object).
- `removeAttribute(String key)` : 주어진 key 속성의 값(value)을 제거한다(리턴타입 : void).
- `getAttributeNames()` : 모든 속성의 이름을 구한다.
  
  
## 6. JSP 페이지 이동 : forward, redirect
- 웹 애플리케이션은 여러 기능을 합쳐 하나의 프로그램을 실행하는 구조로 되어 있다. 회원관리 기능, 게시판 관리 기능, 주문 관리 등에 대해 각각의 서블릿이 기능을 수행하게 된다.
- 이 때 프로그램을 실행하다가 보면 서블릿끼리 또는 서블릿과 JSP를 연동해서 작업을 해야 하는 경우가 생길 수 밖에 없다. 예를 든다면 쇼핑몰의 경우 상품 관리 서블릿과 조회된 상품을 화면에 표시하는 JSP는 각각 따로 존재하게 되어 있다. 따라서 사용자가 상품 조회를 요청하면 상품 관리 서블릿은 데이터베이스에서 상품 정보를 조회한 후 다시 JSP에게 해당 상품 정보를 전달하여 상품 정보를 표시해야 한다. 이러한 페이지 이동이 필수적이라고 보면 된다.
	* 요청에 대한 추가 작업을 다른 서블릿에게 수행하게 한다.
	* 요청에 포함된 정보를 다른 서블릿이나 JSP 와 공유할 수 있다.
	* 요청에 정보를 포함시켜 다른 서블릿에게 전달할 수 있다.
	* 모델2 개발 시 서블릿에서 JSP 페이지로 데이터를 전달하는데 사용된다.
  
### 6.1. forward 방식 (중요!)
- request에 영역(scope)에 담긴 값이 유효하다.
- 이동된 화면이 url 창에 안 보인다(사용자는 이동했는지 알 수 없음)
- 서블릿이 직접 요청하는 방식.
- **주로 키 값을 넘겨 줄 때 사용한다.** (중요!)
- RequestDispatcher 객체를 이용한다. ==> `forward()` 메서드를 사용.
- 형식)

```jsp
RequestDispatcher rd = request.getRequestDispatcher("이동위치");
rd.forward(request, response);
```
  
### 6.2. redirect 방식
- 클라이언트가 새로 페이지를 요청하는 것과 같은 방식으로 페이지가 이동된다.
- 웹 브라우저에 재요청하는 방식이다.
- **일반적으로 변수 값을 넘겨 줄 때 사용한다.** (중요!)
- request, response 값이 유효하지 않다(새로 만들어짐).
- 이동된 url이 화면에 나타난다.
- get방식으로 data를 넘길 때
- 형식) `response.sendRedirect("이동위치");`




*** name 과 value
* `name` : 서블릿이나 jsp 페이지로 데이터(`value`)를 전송하기 위한 속성. 서블릿이나 jsp 페이지에서 form 페이지의 name 속성의 ""(쌍따옴표) 안에 있는 이름을 getParameter() 메서드로 받아주면 value 값을 받아주게 된다. 폼창에서 넘어온 데이터를 받을 때 어떤 데이터를 어떻게 받아야 할지 모르기 때문에 name이라는 속성에 변수명을 작성해서 해당 변수명을 getParamenter("변수명") 메서드로 받으면 변수명에 들어 있는 값을 가져오게 된다.



## 7. error page
에러 발생시 처리하는 방법에는
1. 페이지 지시어에서 `error page="에러발생시 연결되는 페이지 주소"` 작성
2. web.xml 파일에서 에러 페이지 설정



### 7.1. 페이지 지시어에서 `error page` 작성
```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8" errorPage="error.jsp"%>
```


### 7.2. web.xml 파일에서 에러 페이지 설정
```xml
<!-- error 페이지 설정 -->
<error-page>
<error-code>404</error-code> <!-- 에러 코드 -->
<location>/err/error_404.jsp</location> <!-- 에러발생시 연결되는 페이지 주소 -->
</error-page>
```


----------------------------------
# Cookie 쿠키
- 사용자가 웹 사이트를 처음 방문할 때 웹 사이트에서 클라이언트의 컴퓨터에 저장해 놓는 작은 파일.
- 웹 페이지들 사이의 공유 정보를 클라이언트 컴퓨터에 저장해 놓고 필요할 때 여러 웹 페이지들이 공유해서 사용할 수 있도록 매개 역할을 하는 방법.
- http 프로토콜은 웹 브라우저에 응답 후 일정 시간이 지나면 접속을 끊는 특징이 있다. 이러한 특징으로 쿠키 기술이 발달하게 되었다.
    
## 1. 쿠키의 특징
- 쿠키는 서버에서 생성된다.
- 쿠키는 클라이언트 컴퓨터에 저장된다.
- 쿠키의 관리는 웹 브라우저가 한다.
- 쿠키의 크기는 4KB로 제한적이며, 300개 정도 쿠키를 만들어 사용할 수 있다.
- 도메인당 쿠키가 만들어진다(웹 사이트당 하나의 쿠키가 만들어짐).
- 쿠키는 보안이 취약하다.
  
## 2. 쿠키의 생성 방법과 관련 메서드
* 쿠키의 생성 방법
	- 쿠키 생성은 쿠키 클래스를 사용.
	- 쿠키 속성 설정(setter)
	- 쿠키의 전송(response 객체에 탑재 : addCookie())
  
* 쿠키 관련 메서드
	- setMaxAge() : 쿠키의 유효 기간을 설정하는 메서드.
	- setPath() : 쿠키 사용을 위한 디렉토리를 설정하는 메서드. (특정 경로명을 갖는 url로 전송하도록 설정)
	- setValue() : 쿠키값을 설정하는 메서드. 
	- setVersion() : 쿠키의 버전을 설정하는 메서드.
	- getMaxAge() : 쿠키의 유효기간 정보를 얻어오는 메서드.
	- getName() : 쿠키의 이름을 얻어올 때 사용하는 메서드.
	- getPath() : 쿠키의 유효 디렉토리 정보를 얻어올 때 사용하는 메서드.
	- getVersion() : 쿠키의 버전을 얻어올 때 사용하는 메서드.
	- getCookies() : 쿠키 데이터를 읽어올 때 사용하는 메서드. ==> 웹 브라우저가 보낸 쿠키를 배열로 반환해 주는 메서드.
    
## 3. 저장된 쿠키를 사용하는 순서
1. 웹 브라우저에 요청을 하여 쿠키를 얻어온다.
2. 쿠키는 이름, 값의 쌍으로 된 배열 형태로 반환된다. 반환된 쿠키의 배열에서 쿠키의 이름을 가져온다.
3. 쿠키의 이름을 통해서 해당 쿠키의 설정된 값을 추출한다.    
    
    
---------------------------------------    
# Session 세션
- 쿠키와 마찬가지로 서버와의 connection 관계를 유지하기 위해서 이용자
        정보를 저장하는 객체임.

## 1. 세션의 특징
- 세션은 서버에서만 접근이 가능함. - 서버의 메모리에 저장됨.
- 쿠키보다 보안성이 높음.
- 서버에 부하를 줄 수 있음.
- 쿠키의 기본 용량이 4KB, 300개로 제한적인 반면에 세션은 데이터에 제한이 없음.
- 브라우저당 한 개의 세션이 생성이 됨.
- 세션은 유효 시간을 가짐. - 기본 유효 시간은 30분임.
- 로그인 상태 유지 기능이나 쇼핑몰의 장바구니 담기 기능 등에 주로 사용이 됨.
  
## 2. 세션 관련 메서드
- setAttribute() : 세션의 속성을 설정하는 메서드.
	* 형식) session.setAttribute("id", value);
- getAttribute() : 세션에서 데이터를 얻어올 때(세션에 속성을 사용할 때) 이용하는 메서드.
	* 형식) String id = (String)session.getAttribute("id");
- getAttributeNames() : 세션에 저정되어 있는 모든 데이터의 이름을 얻어올 때 사용하는 메서드. 
- removeAttribute() : 세션의 특정 데이터를 제거하는 메서드.
	* 형식) session.removeAttribute("id");
- invalidate() : 세션의 모든 데이터를 삭제하는 메서드. 
- getId() : 자동 생성된 세션의 아이디를 얻어올 때 사용하는 메서드.
- isNew() : 세션이 최초로 생성되었는지 여부를 알고자 할 때 사용하는 메서드.
- getMaxInactiveInterval() : 세션의 유효 시간을 얻어을 때 사용하는 메서드.
  
  
  
-------------------------------------
# ActionTag 액션태그
- 페이지 내에서 어떤 동작을 하도록 지시하는 태그.
	* 예) 페이지 이동(forward), 페이지 포함(include), param
- 웹 컨테이너에서 실행되고 결과만 웹 브라우저에 전달되어 출력.
- 자바 빈(bean)과 연관이 있는 태그.
  
## 1. 액션태그의 종류
- 표준 액션(standard action) : JSP 페이지에서 바로 사용할 수 있는 액션. 
- 커스텀 액션(custom action) : 별도의 라이브러리를 설치해서 사용하는 액션.
  
  
- 표준 액션 사용 예)

```jsp
    <jsp:include page="a.jsp">
```
* jsp 접두어는 표준 액션을 의미한다.
      
      
      
-------------------------------
# Java Bean 자바 빈
- 정보의 덩어리. 즉, 데이터 저장소(데이터 객체).
- 데이터를 저장하기 위한 필드와 데이터를 컨트롤하는 setter / getter 메서드를 하나의 쌍으로 가지고 있는 클래스.
- getter / setter 메서드는 자바빈의 필드에 데이터를 저장하고 조회하는 작업을 한다.
    
    
## 1. 자바 빈(클래스) 만드는 방법
- 패키지 선언 : com.sist.model.클래스이름(빈 클래스명)
- 필드 선언
	* private 를 이용하여 멤버 선언.
	* getter / setter 메서드 만들기. - 프로퍼티 방식
	* 프로퍼티 : private 필드를 외부에서 접근하기 위해서 공개형 접근제어자 public으로 메서드를 정의해 놓고 이를 통해서 간접적으로 필드에 접근하는 방식.
     
                            
## 2. 자바 빈과 관련된 액션 태그 - 3가지
- <jsp:useBean>        ==> 자바 빈을 생성.
- <jsp:setProperty>    ==> 자바 빈에 정보를 저장하는 개념.
- <jsp:getProperty>    ==> 자바 빈에서 정보를 얻어오는 개념.
  
- <jsp:useBean> 기본 형식
	* 형식) <jsp:useBean class="클래스 풀네임" id="빈이름" [scope="범위"] />
  
- <jsp:setProperty> 기본 형식
	* 형식) <jsp:setProperty name="빈 이름" property="프로퍼티 이름" value="값" />

- <jsp:getProperty> 기본 형식
	* 형식) <jsp:getProperty name="빈 이름" property="프로퍼티 이름" />
	: 회원의 이름을 얻기 위해서 getName() 메서드를 호출하는 것과 같다. id의 빈이름과 name의 빈 이름은 반드시 같아야 한다.





  
