package application;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.logging.Level;
import java.util.logging.Logger;
import javafx.scene.control.Alert;
import javafx.scene.control.Alert.AlertType;

// Class connect to database to execute queuries 
public class JDBC  {
	private static String url = "jdbc:mysql://localhost:3306/books";
	
	// for local machine
	private static String user = "user";
	private static String pass = "******";
	
	private String dbEmail = null; 
	private String dbPassword = null; 
	
	public void addEntry(String author, String title, int pages, int timesRead) {
		
		String sql = "INSERT INTO book(author, title, pages, times_read) VALUES(?, ?, ?, ?)";
		
		try(Connection con = DriverManager.getConnection(url, user, pass);
				PreparedStatement pst = con.prepareStatement(sql)){
			
			pst.setString(1, author);
			pst.setString(2, title);
			pst.setInt(3, pages);
			pst.setInt(4, timesRead);
			
			int alert = pst.executeUpdate();
						
			if(alert == 0) {
				Alert error = new Alert(AlertType.ERROR, "Unable to process request");
				error.show();
			}
			else {
				Alert success = new Alert(AlertType.CONFIRMATION, "Book has been added.");
				success.show();
			}
		} 
		
		catch(SQLException ex) {
			Logger lgr = Logger.getLogger(JDBCTest.class.getName());
            lgr.log(Level.SEVERE, ex.getMessage(), ex);
		}
	} // End addEntry
	
	public boolean checkUser(String email, String password) {
		boolean exist = false; 
		System.out.println("inside checkUser");
		String sql = "SELECT email, password FROM user WHERE email = ? AND password = ?";
	
		try(Connection con = DriverManager.getConnection(url, user, pass);
				PreparedStatement pst = con.prepareStatement(sql)){
			pst.setString(1, email);
			pst.setString(2, password);
			
			ResultSet rs = pst.executeQuery();

			if(rs.next()) {
				
				dbEmail = rs.getString(1);
				dbPassword = rs.getString(2);
				
			}
			else {
				return exist; 
			}			
			if(dbEmail.equals(email) & dbPassword.equals(password)) {
				System.out.println("Able to login.");
				exist = true; 
			}
		} 
		catch(SQLException ex) {
			Logger lgr = Logger.getLogger(JDBCTest.class.getName());
            lgr.log(Level.SEVERE, ex.getMessage(), ex);
		}
		
		return exist; 
	}

	public boolean addUser(String fname, String lname, String email, String password) {
		boolean success = false; 
		Connection con = connect(); 
		String sql = "INSERT INTO user VALUES(?, ?, ?, ?, ?)";
		try {
			PreparedStatement pst = con.prepareStatement(sql);
			pst.setInt(1, 0);
			pst.setString(2, fname);
			pst.setString(3, lname);
			pst.setString(4, email);
			pst.setString(5, password);
			
			success = pst.execute();
		} catch (SQLException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} 		
		return success;
	}
	
	// change to private static
	public Connection connect() {
		Connection con = null;
		try{
			con = DriverManager.getConnection(url, user, pass);
		}		
		catch(SQLException ex) {
			Logger lgr = Logger.getLogger(JDBCTest.class.getName());
			lgr.log(Level.SEVERE, ex.getMessage(), ex);
		}
		return con; 
	}
}// End class
