# HTML 관련 프로그램 설치

1) 웹 편집기 다운로드
: [eclipse.org](http://eclipse.org) - Download - Download Packages - More Downloads - Older Versions - Photon - R Packages - Eclipse IDE for Java EE Developers x86_64(사양에 맞는 파일 선택하여 다운로드)

2) 서버 다운로드
: [tomcat.apache.org](http://tomcat.apache.org) - Download - Tomcat9 - 9.0.45 - core - 64-bit [windows.zip](http://windows.zip) (사양에 맞는 파일 선택하여 다운로드)

3) 각각 압축을 풀고, 이클립스를 실행하여 workspace 경로 지정

4) Project Explorer - new project - Other... - Server - server - Tomcat v9.0 server

5) Servers의 server.xml 파일을 열어 코드 수정

```
<!-- 63번 라인을 아래와 같이 port="8585"로 수정 -->
<Connector connectionTimeout="20000" port="8585" protocol="HTTP/1.1" redirectPort="8443"/>
```

6) 한글 설정 : Window - Preference - enc 검색 - Workspace/CSS Files/HTML Files/JSP Files/XML Files 모두 UTF-8로 설정

<p align="center"><img src="./images/210419/06.png" width="80%"></p>

7) Window - Web Browser - Chrome 으로 설정

<p align="center"><img src="./images/210419/07.png" width="80%"></p>
