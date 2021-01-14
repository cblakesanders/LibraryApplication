package application;

import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.PasswordField;
import javafx.scene.control.TextField;
import javafx.scene.layout.GridPane;
import javafx.scene.text.Text;

public class CreateAccountGUI {
	// GridPane and Scene
    private GridPane gridPane = new GridPane();
	private Scene scene = new Scene(gridPane, 400, 400);
	
	// Text Labels
	private Text firstNameText = new Text("First Name");
	private Text lastNameText = new Text("Last Name");
	private Text emailText = new Text("Email");
	private Text passwordText = new Text("Password");
	private Text passwordTwoText = new Text("Re-enter Password");
	
	// Fields
	private TextField firstNameField = new TextField();
	private TextField lastNameField = new TextField();
	private TextField emailField = new TextField();
	private PasswordField passwordField = new PasswordField();
	private PasswordField passwordTwoField = new PasswordField();
	
	// Buttons
	private Button button1 = new Button("Create Account");
	private Button button2= new Button("Clear");
	
	
	public void setScene() throws Exception{
		
		// Set min size 
		gridPane.setMinSize(400, 200);
		gridPane.setPadding(new Insets(10, 10, 10, 10));
		gridPane.setVgap(5);
		gridPane.setHgap(5);
		gridPane.setAlignment(Pos.CENTER);
		
		// Add nodes to grid
		gridPane.add(firstNameText, 0, 0);
		gridPane.add(firstNameField, 1, 0);
		gridPane.add(lastNameText, 0, 1);
		gridPane.add(lastNameField, 1, 1);
		gridPane.add(emailText, 0, 2);
		gridPane.add(emailField, 1, 2);
		gridPane.add(passwordText, 0, 3);
		gridPane.add(passwordField, 1, 3);
		gridPane.add(passwordTwoText, 0, 4);
		gridPane.add(passwordTwoField, 1, 4);
		gridPane.add(button1, 0, 5);
		gridPane.add(button2, 1, 5);
		
		// Add button event handles
		button1.setOnAction(new EventHandler<ActionEvent>() {
			@Override
			public void handle(ActionEvent e) {
				// Try to create user
				JDBCTest conn = new JDBCTest(); 
				
				conn.addUser(firstNameField.getText(), lastNameField.getText(), emailField.getText(), passwordField.getText());
			}
		});
		
		button2.setOnAction(new EventHandler<ActionEvent>() {
			@Override
			public void handle(ActionEvent e) {
				 firstNameField.clear();
				 lastNameField.clear();
				 emailField.clear();
				 passwordField.clear(); 
				 passwordTwoField.clear(); 
			}
		});
				
	}
		
	public Scene getScene() {
		return this.scene;
	}
}
