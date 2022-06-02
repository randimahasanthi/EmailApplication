# EmailApplication
Simple Email Application for the company IT department
import java.util.Scanner;

public class EmailAccount {
	//We define variables as private to keep sensitive data secure
	//We can access private variables only within the defined class.
	//If need to access in another class, get or set methods are used
	
	private String firstName;
	private String lastName;
	private String password;
	private int defaultPasswordLength = 10; //default value
	private String department;
	private String email;
	private String companySuffix = ".xyzcompany.com";
	private int mailBoxCapacity = 500; //default value
	private String alternativeEmail;

		//constructor to receive the first name and last name
		public EmailAccount(String firstName, String lastName) {
			this.firstName = firstName;
			this.lastName = lastName;
			//System.out.println("Email Created: " + this.firstName + " " + this.lastName );
			
			//call the setDepartment method to return the department
			department = setDepartment();
			//System.out.println("Department name: " + department);
			
			//call the setRandomPassword method to return a random password
			password = setRandomPassword(defaultPasswordLength);
			System.out.println("Your random password is: " + password);
			
			//Generate the email address
			email =  this.firstName.toLowerCase() + "." + this.lastName.toLowerCase() + "@" + department.toLowerCase() + companySuffix ;
			//System.out.println("Your email address is: " + email);
			
		}
		
		//method to Ask for the department - Encapsulation is used
		public String setDepartment() {
			System.out.println("Enter the Department: \n 1: Sales \n 2: Engineering \n 3: Admin \n 0: None");
			Scanner sc = new Scanner(System.in); //create a scanner object to get input
			int departmentIndex = sc.nextInt(); //departmentIndex can not be String as we are requesting char at 0
			if (departmentIndex == 1) {
				return "Sales";
			} else if (departmentIndex == 2) {
				return "Engineering";
			} else if (departmentIndex == 3) {
				return "Admin";
			} else {
				return "\0"; //This means null value, not zero
			} 
		}
		
		//Generate a random string for password
		public String setRandomPassword(int passwordLength) {
			String passwordCharacters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%";
			char[] passwordArray = new char[passwordLength]; //create an array with null values
			
			for (int i=0; i < passwordLength; i++) {
				int randomIndex = (int) (Math.random() * passwordCharacters.length()) ; // 0 to 41
				passwordArray[i] = passwordCharacters.charAt(randomIndex);
			}
			String password = new String(passwordArray);  //char array is converted to a string using a String object
			return password;
		}
		
		
		
		//SET method to the mail box capacity - Encapsulation is used
		public void setMailBoxCapacity(int capacity) {
			mailBoxCapacity = capacity;
		}
		//SET method to an alternative email - Encapsulation is used
		public void setAlternativeEmail(String altEmail) {
			alternativeEmail = altEmail;
		}
		
		//method to change the password - this is not a SET method
		public void changePassword(String password) {
			this.password = password;
		}
		
		
		
		//GET method to display mail box capacity
		public int getMailBoxCapacity() {
			return mailBoxCapacity;
		}
		
		//GET method to display email
		public String getAlternativeEmail() {
				return alternativeEmail;
		}
		
		
		//Method to display name, email, mailbox capacity
		public String showInfo() {
			return "DISPLAY NAME: " + firstName + " " + lastName  + "\n" +
					"COMPANY EMAIL: " + email + "\n" +
					"MAILBOX CAPACITY: " + getMailBoxCapacity() ;		
			//when something is returned, it's not printer. For that we need to println
		}
		
		
}
