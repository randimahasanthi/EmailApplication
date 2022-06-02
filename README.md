# EmailApplication
Simple Email Application for the company IT department


public class EmailApplication {
	
	public static void main(String[] args) {
		//create an object from EmailAccount class
		EmailAccount em = new EmailAccount("Randima", "Hasanthi"); //once the object is created, constructor is called
		
		em.setMailBoxCapacity(200);
		//em.setAlternativeEmail("randima@ieee.org");
		//System.out.println("Your alternative email is: " + em.getAlternativeEmail());
		
		System.out.println(em.showInfo());
	}
	
	
	
}
