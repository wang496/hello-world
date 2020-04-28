package cn.sdut.dao;
import java.sql.*;

public class BaseDao {
	Connection con;
	PreparedStatement pst;
	ResultSet rs;
	//con
	public Connection getConnection() throws ClassNotFoundException, SQLException
	{
		Class.forName("com.mysql.jdbc.Driver");
		Connection con = DriverManager.getConnection("jdbc:mysql://localhost:3306/bank?useUnicode=true&characterEncoding=UTF-8","root","");
		return con;
	}
	
	//closeAll
	public void closeAll()
	{
		try {
		if(rs!=null)
		{
			rs.close();
		}
		if(pst!=null)
		{
			pst.close();
		}
		if(con!=null)
		{
			con.close();
		}
	}
		catch(Exception e)
		{
			e.printStackTrace();
		}
	}
}
