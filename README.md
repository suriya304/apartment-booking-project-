import java.util.Scanner;

public class Houserent {
    public static void main(String[] args) {
        Scanner get =new Scanner(System.in);
        Register register = new Register();
        System.out.println(" -------------Exclusive features--------------    ");
        System.out.println("");
        System.out.println(" | Swimming | " + " | GYM |" + " | Shopping  |" + " |  Play  |");
        System.out.println(" |   Pool   | " + " |     |" + " |  Complex  |" + " | School |");
        System.out.println("");
        System.out.println("-------------------------------------------");
        System.out.println("          Login/Register    ");
        String l=logi();
        if (l.equalsIgnoreCase("Login")) {
            Login login = new Login();
            login.log(register);
        } else if (l.equalsIgnoreCase("Register")) {
            register.reg();
        } else {
            System.err.println("Invalid input.");
            logi();
        }

    }
    public static  String logi(){
        Scanner get=new Scanner(System.in);
        String log = get.nextLine();
        return log;

    }

}

class Login extends Register {
    public void log(Register register) {
        Scanner get = new Scanner(System.in);
        System.out.print("Enter Username : ");
        String username = get.nextLine();
        System.out.println("");
        System.out.print("Enter Password : ");
        String password = get.nextLine();
        if (register.isValidLogin(username, password)) {
            System.out.println("Login successful!");
            Choice c = new Choice();
            c.choose();
        } else {
            System.err.println("Invalid username or password.");
            System.out.println();
            System.out.println("Create an account / Try Again");
            System.out.println();
            String loginChoice = get.nextLine();
            if (loginChoice.equalsIgnoreCase("create an account")) {
                register.reg();
            } else {
                Login login = new Login();
                login.log(this);
            }
        }
    }
}

    class Register {
        private String Username[] = new String[10];
        private String Password[] = new String[10];
        int i = 0;

        public void reg() {
            Scanner get = new Scanner(System.in);
            System.out.print("Create Usrename : ");
            String username = get.nextLine().trim();
            Username[i] = username;
            System.out.println();
            System.out.print("Enter Name : ");
            String name = get.nextLine();
            System.out.println();
            System.out.print("Enter mobile number : ");
            String mobileNo = get.nextLine();
            if (mobileNo.length() != 10) {
                System.err.println("Invalid!!");
            }
            System.out.println();
            System.out.print("Enter Email Id : ");
            String email = get.nextLine();
            System.out.println();
            System.out.print("Create a Password : ");
            String password = get.nextLine().trim();
            Password[i] = password;
            String PassWord = confirm();
            if (PassWord.equals(Password[i]) && !(PassWord.isEmpty())) {
                System.out.println("Successfully registered");
                System.out.println();
                System.out.println("Login to continue");
                Login login = new Login();
                login.log(this);
                i = i + 1;
            } else {

                System.err.println("Password mismatched");
                System.out.println("");
                System.out.println("Try Again");
                System.out.println();
                confirm();
                
            }
        }


        public String confirm( ) {
            Scanner get = new Scanner(System.in);
            System.out.print("Confirm Password : ");
            String password1 = get.nextLine();
            return password1;
        }

        public boolean isValidLogin(String username, String password) {
            for (int j = 0; j <= i; j++) {
                if (Username[j] != null && Username[j].equals(username)) {
                    return Password[j] != null && Password[j].equals(password);
                }
            }
            return false;
        }
    }


    class Choice {
        void choose() {
            Scanner get = new Scanner(System.in);
            System.out.println();
            System.out.println("-----------------------------------------");
            System.out.println("GET STARTED WITH EXPLORING RENTAL OPTIONS  ");
            System.out.println("-----------------------------------------");
            System.out.println("");
            System.out.println("  Buying a  " + "  Renting a  ");
            System.out.println("   Flat     " + "    Flat     ");
            System.out.println("  Press(1)  " + "  Press(2)   ");
            System.out.println("");
            System.out.println("-------------------------------");
            System.out.println("");
            int flat = get.nextInt();
            if (flat == 1) {
                Location location = new Location();
                location.loc();
            }
            if (flat == 2) {
                Flat flt = new Flat();
                flt.rent();
            }
        }
    }

    class Location {
        void loc() {
            Scanner get = new Scanner(System.in);
            System.out.println();
            System.out.println("Choose your location");
            System.out.println("---------------------");
            System.out.println(" 1)   Chennai");
            System.out.println(" 2)  Bangalore");
            System.out.println(" 3)  Hyderabad");
            System.out.println(" 4) Coimbatore");
            System.out.println(" 5)    Delhi");
            int ch1 = get.nextInt();
            if (ch1 == 1) {
                Loc c = new Loc();
                c.chennai();
            } else if (ch1 == 2) {
                Loc c = new Loc();
                c.banglore();

            } else if (ch1 == 3) {
                Loc c = new Loc();
                c.Hyderabad();

            } else if (ch1 == 4) {
                Loc c = new Loc();
                c.coimbatore();

            } else if (ch1 == 5) {
                Loc c = new Loc();
                c.delhi();

            }
        }
    }

    class Loc {
        void chennai() {
            Detail d = new Detail();
            d.detail();
        }

        void banglore() {
            Detail d = new Detail();
            d.detail();
        }

        void Hyderabad() {
            Detail d = new Detail();
            d.detail();
        }

        void coimbatore() {
            Detail d = new Detail();
            d.detail();
        }

        void delhi() {
            Detail d = new Detail();
            d.detail();
        }
    }

    class Detail {
        void detail() {
            Scanner scan = new Scanner(System.in);
            Amount house = new Amount();
            house.list();
            int choice = scan.nextInt();
            if (choice == 1)
                house._2bhk();
            else if (choice == 2)
                house._3bhk();
            else if (choice == 3)
                house._4bhk();
            else if (choice == 4)
                house._5bhk();
            house.Interiordesign();
            house.design();
            house.MembershipDetails();
            int membership = scan.nextInt();
            if (membership == 1)
                house.Platinum();
            else if (membership == 2)
                house.Gold();
            else if (membership == 3)
                house.None();
            house.amt();
            Booking bookpage = new Booking();
            bookpage.book();
        }
    }

    class Bhk_Details extends Interior {
        void list() {
            System.out.println("       BHK Details");
            System.out.println(" 1) 2BHK-1154-1239 Sq Ft");
            System.out.println(" 2) 3BHK-1294-1325 Sq Ft");
            System.out.println(" 3) 4BHK-1421-1569 Sq Ft");
            System.out.println(" 4) 5BHK-1647-1892 Sq Ft");
        }

        void _2bhk() {
            System.err.println("Amount of 2BHk - ₹89,00,000");
            System.err.println("₹Eighty Nine Lakhs Only");
            Amount += 8900000;
        }

        void _3bhk() {
            System.err.println("Amount of 3BHk - ₹125,00,000");
            System.err.println("₹ One Crore Twenty Five Lakh Only");
            Amount += 12500000;
        }

        void _4bhk() {
            System.err.println("Amount of 4BHk - ₹164,90,000");
            System.err.println("₹ One Crore Sixty Four Lakh Ninety Thousand Only");
            Amount += 16490000;
        }

        void _5bhk() {
            System.err.println("Amount of 5BHk - ₹285,00,000");
            System.err.println("₹ Two Crore Eighty Five Lakhs Only");
            Amount += 28500000;
        }
    }

    class Interior extends Membership {
        void Interiordesign() {
            System.out.println();
            System.out.println("         Interior");
            System.out.println("----------------------------");
            System.out.println(" 1]   Modular kitchen");
            System.out.println(" 2]  Bedroom furniture");
            System.out.println(" 3] Living room furniture");
            System.out.println(" 4]   Extra Accessories");
        }

        void design() {
            Scanner sc = new Scanner(System.in);
            String b = sc.nextLine();
            char a[] = b.toCharArray();
            int n = a.length;
            for (int i = 0; i < n; i++) {
                if (a[i] == '1') {
                    System.out.println("Modular kitchen");
                    System.out.println("");
                    Amount = Amount + 350000;
                }
                if (a[i] == '2') {
                    System.out.println("Furnished Bedroom ");
                    System.out.println("");
                    Amount = Amount + 175250;
                }
                if (a[i] == '3') {
                    System.out.println("Furnished Livingroom ");
                    System.out.println("");
                    Amount = Amount + 257000;
                }
                if (a[i] == '4') {
                    System.out.println("Extra accessories");
                    System.out.println("");
                    Amount = Amount + 612000;
                }
            }
        }
    }

    class Membership {
        int Amount = 0;

        void MembershipDetails() {
            System.out.println("***Membership Details***");
            System.out.println("");
            System.out.println(" 1)Platinum");
            System.out.println();
            System.out.println("*** Features ***");
            System.out.println();
            System.out.println("   Car Parking ");
            System.out.println("       Gym     ");
            System.out.println("   Swimming pool");
            System.out.println("   Daily Service");
            System.out.println("  Unlimited Wifi");
            System.out.println(" 100% back up power");
            System.out.println();
            System.out.println(" Yearly cost: ₹45999");
            System.out.println();
            System.out.println(" 2)Gold");
            System.out.println();
            System.out.println("*** Features ***");
            System.out.println("");
            System.out.println("   Car Parking");
            System.out.println("      Gym");
            System.out.println("  Swimming pool");
            System.out.println();
            System.out.println("Yearly cost: ₹25499");
            System.out.println();
            System.out.println(" 3)None");
            System.out.println();
            System.out.println("*** Features ***");
            System.out.println("");
            System.out.println("  Car Parking");
            System.out.println(" Security(cctv)");
            System.out.print("Enter your choice:");
        }

        void None() {
            Amount += 0;
        }

        void Gold() {
            Amount += 25499;
        }

        void Platinum() {
            Amount += 45999;
        }
    }

    class Amount extends Bhk_Details {
        void amt() {
            System.out.println(" ");
            System.out.println("Total Amount: ₹" + Amount);
            System.out.println();
        }
    }

    class Booking {
        void book() {
            System.err.println("   CONFIRM  " + " CANCEL");
            System.err.println("   BOOKING  ");
            System.out.println("   Press(1)  " + "Press(2)");
            Scanner b = new Scanner(System.in);
            int bok = b.nextInt();
            if (bok == 1) {
                System.out.println("   Successfully Booked  ");
                System.out.println("   Thanks for booking   ");
                System.out.println();
                Choice choice = new Choice();
                choice.choose();
            } else {
                System.out.println(" Going to booking page ");
                Choice choice = new Choice();
                choice.choose();
            }
        }
    }

    class Flat {
        void rent() {

            Scanner in = new Scanner(System.in);
            System.out.print("Enter your prefered budget: ");
            int budget = in.nextInt();
            in.nextLine();
            int avail;
            if (budget <= 10000) {
                avail = 25;
                System.out.println("There are " + avail + " villas available!");


            }
            else if (budget > 10000 && budget <= 20000) {
                avail = 20;
                System.out.println("There are " + avail + " villas available!");

            } 
            else if (budget > 20000 && budget <= 30000) {
                avail = 30;
                System.out.println("There are " + avail + " villas available!");


            } 
            else if (budget > 30000 && budget <= 40000) {
                avail = 22;
                System.out.println("There are " + avail + " villas available!");

            } 
            else {
                avail = 20;
                System.out.println("There are " + avail + " villas available!");

            }
            System.out.println("Are booking the villa for rent");
            String ch = in.nextLine();
            if (ch.equals("yes")) {
                System.out.print("Enter your full name: ");
                String fullName = in.nextLine();
                System.out.print("Enter your contact number: ");
                String contactNumber = in.nextLine();
                System.out.print("Enter your employment status: ");
                String employmentStatus = in.nextLine();
                System.out.print("Enter your monthly income: ");
                double monthlyIncome = in.nextDouble();
                System.out.print("Enter your previous rental address: ");
                String previousAddress = in.nextLine();
                System.out.println("\nThank you for providing the following details:");
                System.out.println();
                System.out.println("Your Deatils");
                System.out.println("Full Name: " + fullName);
                System.out.println("Contact Number: " + contactNumber);
                System.out.println("Employment Status: " + employmentStatus);
                System.out.println("Monthly Income: " + monthlyIncome);
                System.out.println("Previous Rental Address: " + previousAddress);
                System.out.println("");
                Booking bk = new Booking();
                bk.book();
                System.out.println("Thanks for booking a Flat for rent in our website!");
                System.out.println();
                Choice choice = new Choice();
                choice.choose();
            } else {
                System.out.println("Tune in after sometime to get best offers and deals");
                System.out.println();
                Choice choice = new Choice();
                choice.choose();
            }


        }
    }

