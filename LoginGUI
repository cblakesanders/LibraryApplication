package application;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.HashMap;
import java.util.Map;

import javafx.application.Application;
import javafx.collections.FXCollections;
import javafx.collections.ObservableList;
import javafx.event.ActionEvent;
import javafx.event.EventHandler;
import javafx.geometry.Insets;
import javafx.geometry.Pos;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.control.Menu;
import javafx.scene.control.MenuBar;
import javafx.scene.control.MenuItem;
import javafx.scene.control.PasswordField;
import javafx.scene.control.TableColumn;
import javafx.scene.control.TableView;
import javafx.scene.control.TextField;
import javafx.scene.control.cell.MapValueFactory;
import javafx.scene.layout.BorderPane;
import javafx.scene.layout.GridPane;
import javafx.scene.layout.HBox;
import javafx.scene.text.Text;
import javafx.stage.Stage;

public class LoginGUI extends Application {
	
	private BorderPane root = new BorderPane(); 
	private GridPane pane = new GridPane();
	private Scene loginScene = new Scene(root, 400, 400); 
	private HBox buttonBox = new HBox(); 
	
	// Fields 
	private Text loginText = new Text("Email Address "); 
	private Text passwordText = new Text("Password ");
	private TextField loginField = new TextField();
	private PasswordField passwordField = new PasswordField(); 
	
	// Buttons
	private Button submitButton = new Button("Submit");
	private Button cancelButton = new Button("Cancel"); 
	
	// TableView
	private TableView table = new TableView();
	
	@Override
	public void start(Stage primaryStage) throws Exception {
		
		pane.setPadding(new Insets(10, 10, 10, 10));
		pane.setHgap(10);
		pane.setVgap(10);
		pane.setAlignment(Pos.CENTER);
		
		pane.add(loginText, 0, 0);
		pane.add(loginField, 1, 0);
		pane.add(passwordText, 0, 1);
		pane.add(passwordField, 1, 1);
		
		buttonBox.getChildren().addAll(submitButton, cancelButton);
		buttonBox.setSpacing(10);
		pane.add(buttonBox, 1, 2);
			
		pane.setGridLinesVisible(false);
		
		// Add button event handles
		submitButton.setOnAction(new EventHandler<ActionEvent>() {
			@Override
			public void handle(ActionEvent e) {
				System.out.println("Button Clicked.");
				// Check login return true
				JDBCTest conn = new JDBCTest(); 
				String email = loginField.getText();
				String password = passwordField.getText();
				System.out.println(email);
				System.out.println(password);
				
				if(conn.checkUser(email, password)) {
					GUI gui = new GUI(); 
					try {
						gui.setScene();
						
						primaryStage.setScene(gui.getScene());
					} catch (Exception e1) {
						// TODO Auto-generated catch block
						e1.printStackTrace();
					}
				}
				else {
					// Add Alert
					
					// Pull up account creation page 
					CreateAccountGUI CAgui = new CreateAccountGUI();
					try {
						CAgui.setScene();
						primaryStage.setScene(CAgui.getScene());
						
					} catch(Exception e2) {
						e2.printStackTrace();
					}
				}
				
			}
		});
		
		cancelButton.setOnAction(new EventHandler<ActionEvent>() {
			@Override
			public void handle(ActionEvent e) {
				loginField.clear();
				passwordField.clear();
			}
		});
		
		// Create Menu 
		Menu file = new Menu("File");
		Menu help = new Menu("Help");
		
		// Shows List of books
		MenuItem showBooks = new MenuItem("Show Library");
		MenuItem addBook = new MenuItem("Add Book");
		
		file.getItems().addAll(showBooks, addBook);
		
		MenuBar menuBar = new MenuBar();
		menuBar.getMenus().addAll(file,help);
		
		// Set Action for show Menu item 
		showBooks.setOnAction(new EventHandler<ActionEvent>() {
		    public void handle(ActionEvent t) {
		    	
		        TableTest table = new TableTest(); 
		        primaryStage.setScene(table.getScene());
		    }
		});
		
		addBook.setOnAction(new EventHandler<ActionEvent>() {
		    public void handle(ActionEvent t) {
		    	GUI gui = new GUI();
		    	gui.setScene();
		    	primaryStage.setScene(gui.getScene());
		    }
		});
		
		//add to boarder pane 
		root.setTop(menuBar);
		root.setCenter(pane);
		
		
				
		primaryStage.setScene(loginScene);
		primaryStage.show();
		 
	}
	
	public static void main(String args[]) {
		launch(args);
	}
	
	/*
	 * Method to create Menu items and a MenuBar
	 * It then adds the Menu to the top of the boarder pane and the gridpane to the center 
	 */
	private void setMenu(BorderPane root, GridPane pane) {
		Menu file = new Menu("File");
		Menu help = new Menu("Help");
		
		// Shows List of books
		MenuItem show = new MenuItem("Show Library");
		
		file.getItems().add(show);
		
		MenuBar menuBar = new MenuBar();
		menuBar.getMenus().addAll(file,help);
		
		// Set Action for show Menu item 
		show.setOnAction(new EventHandler<ActionEvent>() {
		    public void handle(ActionEvent t) {
		       TableTest table = new TableTest(); 
		       table.getScene();
		    }
		});
		
		// add to boarder pane 
		root.setTop(menuBar);
		root.setCenter(pane);
	}
	
	
	
	
	public class GUI { 
		// GridPane and Scene
		private BorderPane root = new BorderPane();
	    private GridPane gridPane = new GridPane();
		private Scene scene = new Scene(root, 400, 400);
		
		// Text Labels
		private Text authorText = new Text("Author: ");
		private Text titleText = new Text("Title: ");
		private Text pagesText = new Text("Number of Pages: ");
		private Text timesReadText = new Text("Times read: ");
		
		// Text Fields
		private TextField authorField = new TextField(); 
		private TextField titleField = new TextField(); 
		private TextField pagesField = new TextField(); 
		private TextField timesReadField = new TextField(); 
		
		// Buttons
		private Button button1 = new Button("Submit"); 
	    private Button button2 = new Button("Clear");
	    
		
		
		private void setScene() {
			// Set min size 
			gridPane.setMinSize(400, 200);
			gridPane.setPadding(new Insets(10, 10, 10, 10));
			gridPane.setVgap(5);
			gridPane.setHgap(5);
			gridPane.setAlignment(Pos.CENTER);
			
			// Add nodes to grid
			gridPane.add(authorText, 0, 0);
			gridPane.add(authorField, 1, 0);
			gridPane.add(titleText, 0, 1);
			gridPane.add(titleField, 1, 1);
			gridPane.add(pagesText, 0, 2);
			gridPane.add(pagesField, 1, 2);
			gridPane.add(timesReadText, 0, 3);
			gridPane.add(timesReadField, 1, 3);
			gridPane.add(button1, 0, 4);
			gridPane.add(button2, 1, 4);
			
			// Add button event handles
			button1.setOnAction(new EventHandler<ActionEvent>() {
				@Override
				public void handle(ActionEvent e) {
					JDBCTest testSQL = new JDBCTest(); 
					String author = authorField.getText();
					String title = titleField.getText();
					int pages = Integer.parseInt(pagesField.getText());
					int timesRead = Integer.parseInt(timesReadField.getText()); 
					testSQL.addEntry(author, title, pages, timesRead);
				}
			});
			
			button2.setOnAction(new EventHandler<ActionEvent>() {
				@Override
				public void handle(ActionEvent e) {
					authorField.clear();
					titleField.clear();
					pagesField.clear();
					timesReadField.clear(); 
				}
			});
			
			setMenu(root, gridPane);
					
		}
		
		public Scene getScene() {
			return this.scene;
		}
		
	}

	public class TableTest {
		
		private TableView table = new TableView();
		
		// GridPane and Scene
		private BorderPane root = new BorderPane();
	    private GridPane gridPane = new GridPane();
		private Scene scene = new Scene(root, 400, 400);
		
		
		// Buttons
		private Button button1 = new Button("Submit"); 
	    private Button button2 = new Button("Clear");
		
		/* Build data for table from result set. 
		 * Makes database connection with JDBCTest class then runs a query (will add a method in JDBCTest class later) 
		 * Loops until set is empty adding data with each iteration
		 */
		private void tableData() {
			// Create class
			JDBCTest conn = new JDBCTest(); 
			Connection c = conn.connect();
			
			// Create SQL statement 
			String sql = "SELECT author, title, times_read FROM book";
			
			// Test to see if this is the right statement
			try {
				ResultSet rs = c.createStatement().executeQuery(sql);
				
				// Add table columns statically
				TableColumn<Map, String> authorColumn = new TableColumn<>("Author");
				authorColumn.setCellValueFactory(new MapValueFactory<>("author"));
				
				TableColumn<Map, String> bookColumn = new TableColumn<>("Title");
				bookColumn.setCellValueFactory(new MapValueFactory<>("title"));
				
				TableColumn<Map, Integer> timesReadColumn = new TableColumn<>("Times Read");
				timesReadColumn.setCellValueFactory(new MapValueFactory<>("read"));

				this.table.getColumns().addAll(authorColumn, bookColumn, timesReadColumn);	
				
				ObservableList<Map<String, Object>> row = FXCollections.<Map<String, Object>>observableArrayList();
				while(rs.next()) {
					Map<String, Object> bookInfo = new HashMap<>();
					bookInfo.put("author", rs.getString(1));
					bookInfo.put("title",rs.getString(2));
					bookInfo.put("read", rs.getInt(3));
					
					row.add(bookInfo);				
				}
				
				this.table.getItems().addAll(row);
				
			} catch(SQLException ex) {
				
			}
			
			System.out.println(table.toString());
		}

		
		public void setScene() {
			// Set min size 
			gridPane.setMinSize(400, 200);
			gridPane.setPadding(new Insets(10, 10, 10, 10));
			gridPane.setVgap(5);
			gridPane.setHgap(5);
			gridPane.setAlignment(Pos.CENTER);
			
			// Set table size
			table.setPrefSize(280,300);
		
			
			// Add button event handles
			button1.setOnAction(new EventHandler<ActionEvent>() {
				@Override
				public void handle(ActionEvent e) {
					System.out.println("show");
				}
			});
			
			button2.setOnAction(new EventHandler<ActionEvent>() {
				@Override
				public void handle(ActionEvent e) {
				
				}
			});
			
			// Create table
			tableData(); 
				
			// Add Nodes
			gridPane.add(table,0,0);
			gridPane.add(button1, 0, 1);
			
			// Add Menu 
			Menu file = new Menu("File");
			Menu help = new Menu("Help");
			
			// Shows List of books
			MenuItem showBooks = new MenuItem("Show Library");
			MenuItem addBook = new MenuItem("Add Book");
			
			file.getItems().addAll(showBooks, addBook);
			
			MenuBar menuBar = new MenuBar();
			menuBar.getMenus().addAll(file,help);
			
			// Set Action for show Menu item 
			showBooks.setOnAction(new EventHandler<ActionEvent>() {
			    public void handle(ActionEvent t) {
			    	
			    }
			});
			
			addBook.setOnAction(new EventHandler<ActionEvent>() {
			    public void handle(ActionEvent t) {
			    	
			    }
			});
			
			setMenu(root, gridPane);

		}

		public Scene getScene() {
			setScene();
			return this.scene; 
		}
	}
}
