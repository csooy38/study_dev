
# EmpDTO.java
- DB와 동일하게 멤버변수 구성


```java
// DTO(Data Transfer Object) : 데이터 전송 객체
// 기본적으로 DB 상의 테이블의 컬럼과 동일하게 멤버변수 구성.

public class EmpDTO {
	
	private int empno;			// 사원 번호
	private String ename;		// 사원 이름
	private String job;			// 담당 업무
	private int mgr;			// 관리자 사원번호 
	private String hiredate;	// 입사 일자
	private int sal;			// 사원 급여
	private int comm;			// 사원 보너스
	private int deptno;			// 사원 부서번호
	
	public int getEmpno() {
		return empno;
	}
	public void setEmpno(int empno) {
		this.empno = empno;
	}
	public String getEname() {
		return ename;
	}
	public void setEname(String ename) {
		this.ename = ename;
	}
	public String getJob() {
		return job;
	}
	public void setJob(String job) {
		this.job = job;
	}
	public int getMgr() {
		return mgr;
	}
	public void setMgr(int mgr) {
		this.mgr = mgr;
	}
	public String getHiredate() {
		return hiredate;
	}
	public void setHiredate(String hiredate) {
		this.hiredate = hiredate;
	}
	public int getSal() {
		return sal;
	}
	public void setSal(int sal) {
		this.sal = sal;
	}
	public int getComm() {
		return comm;
	}
	public void setComm(int comm) {
		this.comm = comm;
	}
	public int getDeptno() {
		return deptno;
	}
	public void setDeptno(int deptno) {
		this.deptno = deptno;
	}
	
}
```


# index.jsp
- 기본 화면 설정

```jsp
<body>

	<div align="center">
		<hr width="50%" color="blue">
			<h3>EMP 테이블 메인 페이지</h3>
		<hr width="50%" color="blue">
		<br><br>
		
		<%-- request.getContextPath() : 현재 프로젝트명을 반환하는 메서드. --%>
		<a href="<%=request.getContextPath() %>/select">[전체 레코드]</a>
	</div>

</body>
```

- [전체 레코드] 클릭시 `/select` 를 통해 서블렛으로 이동한다.
- `href="<%=request.getContextPath() %>/select"` = "현재 프로젝트명/select" 를 주소값으로 설정하는 것과 같다.	
	* 예) 현재 주소 : http://localhost:8080/example/test.jsp 
	* 예) "<%=request.getContextPath() %>/select" = http://localhost:8080/example/select

<p align="center"><src img="./images/210506/00.png"></p>



# SelectServlet
- service 서블렛으로 생성하였다.


```java
@WebServlet("/select")
public class SelectServlet extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    
    public SelectServlet() {
        super();
        // TODO Auto-generated constructor stub
    }

	
	protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// DB에 접속을 해서 EMP 테이블의 전체 리스트를 가져오는 작업(비지니스 로직)
		// 가져온 전체 리스트를 View page로 넘겨주는 작업
		EmpDAO dao = new EmpDAO();
		
		// DB EMP 테이블에서 전체 리스트를 조회하는 작업
		List<EmpDTO> allList = dao.selectList();	
		System.out.println("allList >>> " + allList);
		
		// 페이지 이동 시 데이터를 같이 이동시키자.
		request.setAttribute("List", allList);
		
		// 페이지 이동
		RequestDispatcher rd = request.getRequestDispatcher("select.jsp");
		rd.forward(request, response);	// 실질적으로 페이지 이동
		
		
	}

}
```


- EmpDAO 객체의 `dao` 라는 참조변수를 생성하여 `selectList()` 메서드를 호출한다.
```java
EmpDAO dao = new EmpDAO();
```

- `selectList()` 메서드 호출 결과 `list`의 주소값이 `allList`에 저장된다.
- 이 때, `dao.selectList()`로 리턴되는 값이 `List<EmpDTO>` 형태이므로 동일하게 지정한다.
```java
List<EmpDTO> allList = dao.selectList();
```

- `allList`를 `request.setAttribute()`를 활용하여 `"List"`라는 키에 저장한다.
```java
request.setAttribute("List", allList);
```

- 저장한 키&데이터와 함께 `select.jsp`로 페이지 이동한다.
```java
RequestDispatcher rd = request.getRequestDispatcher("select.jsp");
rd.forward(request, response);
```


# EmpDAO.java
* DAO(Data Access Object) : 데이터 접근 객체 ==> DB에 접속(연동)하는 객체.
	- DAO란 데이터베이스에 접속해서 데이터 추가, 수정, 삭제, 조회 등의 작업을 수행하는 클래스.
	- 일반적으로 JSP 또는 Servlet에서 위의 작업들을 같이 사용할 수 있지만 유지보수, 코드의 모듈화를 위해서 DAO 클래스를 따로 만들어서 사용한다.


```java
public class EmpDAO {
	
	Connection con = null;				// DB와 연결하는 객체
	PreparedStatement pstmt = null; 		// DB에 SQL문을 전송하는 객체
	ResultSet rs = null;				// SQL문을 실행 후 결과값을 가지고 있는 객체
	String sql = null;				// 쿼리문을 저장할 객체
	
	public EmpDAO() {	// 기본 생성자
		
		String driver = "oracle.jdbc.driver.OracleDriver";
		String url = "jdbc:oracle:thin:@localhost:1521:XE";
		String user = "web";
		String password = "1234";
		
		try {
			// 1단계 : 오라클 드라이버 로딩
			Class.forName(driver);
			
			// 2단계 : DB(오라클)와 연결
			con = DriverManager.getConnection(url, user, password);
			
			
		} catch (Exception e) {
			e.printStackTrace();
		}
	} // 기본 생성자 end

	// DB EMP 테이블에서 전체 리스트를 조회하는 메서드
	public List<EmpDTO> selectList() {
		List<EmpDTO> list = new ArrayList<EmpDTO>();	// 다형성	
		System.out.println("selectList() 메서드에서 list >>> " + list);		
		
			
		try {
			sql = "select * from emp order by empno desc";
			pstmt = con.prepareStatement(sql);
			rs = pstmt.executeQuery();
			
			while(rs.next()) {
				EmpDTO dto = new EmpDTO();
				
				dto.setEmpno(rs.getInt("empno"));
				dto.setEname(rs.getString("ename"));
				dto.setJob(rs.getString("job"));
				dto.setMgr(rs.getInt("mgr"));
				dto.setHiredate(rs.getString("hiredate"));
				dto.setSal(rs.getInt("sal"));
				dto.setComm(rs.getInt("comm"));
				dto.setDeptno(rs.getInt("deptno"));
				
				list.add(dto);
			}
			
			// open 객체 닫기
			rs.close(); pstmt.close(); con.close();
			
		} catch (Exception e) {
			e.printStackTrace();
		}
		System.out.println("데이터 완료");
		System.out.println("selectList() 메서드에서 list >>> " + list);
		
		return list;
		
		
		
	} // selectList() 메서드 end
	
}
```


# select.jsp
```jsp
<%
	List<EmpDTO> emp = (List<EmpDTO>) request.getAttribute("List");
	System.out.println("emp >>> " + emp);
%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>

	<div align="center">
		<hr width="50%" color="red">
		<h3>EMP 테이블 전체 레코드 리스트</h3>
		<hr width="50%" color="red">
		<br> <br>

		<table border="1" cellspacing="0" width="650">
			<tr>
				<th>사  번</th> <th>이  름</th> <th> 담당업무</th>
				<th>관리자No.</th> <th>급  여</th> <th>보너스</th>
				<th>부서번호</th> <th>입사일자</th>
			</tr>
			<%
				if(emp.size() != 0) {	// 데이터가 있다면
					// 데이터 수만큼 반복해서 출력
					for(int i=0; i<emp.size(); i++) {
						EmpDTO dto = emp.get(i);
						System.out.println("dto >>> " + dto);
					%>
					
					<tr>
						<td><%=dto.getEmpno() %></td>
						<td><%=dto.getEname() %></td>
						<td><%=dto.getJob() %></td>
						<td><%=dto.getMgr() %></td>
						<td><%=dto.getSal() %></td>
						<td><%=dto.getComm() %></td>
						<td><%=dto.getDeptno() %></td>
						<td><%=dto.getHiredate().substring(0, 10) %></td>
					</tr>
	
					<% } // for문 end
				}else {
					// 데이터가 없는 경우
					%>
					<tr>
						<td colspan="8 align="center">
							<h3>검색된 레코드가 없습니다.</h3>
						</td>
					</tr>
				<%}%>
			</table>
	</div>

</body>
</html>
```
