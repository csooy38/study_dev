# 게시판 파일 업로드

이전과 마찬가지로 mapping.properties 파일을 두어 서블릿을 관리하며 게시판을 작성하였다. 

## 0. 필요 파일 다운로드

우선 첨부파일을 업로드하기 위해서는 하나의 파일을 다운로드해야 한다.  

1. servlets.com 사이트 접속
2. COS File Upload Library 메뉴 클릭 - 하단에서 cos-20.08.zip 다운로드
3. 압축을 푼 후 lib 폴더의 "cos" 파일을 복사
4. 프로젝트의 WebContent/WEB-INF/lib 에 붙여넣기


## 1. upload_write.jsp : 파일 업로드 폼

<p align="center"><img src="./images/210521/06.png"></p>

게시글 작성 jsp 파일에서 파일 업로드할 때에는 input type을 "file"로 설정한다. 

```java
<th>파일첨부</th>
<td><input type="file" name="upload_file"></td>
```


폼 태그에서 enctype을 설정한다. 

```java
<%-- enctype : 이진 파일을 업로드하기 위한 속성 --%>
<form method="post" enctype="multipart/form-data" action="<%=request.getContextPath()%>/upload_write_ok.do">
```

## 2. UploadWriteAction : 게시글 작성 폼에서 작성한 파일 데이터 받기
자료실 폼 페이지에서 넘어온 데이터들을 DB에 저장하는 클래스.
편의상 첨부파일의 여부로 두 가지로 나누었지만 모든 경우를 아울러야하므로 둘 다 작성해야 한다.  


### 2-1. 첨부 파일이 존재하는 경우
첨부된 파일이 있다면 파일을 서버에 저장하는 작업이 필요하다.  


1) 첨부파일을 서버에 저장하기 위한 변수 및 객체를 선언한다.  

```java
UploadDTO dto = new UploadDTO();
		
// 첨부파일이 저장된 경로(위치) 설정
String saveFolder = "첨부파일이 저장된 경로(위치)";
		
// 첨부파일의 최대 크기
int fileSize = 10 * 1024 * 1024; // 10MB
		
// 파일 업로드를 진행 시 이진 파일 업로드를 위한 객체 생성
MultipartRequest multi = new MultipartRequest(
				request,						// 일반적인 request 객체 
				saveFolder,						// 업로드 파일 저장 위치 
				fileSize,						// 업로드할 파일의 최대 크기 
				"UTF-8",						// 문자 인코딩 방식
				new DefaultFileRenamePolicy());	// 파일 이름이 중복이 안 되도록 설정
```


2) MultipartRequest 객체를 사용하여 넘어온 데이터를 저장한다. 

```java			
// 자료실 폼에서 넘어온 데이터들을 받아야 한다. 
String upload_writer = multi.getParameter("upload_writer").trim();
String upload_title = multi.getParameter("upload_title").trim();
String upload_cont = multi.getParameter("upload_content").trim();
String upload_pwd = multi.getParameter("upload_pwd").trim();
```

3) input type="file"인 데이터는 getFile() 메서드로 받는다. 

```java
// 자료실 폼에서 type="file"로 되어 있으면 getFile() 메서드로 받아야 한다.
File upload_file = multi.getFile("upload_file");
```

4) 첨부파일이 존재하는 경우 서버 저장을 위한 폴더를 생성한다.  
".../upload/2021-05-21/홍길동_파일명" 형식으로 폴더를 생성하기 위하여 날짜 객체를 생성하였다.   
		
```java
if(upload_file != null) { 	// 첨부파일이 존재하는 경우
			
	// getName() : 첨부파일의 이름을 문자열로 반환하는 메서드.
	String fileName = upload_file.getName();
	
			
	// 날짜 객체 생성 : 첨부파일을 날짜별로 저장하기 위하여.
	Calendar cal = Calendar.getInstance();
	int year = cal.get(Calendar.YEAR);
	int month = cal.get(Calendar.MONTH) + 1;
	int day = cal.get(Calendar.DAY_OF_MONTH);
			
	// ".../upload/2021-05-21" 형태로 폴더를 만든다.
	String homedir = saveFolder+"/"+year+"-"+month+"-"+day;
			
	// 날짜 폴더를 만들어 보자.
	File path1 = new File(homedir);
	if(!path1.exists()) {	// 해당 폴더가 존재하지 않는 경우
		path1.mkdir();	// make directory : 실제 폴더를 만드는 메서드
	}
			
	// 파일 폴더를 만들어 보자. ==> 예) 작성자_파일명
	// ".../upload/2021-05-21/홍길동_파일명"
	String reFileName = upload_writer+"_"+fileName;
			
	upload_file.renameTo(new File(homedir+"/"+reFileName));
			
	String fileDBName = "/"+year+"-"+month+"-"+day+"/"+reFileName;
			
	dto.setUpload_file(fileDBName);
}
```

첨부파일을 넣어 게시물을 저장하면  
지정한 경로를 따라 폴더가 생성되고 그 아래 지정한 파일명으로 저장된다.  

<p align="center"><img src="./images/210521/05.png"></p>


### 2-2. 첨부파일이 존재하지 않는 경우 
첨부파일이 존재하지 않는다면 기존과 같이 parameter로 데이터를 받아 저장한다.  
첨부파일이 없다면 넘어갈 파일 데이터도 존재하지 않으므로 "upload_file"은 parameter로 받을 필요가 없다.  

```java
dto.setUpload_writer(upload_writer);
dto.setUpload_title(upload_title);
dto.setUpload_cont(upload_cont);
dto.setUpload_pwd(upload_pwd);
```


### 2-3. insertUpload() 메서드를 호출하여 DB에 입력값을 저장한다.  
DB 저장에 성공하면 다시 서블릿을 실행하여 upload_list 페이지로 넘어갈 것이기 때문에 redirect 는 true로 설정한다. forward를 반환하면 자동으로 "upload_list.do"에 따른 서블릿이 실행된다.  
실패하면 이전화면으로 돌아가도록 스크립트를 작성한다.    

```java
UploadDAO dao = UploadDAO.getInstance();
int res = dao.insertUpload(dto);
		
ActionForward forward = new ActionForward();
PrintWriter out = response.getWriter();
		
if(res > 0) {
	forward.setRedirect(true);
	forward.setPath("upload_list.do");
}else {
	out.println("<script>");
	out.println("alert('자료실 업로드 실패')");
	out.println("history.back()");
	out.println("</script>");
}				
	return forward;
}
```


## 3. 파일 삭제
file.delete() 메서드를 이용하여 게시물 삭제 시 파일도 함께 삭제되도록 한다.  

```java
// upload된 파일까지 삭제
String up = "C:\\NCS\\transfer\\15_Board_FileUpload\\WebContent\\upload";
		
// 업로드된 파일명 : /년-월-일/파일명
String fileName = dto.getUpload_file();
			
File file = new File(up+fileName);
file.delete();	// 기존 이진 파일을 삭제하는 메서드
```






