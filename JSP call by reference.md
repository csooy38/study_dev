

# indet.jsp
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



# SelectServlet
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
