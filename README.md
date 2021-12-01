//# jdbc-programe-
//SelectTest.java
package com.bce.JDBCApp1;
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.DriverManager;
import java.sql.SQLException ;
import java.sql.Statement;
import java.util.Scanner;
public class SelectTestJava {
	public static void main(String[] args)throws Exception {
		//intialize the varisble 
		Connection con=null;
		Statement st=null;
		ResultSet rs=null;
		String city=null;
	Scanner scn=new Scanner(System.in);
	System.out.println("Enter the city Name :");
	city=scn.nextLine();
	try { 
		//load the driver manager 
		Class.forName("oracle:jdbc:driver:OracleDriver");
		//establish the connection
		con=DriverManager.getConnection("jdbc:oracle:thin:@localhost:1521:xe","system","kundan");
		//create statement object 
		st=con.createStatement();
		//excuse the sql queary 
		rs=st.executeQuery("select * from students where addresh=HYD"+city);
		//print the data the data base table bwlow 
		while(rs!=null) {
			System.out.println(rs.getString(1)+""+rs.getString(2)+" "+rs.getInt(3));
		}//end of the while
		//close the jdbc object 
		rs.close();
		st.close();
		con.close();
	}//end of the try block
	catch(SQLException e) {
    e.printStackTrace();
	}	
	}//end of the main main method 
}//end of the class
