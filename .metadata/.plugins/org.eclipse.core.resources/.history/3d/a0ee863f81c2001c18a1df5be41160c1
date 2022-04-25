

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

/**
 * Servlet implementation class ChangePassword
 */
@WebServlet("/ChangePassword")
public class ChangePassword extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
   
    public ChangePassword() {
        super();
        // TODO Auto-generated constructor stub
    }

	
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.getWriter().append("Served at: ").append(request.getContextPath());
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
	String newPassword=	(String) request.getParameter("password");
	String email=request.getParameter("email");
	PrintWriter out=response.getWriter();

     HttpSession session=request.getSession(false);
    
    
	
	String url = "jdbc:mysql://localhost:3306/flyaway";
	String dbusername = "root";
	String dbpassword = "root";
	try {
		Class.forName("com.mysql.cj.jdbc.Driver");
		Connection connection = DriverManager.getConnection(url, dbusername, dbpassword);

		String sqlQuery = "update Admindetails set password=? where email_id=?";
		PreparedStatement pstmt = connection.prepareStatement(sqlQuery);

		
		pstmt.setString(1, newPassword);
		pstmt.setString(2, email);
		
			pstmt.executeUpdate();
	
			request.setAttribute("newPass", newPassword);
			request.setAttribute("msg", "Password changed Succcessfully");
			RequestDispatcher rd=request.getRequestDispatcher("changePassword.jsp");
			rd.forward(request, response);
			
		

	} catch (Exception e) {
		// TODO: handle exception
	}
	
	}

}
