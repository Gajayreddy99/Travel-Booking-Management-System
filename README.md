import java.util.Random;
import java.util.Scanner;
class loginp 
{
    static Scanner sc = new Scanner(System.in);
    private String username = "CV@212";
    private String password = "CV@212";
    private long mobilenumber = 9876543210L;
    void setname(String username)
    {
        this.username = username;
    }
    void setpass(String password) 
    {
        this.password = password;
    }
    void setnum(long mobilenumber) 
    {
        this.mobilenumber = mobilenumber;
    }
    String getname() 
    {
        return username;
    }
    String getpass()
    {
        return password;
    }
    long getnum()
    {
        return mobilenumber;
    }

    loginp(String username, String password, long mobilenumber)
    {
        this.username = username;
        this.password = password;
        this.mobilenumber = mobilenumber;
    }
    loginp()
    {
        
    }
}
class logina extends loginp 
{
    static loginp x = new loginp();
    static logina xp = new logina();
    static Random rand = new Random();
    int generateOTP() 
    {
        return 1000 + rand.nextInt(8999); 
    }
    void signup()
    {
        System.out.println("============= SIGN UP =============");
        System.out.print("Enter username: ");
        String uname = sc.next();
        System.out.print("Enter password: ");
        String pass = sc.next();
        System.out.print("Enter mobile number: ");
        long mob = sc.nextLong();
        if(mob < 7000000000L || mob > 9999999999L) 
        {
             System.out.println("Invalid mobile number! Signup failed.");
             xp.signup();
        }
        int otp = generateOTP();
        System.out.println("OTP sent to your mobile: " + otp); 
        System.out.print("Enter the OTP: ");
        int enteredOtp = sc.nextInt();
        if (enteredOtp != otp) 
        {
            System.out.println("Invalid OTP. Signup failed.");
            xp.signup();
        }
        x.setname(uname);
        x.setpass(pass);
        //x.setnum(mob);
        System.out.println("Account created successfully!");
        System.out.println("Do you want to login now? (yes/no)");
        String choice = sc.next();
        if (choice.equalsIgnoreCase("yes"))
        {
            xp.login();
        } 
        else 
        {
            System.out.println("Thank you for signing up!");
        }
    }
    void login() 
    {
        System.out.print("Enter username: ");
        String user = sc.next();
        System.out.print("Enter password: ");
        String pass = sc.next();
        if (user.equals(x.getname()) && pass.equals(x.getpass())) 
        {
            int otp = generateOTP();
            System.out.println("OTP sent to your mobile: " + otp);
            System.out.print("Enter OTP: ");
            int enteredOtp = sc.nextInt();
            if (enteredOtp == otp)
            {
                System.out.println("Login successful!");
                serviceprovider();
            } 
            else 
            {
                System.out.println("Incorrect OTP. Login failed.");
                xp.login();
            }
        } 
        else if (!user.equals(x.getname()) && pass.equals(x.getpass()))
        {
            System.out.println("Incorrect username");
            System.out.println("Do you want to reset your username(Yes/No)");
            String p = sc.next();
            if (p.equalsIgnoreCase("yes"))
            {
                System.out.print("Enter new username: ");
                x.setname(sc.next());
                System.out.println("Username updated");
                System.out.println("Do you want to go login page(Yes/No)");
                String lo = sc.next();
                if (lo.equalsIgnoreCase("yes"))
                {
                    xp.login();
                } 
                else
                {
                    System.out.println("Thank you");
                }
            } 
            else
            {
                System.out.println("Thank you");
            }
        } 
        else if (user.equals(x.getname()) && !pass.equals(x.getpass())) 
        {
            System.out.println("Incorrect password");
            System.out.println("Do you want to reset your password(Yes/No)");
            String p = sc.next();
            if (p.equalsIgnoreCase("yes"))
            {
                System.out.print("Enter new password: ");
                x.setpass(sc.next());
                System.out.println("Password updated");
                System.out.println("Do you want to go login page(Yes/No)");
                String lo = sc.next();
                if (lo.equalsIgnoreCase("yes"))
                {
                    xp.login();
                } 
                else
                {
                    System.out.println("Thank you");
                }
            } 
            else
            {
                System.out.println("Visit again");
            }
        } 
        else if (!user.equals(x.getname()) && !pass.equals(x.getpass()))
        {
            System.out.println("Incorrect credentials");
            System.out.println("Do you want to reset your credentials(Yes/No)");
            String p = sc.next();
            while (p.equalsIgnoreCase("yes")) 
            {
                System.out.println("Enter your phone number:");
                long pp = sc.nextLong();
                if(pp < 7000000000L || pp > 9999999999L) 
                {
                    System.out.println("Invalid mobile number! Signup failed.");
                    xp.login();
                }
                if (pp == (x.getnum()))
                {
                    System.out.println("Your username is: " + x.getname());
                    System.out.println("Do you want to go login page(Yes/No)");
                    String c = sc.next();
                    if (c.equalsIgnoreCase("yes"))
                    {
                        xp.login();
                    } 
                    else 
                    {
                        System.out.println("Thank you visit again:)");
                        break;
                    }
                } 
                else
                {
                    System.out.println("User not found");
                }
                
            }
        }
    }
    void serviceprovider()
    {
    
        System.out.println("Select the service provider\n 1.Abhi bus\n 2.Red bus\n 3.Make My Trip\n 4.Booking.com\n");
        System.out.println("Press any other key to exit");
        int pc = sc.nextInt();
    
        if (pc == 1)
        {
        String RESET = "\u001B[0m";
        String RED = "\u001B[31m";
        String GREEN = "\u001B[32m";
        String YELLOW = "\u001B[33m";
        String BLUE = "\u001B[34m";
        String PURPLE = "\u001B[35m";
        String CYAN = "\u001B[36m";

    
        String asciiArt =
                "            _____  ___    _   _  _     ___    _   _  ___   \n" +
        RED+    "           (  _  )(  _`\\ ( ) ( )(_)   (  _`\\ ( ) ( )(  _`\\ \n" +
    YELLOW+      "          | (_) || (_) )| |_| || |   | (_) )| | | || (_(_)\n" +
    GREEN+       "          |  _  ||  _ <'|  _  || |   |  _ <'| | | |`\\__ \\ \n" +
    BLUE+        "          | | | || (_) )| | | || |   | (_) )| (_) |( )_) |\n" +
    CYAN+        "          (_) (_)(____/'(_) (_)(_)   (____/'(_____)`\\____)\n" +
    RESET+           "                                                      \n" +
                "                                                           \n";

        // Apply green + blink + reset
        System.out.println( asciiArt);
            user u=new user();
    		u.login();
    		//System.out.println(".........................WELCOME TO ABHIBUS........................................");
    		System.out.println(GREEN +
    "    +-----------------------------------------------------------+\n" +
    "    |                       WELCOME TO ABHIBUS                  |\n" +
    "    +-----------------------------------------------------------+\n" +
    RESET);

    		while(true)
    		{
    			System.out.println("Press \n 🚍 1.Bus Booking \n 🚆 2.Train Booking \n 🛫 3.Flight Booking \n ➡️  4.Exit"
);
                int a=sc.nextInt();
    			if(a==1)
    			{
    		       		u.BusBooking();
    				
    			}
    			else if(a==2)
    			{
    		    		u.TrainBooking();
    				
    			}
    			else if(a==3)
    			{
    		    		u.FlightBooking();
    			}
    			else if(a==4)
    			{
    			    System.out.println("Thank you for choosing ABHI bus.");
    			    
    			    System.out.println("Do you want to Book Tickets🎟🎟️️(press 1 or any key)");
    			    int r=sc.nextInt();
    			    if(r==1)
    			    {
    			        serviceprovider();
    			    }
    			    else
    			    {
    			        System.out.println("Thank you ! please visit again");
    			        break;
    			    }
    			}
    			else
    			{
    		    		System.out.println("Invalid Input!Please Try again");
    		    		break;
    			}
            }
        }
        else if (pc == 2)
        {
            String RESET = "\u001B[0m";
        String RED = "\u001B[31m";
        String GREEN = "\u001B[32m";
        String YELLOW = "\u001B[33m";
        String BLUE = "\u001B[34m";
        String PURPLE = "\u001B[35m";
        String CYAN = "\u001B[36m";

         String asciiArt =
RED +  "             ___    ___    ___       ___    _   _  ___   \n" +
GREEN + "           |  _`\\ (  _`\\ (  _`\\    (  _`\\ ( ) ( )(  _`\\ \n" +
YELLOW + "          | (_) )| (_(_)| | ) |   | (_) )| | | || (_(_)\n" +
BLUE +   "          | ,  / |  _)_ | | | )   |  _ <'| | | |`\\__ \\ \n" +
PURPLE + "          | |\\ \\ | (_( )| |_) |   | (_) )| (_) |( )_) |\n" +
CYAN +   "          (_) (_)(____/'(____/'   (____/'(_____)`\\____)\n" +
RESET +  "                                                       \n" +
"                                                        \n";


        System.out.println(asciiArt);
        
        System.out.println(RED +
    "    +-----------------------------------------------------------+\n" +
    "    |                       WELCOME TO REDBUS                   |\n" +
    "    +-----------------------------------------------------------+\n" +
    RESET);

            System.out.println("WELCOME TO REDBUS BOOKING!!!");
             
            while (true)
            {
                System.out.print("Enter your phone number: ");
            long  phone = sc.nextLong();
            if(phone < 7000000000L || phone > 9999999999L) 
                {
                    System.out.println("Invalid mobile number! Signup failed.");
                    continue;
                }
                
    
            Random rand = new Random();
            int otp = 1000 + rand.nextInt(9000);
            System.out.println("OTP sent to " + phone + ": " + otp);
    
                System.out.print("Enter OTP: ");
                int enteredOtp = sc.nextInt();
                sc.nextLine();
                if (enteredOtp == otp) {
                    System.out.println("Login Successful!\n");
                    break;
                } 
                else {
                    System.out.println("Invalid OTP.\nPlease! Try again.");
                    this.login();
                }
            }
    
            Booking booking;
            while (true) {
                System.out.println("\n============================= Red Bus =============================");
                System.out.println("Welcome ! Choose your booking module:");
                System.out.println("1. Bus Booking");
                System.out.println("2. Train Booking");
                System.out.println("3. Flight Booking");
                System.out.println("4. Exit");
                System.out.print("Enter your choice: ");
                int choice = sc.nextInt();
                sc.nextLine();
                if (choice == 1)
                    booking = new BusBooking();
                else if (choice == 2)
                    booking = new TrainBooking();
                else if (choice == 3)
                    booking = new FlightBooking();
                else if (choice == 4) 
                {
                    System.out.println("Thank you for using Red Bus Booking System. Have a Safe Journey!");
                     System.out.println("Do you want to Book Tickets(press 1 or any key)");
    			    int r2=sc.nextInt();
    			    if(r2==1)
    			    {
    			        serviceprovider();
    			    }
    			    else
    			    {
    			        System.out.println("Thank you ! please visit again");
    			        break;
    			    }
                    break;
    			}
    	
                
                else 
                {
                    System.out.println("Invalid choice. Try again.");
                    continue;
                }
    
                booking.bookTicket();
            }
    
        }
    else if (pc == 3)
        {
            MakeMyTrip obj = new MakeMyTrip();
            while(true)
            {
                obj.DisplayLogo();
                obj.MobileNumber();
                obj.NumberValidation(obj.number);
                if(!obj.NV)
                {
                    System.out.println("You Want to Enter the Mobile Number Again type 1 You want to exit Type 2");
                    int option1 =sc.nextInt();
                    if(option1==1||option1==2)
                    {
                        if(option1==1)
                        {
                            obj.MobileNumber();
                            obj.NumberValidation(obj.number);
                            obj.NV=true;
                        }
                        else{
                            System.out.println("Thank You Visit Again :)");
                            obj.NV=false;
                        }
                    }
                    else
                    {
                        System.out.println("You Entered Invalid Option Thank You Visit Again :)");
                        obj.NV=false;
                    }
                }
                if(obj.NV) 
                {
                    obj.OTPVerification();
                }
                if(obj.NV) 
                {
                    obj.DisplayCity();
                    obj.Display1();
                    if(obj.a<1 ||obj.a>20 || obj.b<1||obj.b>20|| obj.b==obj.a) 
                    {
                        if(obj.a==obj.b) 
                        {
                            System.out.println("OOPs! You Entered SAME SOURCE AND DESTINATION CITY");
                        }
                        else if(obj.a<1||obj.a>20)
                        {
                            System.out.println("You Entered Invalid Source City");
                        }
                        else
                        {
                            System.out.println("You Entered Invalid Destination City");
                        }
                        System.out.println("If you Want enter Again Type '1'");
                        int a2=sc.nextInt();
                        if(a2==1)
                        {
                            obj.Display1();
                        }
                    }
                    System.out.println("Number of People Travel:");
                    int b3 = sc.nextInt();
                    obj.NPT=b3;
                    obj.name = new String[obj.NPT];
                    obj.age = new int[obj.NPT];
                    obj.Gender=new String[obj.NPT];
                    obj.Type = new String[obj.NPT];
                    obj.PassengerDetails();
                    obj.Display2();
                    int c = sc.nextInt();
                    if(c==1)
                    {
                        obj.FlightFair(obj.a,obj.b);
                    }
                    else if(c==2)
                    {
                        obj.TrainFair(obj.a,obj.b);
                    }
                    else if(c==3)
                    {
                        obj.BusFair(obj.a,obj.b);
                    }
                    obj.sendTicketToMobile();
                    obj.OtherOptions();
                }
                System.out.println("Do you want to Book Tickets again? (1 = Yes, 0 = No)");
                int r2 = sc.nextInt();
                if (r2 != 1) {
                    System.out.println("Thank you! Please visit again.");
                    break;
                }
                 else
                 {
                    serviceprovider();
                 }
            }
        }
        else if (pc == 4)
        {
                        String RESET = "\u001B[0m";
                    String RED = "\u001B[31m";
                    String GREEN = "\u001B[32m";
                    String YELLOW = "\u001B[33m";
                    String BLUE = "\u001B[34m";
                    String PURPLE = "\u001B[35m";
                    String CYAN = "\u001B[36m";
                    String WHITE = "\u001B[37m";
                      // bright purple
                   
            
String asciiArt =
    RED +  "             ___    _____  _____  _   _  _  _   _  ___       ___    _____        \n" +
    GREEN + "           (  _`\\ (  _  )(  _  )( ) ( )(_)( ) ( )(  _`\\    (  _`\\ (  _  )/'\\_/`\\\n" +
    YELLOW + "          | (_) )| ( ) || ( ) || |/'/'| || `\\| || ( (_)   | ( (_)| ( ) ||     |\n" +
    BLUE +  "           |  _ <'| | | || | | || , <  | || , ` || |___    | |  _ | | | || (_) |\n" +
    PURPLE +"           | (_) )| (_) || (_) || |\\`\\ | || |`\\ || (_, ) _ | (_( )| (_) || | | |\n" +
    CYAN +  "           (____/'(_____)(_____)(_) (_)(_)(_) (_)(____/'(_)(____/'(_____)(_) (_)\n" +
    WHITE + "                                                                     \n" +
    "                                                                     \n" +
    RESET;
            
                    System.out.println(asciiArt);
                    System.out.println(PURPLE+"WELCOME TO BOOKING.COM!!!"+RESET);
            
            
            // Big ASCII banner (red)
            System.out.println(RED +
            
            "    +-----------------------------------------------------------+\n" +
            "    |                   WELCOME TO BOOKING.COM!!!               |\n" +
            "    +-----------------------------------------------------------+\n" +
            RESET);
                  //  System.out.println("WELCOME TO BOOKING.COM!!!");
        while(true)
        {
            System.out.print("Enter your phone number: ");
            long phone = sc.nextLong();
            if(phone < 7000000000L || phone > 9999999999L) 
                {
                    System.out.println("Invalid mobile number! Signup failed.");
                    continue;
                }
            Random r = new Random();
            int otp = 1000 + r.nextInt(9000);
            System.out.println("OTP sent to " + phone + ": " + otp);
            
            // OTP verification loop
            boolean verified = false;
            while (!verified) {
                System.out.print("Enter OTP: ");
                int enteredOtp = sc.nextInt();
                sc.nextLine();
                if (enteredOtp == otp) {
                    System.out.println("Login Successful!\n");
                    verified = true;
                } 
                else
                {
                    System.out.println("Invalid OTP. Please try again.\n");
                }
            }
            System.out.println("Do you want to Book Tickets? (1 = Yes, 0 = No)");
            int rb = sc.nextInt();
            if (rb == 1)
            {
                PBooking booking;
                while (true) {
                    System.out.println("\n============================= Booking.com =============================");
                    System.out.println("Welcome ! Choose your booking module:");
                    System.out.println("1. Bus Booking");
                    System.out.println("2. Train Booking");
                    System.out.println("3. Flight Booking");
                    System.out.println("4. Exit");
                    System.out.print("Enter your choice: ");
                    int choice = sc.nextInt();
                    sc.nextLine();
            
                    if (choice == 1)
                        booking = new PBusBooking();
                    else if (choice == 2)
                        booking = new PTrainBooking();
                    else if (choice == 3)
                        booking = new PFlightBooking();
                    else if (choice == 4) 
                    {
                        System.out.println("Thank you for using Booking.com. Have a Safe Journey!");
                         System.out.println("Still Do you want to Book Tickets(0/1)");
            			    int r2=sc.nextInt();
            			    if(r2==1)
            			    {
            			        serviceprovider();
            			    }
            			    else
            			    {
            			        System.out.println("Thank you ! please visit again");
            			        break;
            			    }
                            continue;
                    } 
                    
                    else
                    {
                        System.out.println("Thank you ! please visit again.");
                        return;
                    }
                    booking.PbookTicket();
                }
            } 
            else
            {
                System.out.println("Thank you for Visting");
            }
    
        }
      
}
}

 public static void main(String[] args)
 {
        //showAsciiArt(); 
        System.out.println("Welocome to CVTRIP*");
        
        System.out.println("Enter the choice:");
        System.out.println("                            ----------------                         ----------------");
        System.out.println("                            |   1.Signup   |                         |    2.Login   |");
        System.out.println("                            ----------------                         ----------------");
        int n = sc.nextInt();
        
        if (n == 1) 
        {
            new logina().signup();
        }
        else if (n == 2)
        {
            new logina().login();
        } 
        else 
        {
            System.out.println("Invalid choice!Press any key to re-attempt");
            main(args);
        }
    }
}
class Abhibus
{
	//private long mobile_no=9876543210L;
	private String username="CV@212";
	private String password="CV@212";
	String getusername()
	{
	    return username;
	}
	String getpassword()
	{
	    return password;
	}
	int otp()
	{
		int otp=1000+(int)(Math.random()*8999);
		System.out.println("Your otp is: "+otp);
		return otp;
	}

}
class fareCalculator
{
	int getBusFare(int from,int to)
	{
		if(from==1 && to==2) return 600;
		else if(from==1 && to==3) return 700;
		else if(from==1 && to==4) return 800;
		else if(from==1 && to==5) return 900;
		else if(from==1 && to==6) return 1000;
		else if(from==1 && to==7) return 1100;
		else if(from==1 && to==8) return 1200;
		else if(from==1 && to==9) return 1100;
		else if(from==1 && to==10) return 1400;

	
		else if(from==2 && to==1) return 600;
		else if(from==2 && to==3) return 700;
		else if(from==2&& to==4) return 800;
		else if(from==2 && to==5) return 900;
		else if(from==2 && to==6) return 1000;
		else if(from==2 && to==7) return 1100;
		else if(from==2 && to==8) return 1200;
		else if(from==2 && to==9) return 1100;
		else if(from==2 && to==10) return 1400;
		
		else if(from==3 && to==1) return 600;
		else if(from==3 && to==2) return 700;
		else if(from==3&& to==4)  return 800;
		else if(from==3 && to==5) return 900;
		else if(from==3 && to==6) return 1000;
		else if(from==3 && to==7) return 1100;
		else if(from==3 && to==8) return 1200;
		else if(from==3 && to==9) return 800;
		else if(from==3 && to==10) return 700;

		else if(from==4 && to==1) return 600;
		else if(from==4 && to==2) return 700;
		else if(from==4 && to==3) return 800;
		else if(from==4 && to==5) return 900;
		else if(from==4 && to==6) return 1000;
		else if(from==4 && to==7) return 1100;
		else if(from==4 && to==8) return 1200;
		else if(from==4&& to==9) return 1100;
		else if(from==4 && to==10) return 900;
		
		else if(from==5 && to==1) return 600;
		else if(from==5 && to==2) return 700;
		else if(from==5 && to==3) return 800;
		else if(from==5 && to==4) return 900;
		else if(from==5 && to==6) return 1000;
		else if(from==5 && to==7) return 1100;
		else if(from==5 && to==8) return 1200;
		else if(from==5&& to==9) return 1100;
		else if(from==5 && to==10) return 900;
		
		else if(from==6 && to==1) return 600;
		else if(from==6 && to==2) return 700;
		else if(from==6 && to==3) return 800;
		else if(from==6 && to==4) return 900;
		else if(from==6 && to==5) return 1000;
		else if(from==6 && to==7) return 1100;
		else if(from==6 && to==8) return 1200;
		else if(from==6&& to==9) return 1100;
		else if(from==6 && to==10) return 900;

		else if(from==7 && to==1) return 600;
		else if(from==7 && to==2) return 700;
		else if(from==7 && to==3) return 800;
		else if(from==7 && to==4) return 900;
		else if(from==7 && to==5) return 1000;
		else if(from==7 && to==6) return 1100;
		else if(from==7 && to==8) return 1200;
		else if(from==7&& to==9) return 1100;
		else if(from==7 && to==10) return 900;
		

		else if(from==8 && to==1) return 600;
		else if(from==8 && to==2) return 700;
		else if(from==8 && to==3) return 800;
		else if(from==8 && to==4) return 900;
		else if(from==8 && to==5) return 1000;
		else if(from==8 && to==6) return 1100;
		else if(from==8 && to==7) return 700;
		else if(from==8&& to==9) return 1100;
		else if(from==8 && to==10) return 900;
	
	
		else if(from==9 && to==1) return 600;
		else if(from==9 && to==2) return 700;
		else if(from==9 && to==3) return 800;
		else if(from==9 && to==4) return 900;
		else if(from==9 && to==5) return 1000;
		else if(from==9 && to==6) return 1100;
		else if(from==9 && to==7) return 700;
		else if(from==9&& to==8) return 1100;
		else if(from==9 && to==10) return 900;

		else
				return 0;

	}
}
class user
{
     String RESET = "\u001B[0m";
                    String RED = "\u001B[31m";
                    String GREEN = "\u001B[32m";
                    String YELLOW = "\u001B[33m";
                    String BLUE = "\u001B[34m";
                    String PURPLE = "\u001B[35m";
                    String CYAN = "\u001B[36m";
                    String WHITE = "\u001B[37m";
	static Scanner sc=new Scanner(System.in);
	Abhibus a=new Abhibus();
	int fare;
	int norfare;
	void login()
	{
	    while(true)
		{
		System.out.print("📱 Enter your mobile number to Login:+91 ");
		long mobile=sc.nextLong();
// 		if(mobile==(a.getmobile()))
// 		{
            if(mobile < 7000000000L || mobile > 9999999999L) 
                {
                    System.out.println("Invalid mobile number! Signup failed.");
                    continue;
                }
			int newotp=a.otp();
			System.out.println("Enter your otp: ");
			int ottp=sc.nextInt();
			if(ottp==newotp)
			{
				System.out.println("*Otp verified");
				System.out.println("..........................Login Successfully..................................");
				break;
			}
			else
			{
			System.out.println(PURPLE+"Invalid Otp!please try again");
			this.login();
			}
		}
	
		
	}
	void BusBooking()
	 {
		System.out.println("1.Hyderabad    2.Bangalore     3.Chennai");
		System.out.println("4.Mumbai       5.Delhi         6.Kolkata");
		System.out.println("7.Pune         8.Ahmedabad     9.Jaipur");
		System.out.println();
		System.out.println("📍 Enter Boarding Point: ");
		int from=sc.nextInt();
		System.out.println("📍 Enter Dropping Point: ");
		int to=sc.nextInt();
		fareCalculator f=new fareCalculator();
		if(from==to)
		{
			System.out.println("Your Boarding point and Dropping point are same! No need to Book any Tickets");
			System.out.println("Press 1.Booking 2.exit");
			int a=sc.nextInt();
			if(a==1)
			{
				BusBooking();
			}
			else
			{
				System.out.println(".........................THANK YOU FOR CHOOSING ABHIBUS 🤝............................");
			}
		}
		else if(from>=1&& from<=9 && to>=1 && to<=9)
		{
	    		fare=f.getBusFare(from,to);
			System.out.println(" 👥 Enter Number of Passengers: ");
			int passengers=sc.nextInt();
			norfare=fare;
			fare=fare*passengers;
			for(int i=1;i<=passengers;i++)
			{
    			System.out.println("Passenger " + i + ":");
                System.out.print(" 👤 Name: ");
                String name = sc.next();
                System.out.print(" 📅 Age: ");
                int age = sc.nextInt();
                sc.nextLine();
				System.out.println("Press \n1.🪟 💺 window seat\n Any key for 💺 Normal Seat");
				char n=sc.next().charAt(0);
				if(n=='1')
				{
					System.out.println(" ✅ Window seat Resereved for "+i+" passenger");
				}
				else
				{
					System.out.println(" ✅Normal Seat reserved for "+i+" passenger");
				}
			}
			amount();
		}
		else
		{
			System.out.println("⚠️ OOPS!:)Invalid!Input Please try again");
			System.out.println();
			BusBooking();
		}
	}
	 void TrainBooking()
	 {
	     while(true)
		{
	     		System.out.println("👤 Enter Your IRCTC Username: ");
	     		String username=sc.next();
	     		System.out.println("🔑 Enter Your IRCTC password: ");
	     		String password=sc.next();
	  		if(username.equals(a.getusername())&&password.equals(a.getpassword())) 
	  		{
	      
	            		BusBooking();
	            		return;
	  		}
	  		else
			{
	      		System.out.println("Invalid!Input");
	        }
	   	 }
	 }
	  void FlightBooking()
	 {
        	System.out.println(".................................WELCOME TO THE AIR INDIA FLIGHT BOOKING............................");
        	BusBooking();
    	}

	 void amount()
	 {
	     
		System.out.println("💺 seat fare: "+norfare);
		System.out.println("💵 Total fare: "+fare);
		float gst=fare/50f;
		System.out.println("💲 GST is: "+gst);
		System.out.println("💵 Total Amount: "+(fare+gst));
		Payment p = new Payment();
        p.pay(fare);
		System.out.println(".........................👉 THANK YOU FOR CHOOSING ABHIBUS............................");
		
	 }
}
class MakeMyTrip
{
    
    static Scanner sc = new Scanner(System.in);
    int a,b;
    long number;
    boolean NV;
    int NPT;
    String[] name = new String[NPT];
    int[] age = new int[NPT];
    String[] Gender = new String[NPT];
    String[] Type = new String[NPT];
    double TicketPrice = 0.0f;
    double gst=0.0f;
    double ServiceTax=0.0f;
    static int otp = (int)(100000 + Math.random() * 900000);
    void MobileNumber()
    {
        System.out.println("Enter Your Valid Mobile Number:");
        long number1=sc.nextLong();
        number=number1;
    }
    void PassengerDetails()
    {
        for(int i=0;i<NPT;i++)
            {
                System.out.println("Enter  Details Of Passenger "+(i+1)+" :");
                System.out.println("Name :");
                name[i]=sc.next();
                System.out.println("Gender(M/F) :");
                Gender[i]=sc.next();
                System.out.println("Age : ");
                age[i]=sc.nextInt();
                System.out.println("Entered Prefferd Seat Type Window(W) or Normal(N)");
                Type[i]=sc.next();
            }
    }
    void NumberValidation(long number)
    {
        if(number>5999999999l&&number<10000000000l)
        {
            System.out.println("You Entered Valid Mobile And OTP send to Your Mobile");
            System.out.println("Your 6-digit OTP is "+otp+" to login MakeMyTrip");
            NV=true;
        }
        else{
            System.out.println("you Entered inappropriate Number");
            NV=false;
        }
    }
    void DisplayLogo()
    {
        String RESET = "\u001B[0m";
        String RED = "\u001B[31m";
        String WHITE = "\u001B[37m";
        String BLUE = "\u001B[34m";
        String[] art = {
            "....................................................................................................",
            "....................................................................................................",
            "..............................................-==--===--===--===--:................................",
            "...........................................-*************************+..............................",
            "..........................................+****************************:............................",
            ".........................................=*****************************+............................",
            ".........................................=*****************************+...............:............",
            ".......................:#+...............=***+..-**+..**++****..***=.=*+...:*.........=*............",
            "..+*:*#*::##*...+###=..:#+..##-..+##+....=**+.:.-*-..+*:..***..=**=.-**+..####*.+*.*#:+#..*=-##*....",
            "..+#+.:##=.-#*.:-..:#*.:#+-#*..=#+..*#:..=****=.+....+...-**..-**-.:***+...#*...+##-..*#..##+..##-..",
            "..+#:..##...#*.=#*+=#*.:#*##:..%#*****=..=****....=.-..:.++...**-.:****+...#*...*#....*#..#%...:#+..",
            "..+#:..##...#*.+#*+##*.:#+.=#*..##*+*#...=***+..-*:..-*:.:.=..:..:*****+...##*+.+#:...*#..###+*##:..",
            "...:....:...::...:.......................=***..=**..***:.:**+...:******+..................#%..:.....",
            ".........................................=********************..+******+..................#%........",
            ".........................................=*******************-.-*******+............................",
            ".........................................-*******************..=*******=............................",
            "..........................................-******************-.:******+.............................",
            "............................................+************************:..............................",
            "...................................................................................................."
        };

        try {
            for (String line : art) {
                StringBuilder coloredLine = new StringBuilder("\t\t");
                for (int i = 0; i < line.length(); i++) {
                    char ch = line.charAt(i);
                    if (ch == '.') {
                        coloredLine.append(RED).append('.').append(RESET);
                    } else {
                        coloredLine.append(ch);
                    }
                }
                System.out.println(coloredLine);
                Thread.sleep(360); 
            }
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
    void OTPVerification()
    {
        int optEntered=sc.nextInt();
        if(optEntered==otp)
        {
            System.out.println("You Login is done Successfully");
            NV= true;
        }
        else
        {
            System.out.println("Enter Invalid OTP Thank you :)");
            NV=false;
        }
    }
    void DisplayCity()
    {
        System.out.println("Avaiable Cities:");
        System.out.println("\t\t 1.Thiruvanthapuram     11.Goa");
        System.out.println("\t\t2.Chennai              12.Ahmedabad");
        System.out.println("\t\t3.Bengaluru            13.Jaipur");
        System.out.println("\t\t4.Hyderabad            14.Delhi");
        System.out.println("\t\t5.Amaravathi          15.Lucknow");
        System.out.println("\t\t6.Visakhaptnam        16.Patna");
        System.out.println("\t\t7. Bhubaneswar        17.Ranchi");
        System.out.println("\t\t8.Raipur              18.Kolkata");
        System.out.println("\t\t9.Bhopal              19.Shimla"); 
        System.out.println("\t\t10.mumbai             20.Leh");
    }
    void Display1()
    {
        System.out.println("Enter Source City Code: ");
        int a1=sc.nextInt();
        a=a1;
        System.out.println("Enter Destination City Code:");
        int b1 = sc.nextInt();
        b=b1;
    }
    void Display2()
    {
        System.out.println("Choose the Mode of Transportation: ");
        System.out.println("1.Flight\t 2.Train \t 3.Bus");
    }
    void BusFair(int a, int b) {
    System.out.println("For Seater Type '1'\t For Sleeper Type '2'");
    int b2 = sc.nextInt();
    if (b2 == 1) {
        float base = (float) (Math.abs(a - b) * 320.6);
        gst = 18 * base / 100;
        ServiceTax = 23.87 * Math.abs(a - b) * NPT;
        TicketPrice = (float) (base + gst + ServiceTax);
    } else if (b2 == 2) {
        float base = (float) (Math.abs(a - b) * 510.9);
        gst = 18 * base / 100;
        ServiceTax = 33.97 * Math.abs(a - b) * NPT;
        TicketPrice = (float) (base + gst + ServiceTax);
    }
    System.out.printf("Total: %.2f (including GST: %.2f and Service Tax: %.2f)%n",
            TicketPrice, gst, ServiceTax);
            Payment p = new Payment();
            p.pay(TicketPrice);    
}

void FlightFair(int a, int b) {
    System.out.println("For Normal Class Type '1'\t For Business Class '2'");
    int b2 = sc.nextInt();
    if (b2 == 1) {
        float base = (float) (Math.abs(a - b) * 2320.6);
        gst = 18 * base / 100;
        ServiceTax = 23.87 * Math.abs(a - b) * NPT;
        TicketPrice = (float) (base + gst + ServiceTax);
    } else if (b2 == 2) {
        float base = (float) (Math.abs(a - b) * 6510.9);
        gst = 18 * base / 100;
        ServiceTax = 33.97 * Math.abs(a - b) * NPT;
        TicketPrice = base + gst + ServiceTax;
    }
    System.out.printf("Total: %.2f (including GST: %.2f and Service Tax: %.2f)%n",
            TicketPrice, gst, ServiceTax);
            Payment p = new Payment();
            p.pay(TicketPrice);
}

void TrainFair(int a, int b)
{
    System.out.println("For Non-AC Sleeper Class Type '1'\t For AC Sleeper Type '2'");
    int b2 = sc.nextInt();
    if (b2 == 1) 
    {
        float base = (float) (Math.abs(a - b) * 220.6);
        gst = 18 * base / 100;
        ServiceTax = 23.87 * Math.abs(a - b) * NPT;
        TicketPrice = base + gst + ServiceTax;
    }
    else if (b2 == 2) 
    {
        float base = (float) (Math.abs(a - b) * 450.9);
        gst = 18 * base / 100;
        ServiceTax = 33.97 * Math.abs(a - b) * NPT;
        TicketPrice = base + gst + ServiceTax;
    }
    System.out.printf("Total: %.2f (including GST: %.2f and Service Tax: %.2f)%n",
            TicketPrice, gst, ServiceTax);
            Payment p = new Payment();
            p.pay(TicketPrice);
}

    void sendTicketToMobile() 
    {
        StringBuilder ticket = new StringBuilder();
        ticket.append("\n\t\t=== MakeMyTrip Booking Confirmation ===\n");
        ticket.append("\t \t"+String.format("%-15s %-5s %-12s %-8s%n", "Name", "Age", "SeatType", "Gender"));
        ticket.append("\t\t---------------------------------------------------\n");

        for (int i = 0; i < NPT; i++) {
            ticket.append(String.format("\t\t%-15s %-5d %-12s %-8s%n",
                    name[i], age[i], Type[i], Gender[i]));
        }

        ticket.append("\t\t"+"---------------------------------------------------\n");
        ticket.append(String.format("Total Fare: %.2f (GST: %.2f, Service Tax: %.2f)%n",
                TicketPrice, gst, ServiceTax));
        ticket.append("Thank you for booking with MakeMyTrip!\n");

        System.out.println("\nSending ticket to mobile number: " + number);
        System.out.println(ticket);
        
    }
    void DisplayThanksArt() {
        String RESET = "\u001B[0m";
        String YELLOW = "\u001B[33m";
        String GREEN = "\u001B[32m";
        String[] art = {

            YELLOW + "\t\t-------------------------------------------------------------------------------",
            GREEN  + "\t\t\t\t\tThanks For Visiting Us!",
            YELLOW + "\t\t-------------------------------------------------------------------------------" + RESET
        };

        try {
            for (String line : art) {
                System.out.println(line);
                Thread.sleep(360);
            }
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
    void OtherOptions()
    {
        System.out.println("You Are Looking for SomeThing Else");
        System.out.println("Here we are Type 1 for bus book Type 2 for train booking Type 3 Flight booking Type 4 for Exit");
        int option2=sc.nextInt();
        if(option2==1)
        {
            BusFair(a,b);
        }
        else if(option2==2)
        {
            TrainFair(a,b);
        }
        else if(option2==3)
        {
            FlightFair(a,b);
        }
        else
        {
            DisplayThanksArt();
        }
    }
}
//Red bus
abstract class Booking 
{
    Scanner sc = new Scanner(System.in);
    String from, to, date;
    int numPass;
    double baseFare;
    public static final String RESET = "\u001B[0m";
    public static final String RED = "\u001B[31m";
    public static final String GREEN = "\u001B[32m";
    public static final String YELLOW = "\u001B[33m";
    public static final String BLUE = "\u001B[34m";
    public static final String PURPLE = "\u001B[35m";
    public static final String CYAN = "\u001B[36m";
    public static final String WHITE = "\u001B[37m";
    void collectDetails() 
    {
        System.out.print("Enter Source: ");
        from = sc.nextLine();
        System.out.print("Enter Destination: ");
        to = sc.nextLine();
        System.out.print("Enter Travel Date (DD-MM-YYYY): ");
        date = sc.nextLine();
        System.out.print("Enter Number of Passengers: ");
        numPass = sc.nextInt();
        sc.nextLine();
    }

    abstract void bookTicket();
}

class BusBooking extends Booking 
{
    double gstRate = 0.18;
    double serviceCharge = 50;

    void bookTicket() {
        System.out.println(BLUE + "\n   _______");
         System.out.println("                              ");
        System.out.println("                              ");
        System.out.println("                              ");
        System.out.println("                              ");
        System.out.println(" ⢀⡴⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⠶⣦   ");
        System.out.println(" ⢸⡇⢰⣶⣶⣶ ⣶⣶⣶⡆⢰⣶ ⣶⡆⢰⣶⣶⣶ ⢰⣶⣶⡆⢸⡆  ");
        System.out.println(" ⢸⡇⠘⠛⠛⠛ ⠛⠛⠛⠃⢸⣿ ⣿⡇⠘⠛⠛⠛ ⠘⠛⠛⠛ ⢿⡀ ");
        System.out.println(" ⢸⣿⣿⣿⣿⣿⣿⣿⣿⣿⡇⢸⣿ ⣿⡇⢸⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡇ ");
        System.out.println(" ⢸⣿⣿⣿⠟⠛⠛⠻⣿⣿⣇⠘⠛ ⠛⠃⣸⣿⣿⣿⡿⠛⠛⠛⢿⣿⣿⡇ ");
        System.out.println("   ⠈⠁⣴⡟⢻⣦⠈⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⢠⣾⠻⣷⡀⠉⠉⠁ ");
        System.out.println("      ⠙⠿⠿⠃                ⠈⠻⠟   ");
        System.out.println("                              ");
        System.out.println("                              ");
        System.out.println("                              ");
        System.out.println("                              "+RESET);

        System.out.println(PURPLE + "\nAvailable Bus Routes:" + RESET);
        //System.out.println("\nAvailable Bus Routes:");
        System.out.println("1. Hyderabad → Vijayawada   ");
        System.out.println("2. Hyderabad → Bangalore    ");
        System.out.println("3. Hyderabad → Chennai      ");
        System.out.println("4. Vijayawada → Vizag       ");
        System.out.println("5. Bangalore → Mysore       ");
        System.out.println("6. Chennai → Coimbatore     ");
        System.out.println("7. Vizag → Arunachalam      ");
        System.out.println("8. Pune → Mumbai            ");

        collectDetails();

        if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Vijayawada"))
            baseFare = 500;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Bangalore"))
            baseFare = 800;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Chennai"))
            baseFare = 900;
        else if (from.equalsIgnoreCase("Vijayawada") && to.equalsIgnoreCase("Vizag"))
            baseFare = 600;
        else if (from.equalsIgnoreCase("Bangalore") && to.equalsIgnoreCase("Mysore"))
            baseFare = 400;
        else if (from.equalsIgnoreCase("Chennai") && to.equalsIgnoreCase("Coimbatore"))
            baseFare = 700;
        else if (from.equalsIgnoreCase("Vizag") && to.equalsIgnoreCase("Arunachalam"))
            baseFare = 750;
        else if (from.equalsIgnoreCase("Pune") && to.equalsIgnoreCase("Mumbai"))
            baseFare = 550;
        else {
            System.out.println("Invalid route! Please try again.");
            return;
        }

        double totalFare = 0;
        System.out.println("\nBUS BOOKING SUMMARY:");
        System.out.println("From: " + from + " | To: " + to + " | Date: " + date);

        for (int i = 1; i <= numPass; i++) {
            System.out.println("Passenger " + i + ":");
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Age: ");
            int age = sc.nextInt();
            sc.nextLine();
            System.out.print("Seat Preference (Window/Normal): ");
            String seat = sc.nextLine();

            double fare = baseFare;
            if (age > 60) fare *= 0.75; // Senior citizen discount
            double gstAmount = fare * gstRate;
            fare += gstAmount;
            fare += serviceCharge;

            totalFare += fare;

            System.out.println("Name: " + name + "\nAge: " + age + "\nSeat: " + seat);
            System.out.printf("Base Fare: %.2f\nGST: %.2f\nService Charge: %.2f\nFinal Fare: %.2f\n",
                    baseFare, gstAmount, serviceCharge, fare);
        }
        System.out.printf("Total Fare: %.2f\n", totalFare);
        Payment p = new Payment();
        p.pay(totalFare);
    }
}

class TrainBooking extends Booking 
{
    double gstRate = 0.18;
    double serviceCharge = 60;

    boolean IRCTC(String id, String pwd) {
        return id.equals("CV123") && pwd.equals("CV@123");
    }

    void bookTicket() {
        System.out.println(PURPLE + "\n      _____        ");
        System.out.println(BLUE +"      ___      ___      ___\n" +
                                 " __|[]|_  |[]|_  |[]|_\n" +
                                 "|o o o o o||o o o o o||o o o o|\n" +
                                 "'--O-----O''--O-----O''--O-----O'\n"+RESET);
        System.out.print("Enter IRCTC ID: ");
        String id = sc.nextLine();
        System.out.print("Enter IRCTC Password: ");
        String pwd = sc.nextLine();

        if (!IRCTC(id, pwd)) {
            System.out.println("Invalid IRCTC credentials.");
            return;
        }
        
        System.out.println("\nAvailable Train Routes:");
        System.out.println("1. Hyderabad → Vijayawada   ");
        System.out.println("2. Hyderabad → Bangalore    ");
        System.out.println("3. Hyderabad → Chennai      ");
        System.out.println("4. Vijayawada → Vizag       ");
        System.out.println("5. Bangalore → Mysore       ");
        System.out.println("6. Chennai → Coimbatore     ");
        System.out.println("7. Vizag → Arunachalam      ");
        System.out.println("8. Pune → Mumbai            ");

        collectDetails();

        if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Vijayawada"))
            baseFare = 400;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Bangalore"))
            baseFare = 650;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Chennai"))
            baseFare = 700;
        else if (from.equalsIgnoreCase("Vijayawada") && to.equalsIgnoreCase("Vizag"))
            baseFare = 500;
        else if (from.equalsIgnoreCase("Bangalore") && to.equalsIgnoreCase("Mysore"))
            baseFare = 300;
        else if (from.equalsIgnoreCase("Chennai") && to.equalsIgnoreCase("Coimbatore"))
            baseFare = 550;
        else if (from.equalsIgnoreCase("Vizag") && to.equalsIgnoreCase("Arunachalam"))
            baseFare = 600;
        else if (from.equalsIgnoreCase("Pune") && to.equalsIgnoreCase("Mumbai"))
            baseFare = 450;
        else {
            System.out.println("Invalid route! Please try again.");
            return;
        }

        double totalFare = 0;
        System.out.println("\nTRAIN BOOKING SUMMARY:");
        System.out.println("From: " + from + " | To: " + to + " | Date: " + date);

        for (int i = 1; i <= numPass; i++) {
            System.out.println("Passenger " + i + ":");
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Age: ");
            int age = sc.nextInt();
            sc.nextLine();
            System.out.print("Seat Preference (Window/Normal): ");
            String seat = sc.nextLine();

            double fare = baseFare;
            double gstAmount = fare * gstRate;
            fare += gstAmount;
            fare += serviceCharge;

            totalFare += fare;

            System.out.println("Name: " + name + "\nAge: " + age + "\nSeat: " + seat);
            System.out.printf("Base Fare: %.2f\nGST: %.2f\nService Charge: %.2f\nFinal Fare: %.2f\n",
                    baseFare, gstAmount, serviceCharge, fare);
        }
        System.out.printf("Total Fare: %.2f\n", totalFare);
        Payment p = new Payment();
        p.pay(totalFare);
    }
}

class FlightBooking extends Booking 
{
    double gstRate = 0.18;
    double serviceCharge = 100;

    void bookTicket() {
        System.out.println(CYAN + "\n      _|_");
        System.out.println("                      \\ \\\n" +
                           "                       \\ `\\\n" +
                           "    ___                 \\  \\\n" +
                           "   |    \\                \\  `\\\n" +
                           "   |_\\                \\    \\\n" +
                           "   |\\                \\    `\\\n" +
                           "   |       \\                \\     \\\n" +
                           "   |      _\\---------------------------------..\n" +
                           " _|---~o_o_o_o_o_o_o_o_o_o_o_o_o_o_o_o_o_o[][\\\n" +
                           "|___                         /~      )                \\\n" +
                           "    ~~~---.../      ,//\n" +
                           "                           /      /\n" +
                           "                          /     ,/\n" +
                           "                         /     /\n" +
                           "                        /    ,/\n" +
                           "                       /    /\n" +
                           "                      //  ,/\n" +
                           "                     //  /\n" +
                           "                    // ,/\n" +
                           "                   //_/\n" + RESET);

        System.out.println(PURPLE +"\nAvailable Flight Routes:" + RESET);
        System.out.println("\nAvailable Flight Routes:");
        System.out.println("1. Hyderabad → Vijayawada   ");
        System.out.println("2. Hyderabad → Bangalore    ");
        System.out.println("3. Hyderabad → Chennai      ");
        System.out.println("4. Vijayawada → Vizag       ");
        System.out.println("5. Bangalore → Mysore       ");
        System.out.println("6. Chennai → Coimbatore     ");
        System.out.println("7. Vizag → Arunachalam      ");
        System.out.println("8. Pune → Mumbai            ");

        collectDetails();

        if (from.equals("Hyderabad") && to.equalsIgnoreCase("Vijayawada"))
            baseFare = 2500;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Bangalore"))
            baseFare = 3000;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Chennai"))
            baseFare = 3200;
        else if (from.equalsIgnoreCase("Vijayawada") && to.equalsIgnoreCase("Vizag"))
            baseFare = 2800;
        else if (from.equalsIgnoreCase("Bangalore") && to.equalsIgnoreCase("Mysore"))
            baseFare = 2200;
        else if (from.equalsIgnoreCase("Chennai") && to.equalsIgnoreCase("Coimbatore"))
            baseFare = 2600;
        else if (from.equalsIgnoreCase("Vizag") && to.equalsIgnoreCase("Arunachalam"))
            baseFare = 2700;
        else if (from.equalsIgnoreCase("Pune") && to.equalsIgnoreCase("Mumbai"))
            baseFare = 2400;
        else {
            System.out.println("Invalid route! Please try again.");
            return;
        }

        double totalFare = 0;
        System.out.println("\nFLIGHT BOOKING SUMMARY:");
        System.out.println("From: " + from + " | To: " + to + " | Date: " + date);

        for (int i = 1; i <= numPass; i++) {
            System.out.println("Passenger " + i + ":");
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Age: ");
            int age = sc.nextInt();
            sc.nextLine();
            System.out.print("Seat Preference (Window/Normal): ");
            String seat = sc.nextLine();

            double fare = baseFare;
            double gstAmount = fare * gstRate;
            fare += gstAmount+serviceCharge;
            totalFare += fare;

            System.out.println("Name: " + name + "\nAge: " + age + "\nSeat: " + seat);
            System.out.printf("Base Fare: %.2f\nGST: %.2f\nService Charge: %.2f\nFinal Fare: %.2f\n",
                    baseFare, gstAmount, serviceCharge, fare);
        }
        System.out.printf("Total Fare: %.2f\n", totalFare);
        Payment p = new Payment();
        p.pay(totalFare);
    }
}

abstract class PBooking 
{
    Scanner sc = new Scanner(System.in);
    String from, to, date;
    int numPass;
    double baseFare;

    void collectDetails() 
    {
        System.out.print("Enter Source: ");
        from = sc.nextLine();
        System.out.print("Enter Destination: ");
        to = sc.nextLine();
        System.out.print("Enter Travel Date (DD-MM-YYYY): ");
        date = sc.nextLine();
        System.out.print("Enter Number of Passengers: ");
        numPass = sc.nextInt();
        sc.nextLine();
    }

    abstract void PbookTicket();
}

class PBusBooking extends PBooking 
{
    double gstRate = 0.18;
    double serviceCharge = 50;

    void PbookTicket() 
    {
        System.out.println("\nAvailable Bus Routes:");
        System.out.println("1. Hyderabad → Vijayawada   ");
        System.out.println("2. Hyderabad → Bangalore    ");
        System.out.println("3. Hyderabad → Chennai      ");
        System.out.println("4. Vijayawada → Vizag       ");
        System.out.println("5. Bangalore → Mysore       ");
        System.out.println("6. Chennai → Coimbatore     ");
        System.out.println("7. Vizag → Arunachalam      ");
        System.out.println("8. Pune → Mumbai            ");

        collectDetails();

        if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Vijayawada"))
            baseFare = 600;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Bangalore"))
            baseFare = 700;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Chennai"))
            baseFare = 1000;
        else if (from.equalsIgnoreCase("Vijayawada") && to.equalsIgnoreCase("Vizag"))
            baseFare = 650;
        else if (from.equalsIgnoreCase("Bangalore") && to.equalsIgnoreCase("Mysore"))
            baseFare = 300;
        else if (from.equalsIgnoreCase("Chennai") && to.equalsIgnoreCase("Coimbatore"))
            baseFare = 680;
        else if (from.equalsIgnoreCase("Vizag") && to.equalsIgnoreCase("Arunachalam"))
            baseFare = 750;
        else if (from.equalsIgnoreCase("Pune") && to.equalsIgnoreCase("Mumbai"))
            baseFare = 500;
        else 
        {
            System.out.println("Invalid route! Please try again.");
            return;
        }

        double totalFare = 0;
        System.out.println("\n BUS BOOKING SUMMARY:");
        System.out.println("From: " + from + " | To: " + to + " | Date: " + date);

        for (int i = 1; i <= numPass; i++)
        {
            System.out.println("Passenger " + i + ":");
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Age: ");
            int age = sc.nextInt();
            sc.nextLine();
            System.out.print("Seat Preference (Window/Normal): ");
            String seat = sc.nextLine();

            double fare = baseFare;
            if (age > 60) fare *= 0.75; 
            double gstAmount = fare * gstRate;
            fare += gstAmount;
            fare += serviceCharge;

            totalFare += fare;

            System.out.println("Name: " + name + "\n Age: " + age + "\n Seat: " + seat);
            System.out.printf("Base Fare: %.2f\n GST: %.2f\n Service Charge: %.2f\n Final Fare: %.2f\n",
                    baseFare, gstAmount, serviceCharge, fare);
        }
        System.out.printf("Total Fare: %.2f\n", totalFare);
        Payment p = new Payment();
        p.pay(totalFare);
    }
}

class PTrainBooking extends PBooking 
{
    double gstRate = 0.18;
    double serviceCharge = 60;

    boolean IRCTC(String id, String pwd) 
    {
        return id.equals("CV123") && pwd.equals("CV@123");
    }

    void PbookTicket()
    {
        System.out.print("Enter IRCTC ID: ");
        String id = sc.nextLine();
        System.out.print("Enter IRCTC Password: ");
        String pwd = sc.nextLine();

        if (!IRCTC(id, pwd))
        {
            System.out.println("Invalid IRCTC credentials.");
            return;
        }

        System.out.println("\n Available Train Routes:");
        System.out.println("1. Hyderabad → Vijayawada   ");
        System.out.println("2. Hyderabad → Bangalore    ");
        System.out.println("3. Hyderabad → Chennai      ");
        System.out.println("4. Vijayawada → Vizag       ");
        System.out.println("5. Bangalore → Mysore       ");
        System.out.println("6. Chennai → Coimbatore     ");
        System.out.println("7. Vizag → Arunachalam      ");
        System.out.println("8. Pune → Mumbai            ");

        collectDetails();

        if (from.equals("Hyderabad") && to.equalsIgnoreCase("Vijayawada"))
            baseFare = 400;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Bangalore"))
            baseFare = 640;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Chennai"))
            baseFare = 710;
        else if (from.equalsIgnoreCase("Vijayawada") && to.equalsIgnoreCase("Vizag"))
            baseFare = 600;
        else if (from.equalsIgnoreCase("Bangalore") && to.equalsIgnoreCase("Mysore"))
            baseFare = 400;
        else if (from.equalsIgnoreCase("Chennai") && to.equalsIgnoreCase("Coimbatore"))
            baseFare = 560;
        else if (from.equalsIgnoreCase("Vizag") && to.equalsIgnoreCase("Arunachalam"))
            baseFare = 590;
        else if (from.equalsIgnoreCase("Pune") && to.equalsIgnoreCase("Mumbai"))
            baseFare = 450;
        else 
        {
            System.out.println("Invalid route! Please try again.");
            return;
        }
        double totalFare = 0;
        System.out.println("\nTRAIN BOOKING SUMMARY:");
        System.out.println("From: " + from + " | To: " + to + " | Date: " + date);

        for (int i = 1; i <= numPass; i++)
        {
            System.out.println("Passenger " + i + ":");
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Age: ");
            int age = sc.nextInt();
            sc.nextLine();
            System.out.print("Seat Preference (Window/Normal): ");
            String seat = sc.nextLine();

            double fare = baseFare;
            double gstAmount = fare * gstRate;
            fare += gstAmount;
            fare += serviceCharge;

            totalFare += fare;

            System.out.println("Name: " + name + "\nAge: " + age + "\nSeat: " + seat);
            System.out.printf("Base Fare: %.2f\nGST: %.2f\nService Charge: %.2f\nFinal Fare: %.2f\n",
                    baseFare, gstAmount, serviceCharge, fare);
        }
        System.out.printf("Total Fare: %.2f\n", totalFare);
        Payment p = new Payment();
        p.pay(totalFare);
    }
}

class PFlightBooking extends PBooking 
{
    double gstRate = 0.18;
    double serviceCharge = 100;

    void PbookTicket()
    {
        System.out.println("\nAvailable Flight Routes:");
        System.out.println("1. Hyderabad → Vijayawada   ");
        System.out.println("2. Hyderabad → Bangalore    ");
        System.out.println("3. Hyderabad → Chennai      ");
        System.out.println("4. Vijayawada → Vizag       ");
        System.out.println("5. Bangalore → Mysore       ");
        System.out.println("6. Chennai → Coimbatore     ");
        System.out.println("7. Vizag → Arunachalam      ");
        System.out.println("8. Pune → Mumbai            ");

        collectDetails();

        if (from.equals("Hyderabad") && to.equalsIgnoreCase("Vijayawada"))
            baseFare = 2400;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Bangalore"))
            baseFare = 4000;
        else if (from.equalsIgnoreCase("Hyderabad") && to.equalsIgnoreCase("Chennai"))
            baseFare = 3000;
        else if (from.equalsIgnoreCase("Vijayawada") && to.equalsIgnoreCase("Vizag"))
            baseFare = 2800;
        else if (from.equalsIgnoreCase("Bangalore") && to.equalsIgnoreCase("Mysore"))
            baseFare = 2300;
        else if (from.equalsIgnoreCase("Chennai") && to.equalsIgnoreCase("Coimbatore"))
            baseFare = 2500;
        else if (from.equalsIgnoreCase("Vizag") && to.equalsIgnoreCase("Arunachalam"))
            baseFare = 2300;
        else if (from.equalsIgnoreCase("Pune") && to.equalsIgnoreCase("Mumbai"))
            baseFare = 2900;
        else
        {
            System.out.println("Invalid route! Please try again.");
            return;
        }

        double totalFare = 0;
        System.out.println("\nFLIGHT BOOKING SUMMARY:");
        System.out.println("From: " + from + " | To: " + to + " | Date: " + date);

        for (int i = 1; i <= numPass; i++)
        {
            System.out.println("Passenger " + i + ":");
            System.out.print("Name: ");
            String name = sc.nextLine();
            System.out.print("Age: ");
            int age = sc.nextInt();
            sc.nextLine();
            System.out.print("Seat Preference (Window/Normal): ");
            String seat = sc.nextLine();

            double fare = baseFare;
            double gstAmount = fare * gstRate;
            fare += gstAmount+serviceCharge;
            //fare += serviceCharge;

            totalFare += fare;

            System.out.println("Name: " + name + "\nAge: " + age + "\nSeat: " + seat);
            System.out.printf("Base Fare: %.2f\nGST: %.2f\nService Charge: %.2f\nFinal Fare: %.2f\n",
                    baseFare, gstAmount, serviceCharge, fare);
        }
        System.out.printf("Total Fare: %.2f\n", totalFare);
        Payment p = new Payment();
        p.pay(totalFare);
    }
}
class Payment {
    static Scanner sc = new Scanner(System.in);
    int generateOtp() 
    {
        return 1000 + (int)(Math.random() * 8999);
    }
    void pay(double amount)
    {
        System.out.println("=== PAYMENT GATEWAY ===");
        System.out.println("Amount to Pay: " + amount);
        System.out.println("Choose Payment Method: ");
        System.out.println("1. UPI");
        System.out.println("2. Card");
        int choice = sc.nextInt();

        if (choice == 1)
        {
            upiPayment(amount);
        } 
        else if (choice == 2)
        {
            cardPayment(amount);
        } 
        else
        {
            System.out.println("Invalid choice. Payment failed.");
            this.pay(amount);
        }
    }
    void upiPayment(double amount) 
    {
        System.out.print("Enter UPI ID: ");
        String upiId = sc.next();
        int otp = generateOtp();
        System.out.println("Your OTP is: " + otp);
        System.out.print("Enter OTP: ");
        int entered = sc.nextInt();

        if (entered == otp) 
        {
            String BLINK = "\u001B[5m";
            String RESET = "\u001B[0m";
            String GREEN = "\u001B[32m";
            
            System.out.println(GREEN + BLINK + "UPI Payment of " + amount + " successful!" + RESET);

        }
        else
        {
            System.out.println("Incorrect OTP. Payment Failed.");
        }
    }

    void cardPayment(double amount)
    {
        while(true)
        {
        System.out.print("Enter Card Number: ");
        String card = sc.next();
        if(card.length()!=16) 
        {
            System.out.println("Invalid mobile number! Signup failed.");
            continue;
        }
        System.out.print("Enter CVV: ");
        int cvv = sc.nextInt();
        int otp = generateOtp();
        System.out.println("Your OTP is: " + otp);
        System.out.print("Enter OTP: ");
        int entered = sc.nextInt();
        if (entered == otp) 
        {
            System.out.println("Card Payment of " + amount + " successful!");
            break;
        } 
        else
        {
            System.out.println("Incorrect OTP. Payment Failed.");
        }
        }
    }
}
