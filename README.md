# OOPS
1.	. Write a program to perform arithmetic operations of two complex numbers.(Addition & subtraction)
2.	Write a program to perform arithmetic operations of two complex numbers.(Multiplication and Division)

import java.util.*;

class Complex_Op {
    float real, imag;

    Complex_Op() // Default Constructor
    {
        real = 0;
        imag = 0;
    }

    Complex_Op(float Comp1, float Comp2) // Parameterized Constructor
    {
        real = Comp1;
        imag = Comp2;
    }

    void AddNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag;
        real = (C1.real + C2.real);
        imag = (C1.imag + C2.imag);
        System.out.println("Addition:=" + real + "+" + imag + "i");
    }

    void SubtractNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag;
        real = (C1.real - C2.real);
        imag = (C1.imag - C2.imag);
        System.out.println("Subtraction:=" + real + "+" + imag + "i");
    }

    void MultiplyNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag;
        real = (C1.real * C2.real - C1.imag * C2.imag);
        imag = (C1.real * C2.imag + C2.real * C1.imag);
        System.out.println("Multiplication:=" + real + "+" + imag + "i");
    }

    void DivideNumbers(Complex_Op C1, Complex_Op C2) {
        float real, imag, deno;
        deno = (C2.real * C2.real + C2.imag * C2.imag);
        real = (C1.real * C2.real + C1.imag * C2.imag) / deno;
        imag = (C2.real * C1.imag - C1.real * C2.imag) / deno;
        System.out.println("Division:=" + real + "+" + imag + "i");
    }
}

public class Complex {
    public static void main(String args[]) {
        int num1, num2, answer;
        Complex_Op cal = new Complex_Op();
        Scanner input = new Scanner(System.in);
        System.out.println("Enter first number");
        num1 = input.nextInt(); // Real part
        num2 = input.nextInt(); // Imaginary Part
        Complex_Op Object1 = new Complex_Op(num1, num2);
        System.out.println("Enter the Second Number");
        num1 = input.nextInt(); // Real Part
        num2 = input.nextInt(); // Imaginary Part
        Complex_Op Object2 = new Complex_Op(num1, num2);
        cal.AddNumbers(Object1, Object2);
        cal.SubtractNumbers(Object1, Object2);
        cal.MultiplyNumbers(Object1, Object2);
        cal.DivideNumbers(Object1, Object2);
    }
}
Output: 













----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2. Write a program to find how many copies of the given books are ordered and display total sale of publication.

(Polymorphism- Title, Price, Copies are common instance variables and saleCopy is common method. The differences are, Bookclass has author and order Copies(). Magazine Class has methods orderQty, Currentissue, receiveissue().)

import java.util.Scanner;

abstract class Publication {
    String title;
    float price;
    int copies;

    abstract void setprice();

    abstract void salecopy();
}

class Book extends Publication {
    String author;

    void ordercopies() {
    }

    public void salecopy() {
        System.out.println("name of book:" + title);
        System.out.println("name of author:" + author);
        System.out.println("price of book:" + price);
        System.out.println("number of copies:" + copies);
        System.out.println("total sale=" + copies * price);
    }

    public void setprice() {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter the name of book ");
        title = sc.next();
        System.out.println("enter the name of author ");
        author = sc.next();
        System.out.println("enter price ");
        price = sc.nextInt();
        System.out.println("enter copies ");
        copies = sc.nextInt();
    }
}

class Magzine extends Publication {
    int quantity;
    String currentIssue;

    public void salecopy() {
        System.out.println("name of magzine " + title);
        System.out.println("Price of magzine " + price);
    }

    public void setprice() {
        Scanner sc = new Scanner(System.in);
        System.out.println("enter name of magzine ");
        title = sc.next();
        System.out.println("order quantity");
        quantity = sc.nextInt();
        System.out.println("price of magzine  ");
        price = sc.nextInt();
        System.out.println("enter number of copies  ");
        copies = sc.nextInt();
    }

    public void receiveIssue() {
        System.out.println(" enter currentIssue ");
        Scanner sc = new Scanner(System.in);
        currentIssue = sc.next();
        System.out.println("you will receive" + currentIssue + "soon");
    }
}

class Polymorphism {
    public static void main(String args[]) {
        Book b = new Book();
        b.setprice();
        b.salecopy();
        Magzine m = new Magzine();
        m.setprice();
        m.salecopy();
        m.receiveIssue();
    }
}
Output:












------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
3. Inheritance
   Employee class has Emp_name, Emp_id, Address, Mail_id, and Mobile_no as members. Inherit the classes: Programmer, Team Lead, Assistant Project Manager and Project Manager from employee class. Add Basic Pay (BP) as the member of all the inherited classes with 97% of BP as DA, 10 % of BP as HRA, 12% of BP as PF, 0.1% of BP for staff club fund. Generate pay slips for the employees with their gross
and net salary.


import java.util.Scanner;

class Empolyee {
    String emp_name, emp_id, address, mail_id, mob;

    void get_data() {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter Name of employee :");
        emp_name = sc.nextLine();

        System.out.print("Enter ID of employee :");
        emp_id = sc.next();

        System.out.print("Enter Address of employee :");
        address = sc.next();

        System.out.print("Enter Mail_ID of employee :");
        mail_id = sc.next();

        System.out.print("Enter mobile number of employee :");
        mob = sc.next();

    }

    void display() {
        System.out.println("-------------------------------------------------------------");
        System.out.println("EMP NAME\tID\tADDRESS\t\tMOBILE\t\tEmail_id");
        System.out.println(emp_name + "\t" + emp_id + "\t" + address + "\t" + mob + "\t" + mail_id);
        System.out.println("-------------------------------------------------------------");
    }
}

class Programmer extends Empolyee {
    double BP, DA, HRA, PF, club_f, Gross_sal, Net_sal;;

    void get_sal() {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter Basic salary : ");
        BP = sc.nextDouble();
    }

    void cal_sal() {
        DA = BP * 0.97;
        HRA = BP * 0.1;
        PF = BP * 0.12;
        club_f = BP * 0.001;
        Gross_sal = BP + HRA;
        Net_sal = Gross_sal - PF - club_f;
    }

    void display1() {
        System.out.println("\t\tPayslip of programmer :");
        display();

        System.out.println("\t\tBasic pay      : " + BP);
        System.out.println("\t\tDA             : " + DA);
        System.out.println("\t\tHRA            : " + HRA);
        System.out.println("\t\tPF             : " + PF);
        System.out.println("\t\tClub fund      : " + club_f);
        System.out.println("\t\tGross salary   : " + Gross_sal);
        System.out.println("\t\tNet salary     : " + Net_sal);
    }
}

class teamlead extends Empolyee {
    double BP, DA, HRA, PF, club_f, Gross_sal, Net_sal;;

    void get_sal() {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter Basic salary : ");
        BP = sc.nextDouble();
    }

    void cal_sal() {
        DA = BP * 0.97;
        HRA = BP * 0.1;
        PF = BP * 0.12;
        club_f = BP * 0.001;
        Gross_sal = BP + HRA;
        Net_sal = Gross_sal - PF - club_f;
    }

    void display1() {
        System.out.println("\t\tPayslip of Teamlead :");
        display();

        System.out.println("\t\tBasic pay      : " + BP);
        System.out.println("\t\tDA             : " + DA);
        System.out.println("\t\tHRA            : " + HRA);
        System.out.println("\t\tPF             : " + PF);
        System.out.println("\t\tClub fund      : " + club_f);
        System.out.println("\t\tGross salary   : " + Gross_sal);
        System.out.println("\t\tNet salary     : " + Net_sal);
    }
}

class ass_pro_manager extends Empolyee {
    double BP, DA, HRA, PF, club_f, Gross_sal, Net_sal;;

    void get_sal() {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter Basic salary : ");
        BP = sc.nextDouble();
    }

    void cal_sal() {
        DA = BP * 0.97;
        HRA = BP * 0.1;
        PF = BP * 0.12;
        club_f = BP * 0.001;
        Gross_sal = BP + HRA;
        Net_sal = Gross_sal - PF - club_f;
    }

    void display1() {
        System.out.println("\t\tPayslip of ass_pro_manager :");
        display();

        System.out.println("\t\tBasic pay      : " + BP);
        System.out.println("\t\tDA             : " + DA);
        System.out.println("\t\tHRA            : " + HRA);
        System.out.println("\t\tPF             : " + PF);
        System.out.println("\t\tClub fund      : " + club_f);
        System.out.println("\t\tGross salary   : " + Gross_sal);
        System.out.println("\t\tNet salary     : " + Net_sal);
    }
}

class pro_manager extends Empolyee {
    double BP, DA, HRA, PF, club_f, Gross_sal, Net_sal;;

    void get_sal() {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter Basic salary : ");
        BP = sc.nextDouble();
    }

    void cal_sal() {
        DA = BP * 0.97;
        HRA = BP * 0.1;
        PF = BP * 0.12;
        club_f = BP * 0.001;
        Gross_sal = BP + HRA;
        Net_sal = Gross_sal - PF - club_f;
    }

    void display1() {
        System.out.println("\t\tPayslip of pro_manager :");
        display();

        System.out.println("\t\tBasic pay      : " + BP);
        System.out.println("\t\tDA             : " + DA);
        System.out.println("\t\tHRA            : " + HRA);
        System.out.println("\t\tPF             : " + PF);
        System.out.println("\t\tClub fund      : " + club_f);
        System.out.println("\t\tGross salary   : " + Gross_sal);
        System.out.println("\t\tNet salary     : " + Net_sal);
    }
}

class Inherit {
    public static void main(String args[]) {
        int c;
        Scanner sc = new Scanner(System.in);
        do {
            System.out.println("\nEnter following choice for Salary slip...");
            System.out.println("1.Programmer");
            System.out.println("2.Teamleader");
            System.out.println("3.Assistant Project manager");
            System.out.println("4.Project manager");
            System.out.println("5.Exit");
            System.out.print("Enter choice :");
            c = sc.nextInt();

            switch (c) {
                case 1:
                    Programmer p = new Programmer();
                    p.get_data();
                    p.get_sal();
                    p.cal_sal();

                    System.out.println("-------------------------------------------------------------");
                    p.display1();
                    System.out.println("-------------------------------------------------------------");
                    break;

                case 2:
                    teamlead t = new teamlead();
                    t.get_data();
                    t.get_sal();
                    t.cal_sal();
                    System.out.println("------------------------------------------------------------");
                    t.display1();
                    System.out.println("---------------------------------------------------");
                    break;

                case 3:
                    ass_pro_manager a = new ass_pro_manager();
                    a.get_data();
                    a.get_sal();
                    a.cal_sal();
                    System.out.println("-------------------------------------------------------------");
                    a.display1();
                    System.out.println("-------------------------------------------------------------");
                    break;

                case 4:
                    pro_manager m = new pro_manager();
                    m.get_data();
                    m.get_sal();
                    m.cal_sal();
                    System.out.println("-------------------------------------------------------------");
                    m.display1();
                    System.out.println("-------------------------------------------------------------");
                    break;

                case 5:
                    System.out.println("\n---------- THANK YOU ----------\n");
                    break;
            }

        } while (c < 5);

    }
    }
    Output:








    ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    4.	 . Write a program that accepts dimensions of triangle/rectangle and display calculated area. Implement dynamic binding for given case study.

(Design a base class shape with two double type values and member functions to input the data and compute_area() for calculating area of shape. Derive two classes: triangle and rectangle. Make compute_area() as abstract function and redefine this function in the derived class to suit their requirement)
import java.util.Scanner;

abstract class Shape {
    double l, h;

    abstract void get_data();
    abstract void compute_area();
}

class Triangle extends Shape {
    void get_data() {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the base of the triangle: ");
        l = sc.nextDouble();

        System.out.print("Enter the height of the triangle: ");
        h = sc.nextDouble();
    }

    void compute_area() {
        double area = (l * h) / 2;
        System.out.println("Area of the triangle is: " + area);
    }
}

class Rectangle extends Shape {
    void get_data() {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter the length of the rectangle: ");
        l = sc.nextDouble();

        System.out.print("Enter the height of the rectangle: ");
        h = sc.nextDouble();
    }

    void compute_area() {
        double area = l * h;
        System.out.println("Area of the rectangle is: " + area);
    }
}

public class Main {
    public static void main(String[] args) {
        Shape shape;

        shape = new Triangle();
        shape.get_data();
        shape.compute_area();

        shape = new Rectangle();
        shape.get_data();
        shape.compute_area();
    }
}
Output:









---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
5.	 Interface
Design and develop a context for given case study and implement an interface for Vehicles Consider the example of vehicles like bicycle, car and bike. All Vehicles have common functionalities such as Gear Change, Speed up and apply breaks. Make an interface and put all these common functionalities. Bicycle, Bike, Car classes should be implemented for all these functionalities in their own class in their own way.


import java.util.Scanner;

interface vehicle {
  public void gear_change();

  public void speed_up();

  public void apply_break();
}

class bicycle implements vehicle {
  bicycle() {
    System.out.println("------------------------------------");
    System.out.println("\tBicycle Start : ");
    System.out.println("------------------------------------");
  }

  public void gear_change() {
    System.out.println("\n\tGear Change - Bicycle");
  }

  public void speed_up() {
    System.out.println("\tSpeed Up - Bicycle");
  }

  public void apply_break() {
    System.out.println("\tApply Break - Bicycle\n");
  }

}

class car implements vehicle {
  car() {
    System.out.println("------------------------------------");
    System.out.println("\tCar Start : ");
    System.out.println("------------------------------------");
  }

  public void gear_change() {
    System.out.println("\n\tGear Change - car");
  }

  public void speed_up() {
    System.out.println("\tSpeed Up - car");
  }

  public void apply_break() {
    System.out.println("\tApply Break - car\n");
  }

}

class bike implements vehicle {
  bike() {
    System.out.println("------------------------------------");
    System.out.println("\tBike Start : ");
    System.out.println("------------------------------------");
  }

  public void gear_change() {
    System.out.println("\n\tGear Change - bike");
  }

  public void speed_up() {
    System.out.println("\tSpeed Up - bike");
  }

  public void apply_break() {
    System.out.println("\tApply Break - bike\n");
  }

}

class interfaces {
  public static void main(String args[]) {
    int c;
    do {
      System.out.println("Enter option for vehicle : ");
      System.out.println("\t1.Bicycle");
      System.out.println("\t2.Car");
      System.out.println("\t3.Bike");
      System.out.println("\tExit");
      Scanner sc = new Scanner(System.in);
      System.out.print("Enter choice : ");
      c = sc.nextInt();

      switch (c) {
        case 1:
          bicycle b = new bicycle();
          b.gear_change();
          b.speed_up();
          b.apply_break();
          System.out.println("------------------------------------");
          break;

        case 2:
          car c1 = new car();
          c1.gear_change();
          c1.speed_up();
          c1.apply_break();
          System.out.println("------------------------------------");
          break;

        case 3:
          bike b1 = new bike();
          b1.gear_change();
          b1.speed_up();
          b1.apply_break();
          System.out.println("------------------------------------");
          break;

        case 4:
          break;
      }
    } while (c < 4);
  }
}
Output:








-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
6.  Exception handling
Implement a program to handle Arithmetic exception, Array Index Out of Bounds. The user enters two numbers Num1 and Num2. The division of Num1 and Num2 is displayed. If Num1 and Num2 are not integers, the program would throw a Number Format Exception. If Num2 were zero, the program would throw an Arithmetic Exception. Display the exception.


import java.util.Scanner;

class Exception_Handling {
  public static void main(String args[]) {
    int c;
    Scanner sc = new Scanner(System.in);
    do {
      System.out.println("\nEnter following choice for exception");
      System.out.println("\t1.Arithmatic Exception");
      System.out.println("\t2.Array Index out of bouds Exception");
      System.out.println("\t3.Number format Exception");
      System.out.println("\t4.Exit");
      System.out.print("Enter your choice : ");
      c = sc.nextInt();

      switch (c) {
        case 1:
          try {
            int num1, num2, num3;
            System.out.print("Enter First number : ");
            num1 = sc.nextInt();

            System.out.print("Enter Second number : ");
            num2 = sc.nextInt();

            num3 = num1 / num2;
            System.out.print("Division = " + num3);
          }

          catch (Exception e) {
            System.out.println("\n------------------------------------------\n");
            System.out.println("Divide by Zero \n" + e);
            System.out.println("\n------------------------------------------\n");
          }
          break;

        case 2:
          try {
            int a[] = new int[8];
            a[4] = 10;
            System.out.println("value at index 4 : " + a[4]);
            a[9] = 20;
            System.out.println("value at index 9 : " + a[9]);
          }

          catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("\n------------------------------------------\n");
            System.out.println("Array Index Out Of Bounds \n" + e);
            System.out.println("\n------------------------------------------\n");
          }
          break;

        case 3:
          try {
            int a;
            a = Integer.parseInt("XYZ");
            System.out.println("a = " + a);
          }

          catch (Exception e) {
            System.out.println("\n------------------------------------------\n");
            System.out.println("Number Format Exception \n" + e);
            System.out.println("\n------------------------------------------\n");
          }
          break;

        case 4:
          break;
      }
    } while (c < 4);
  }
}
Output:








--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
7.	  Template
Implement a generic program using any collection class to count the number of elements in a collection that have a specific property such as even numbers, odd number, prime number and palindromes.

public class Generics {

  static boolean isPrime(int num) {
    int flag = 0;
    for (int i = 2; i < num; i++)
      if (num % i == 0) {
        flag = 1;
        break;
      }
    if (flag == 0)
      return true;
    return false;

  }

  static <T> void count(String type, T[] element) {
    int even = 0, odd = 0, prime = 0, palin = 0;
    if (type.equals("even")) {
      for (T value : element)
        if (Integer.parseInt(value.toString()) % 2 == 0)
          even++;
      System.out.println("Total Even: " + even);
    }
    if (type.equals("odd")) {
      for (T value : element)
        if (Integer.parseInt(value.toString()) % 2 != 0)
          odd++;
      System.out.println("Total Odd: " + odd);

    }
    if (type.equals("prime")) {
      for (T value : element)
        if (isPrime(Integer.parseInt(value.toString())))
          prime++;
      System.out.println("Total Prime: " + prime);

    }
    if (type.equals("palindrome")) {
      for (T value : element) {
        StringBuffer rev = new StringBuffer(value.toString());
        if (value.toString().equals(new String(rev.reverse())))
          palin++;

      }
      System.out.println("Total Palindrome: " + palin);
    }
  }

  public static void main(String[] args) {

    Integer iarray[] = { 45, 7, 12, 84, 38, 115, 29, 30, 19 };
    count("even", iarray);

    Byte barray[] = { 45, 7, 12, 84, 38, 115, 29, 30, 19 };
    count("even", barray);

    Short sarray[] = { 45, 73, 12, 84, 38, 151, 29, 30, 19 };

    Long larray[] = { 45L, 73L, 12L, 84L, 38L, 151L, 29L, 30L, 19L };
    count("even", larray);

    count("odd", sarray);

    count("prime", larray);

    count("palindrome", sarray);

  }

}
Output:











----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
8.	File Handling
Implement a program for maintaining a database of student records using Files.
Student has Student_id,name,Roll_no, Class, marks and address. Display the data for few students.(min 3 records)
i) Create Database ii)Display Database
iii)	Delete Records
iv)Search Record

import java.io.*;

class StudentRecords1 {
  static BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

  public void addRecords() throws IOException {
    // Create or modify a file for Database
    PrintWriter pw = new PrintWriter(new BufferedWriter(new FileWriter("SRecords.txt", true)));
    String name, studentClass, address, StudID;
    int RollNo, marks;
    long telephoneNo;
    String s;
    boolean addMore;

    // Read Data
    do {
      System.out.print("\nEnter Student ID: ");
      StudID = br.readLine();

      System.out.print("Enter Name of Student: ");
      name = br.readLine();

      System.out.print("Roll No: ");
      RollNo = Integer.parseInt(br.readLine());

      System.out.print("Class: ");
      studentClass = br.readLine();

      System.out.print("Marks: ");
      marks = Integer.parseInt(br.readLine());

      System.out.print("Address: ");
      address = br.readLine();

      System.out.print("Telephone No.: ");
      telephoneNo = Long.parseLong(br.readLine());

      // Print to File
      pw.println(StudID);
      pw.println(name);
      pw.println(RollNo);
      pw.println(studentClass);
      pw.println(marks);
      pw.println(address);
      pw.println(telephoneNo);

      System.out.print("\nRecords added successfully!\n\nDo you want to add more records? (y/n): ");
      s = br.readLine();
      addMore = s.equalsIgnoreCase("y");
      System.out.println();
    } while (addMore);
    
    pw.close();
    showMenu();
  }

  public void readRecords() throws IOException {
    try {
      // Open the file
      BufferedReader file = new BufferedReader(new FileReader("SRecords.txt"));
      String name;
      int i = 1;

      // Read records from the file
      while ((name = file.readLine()) != null) {
        System.out.println("S.No.: " + (i++));
        System.out.println("-------------");
        System.out.println("Student ID: " + name);
        System.out.println("Name: " + file.readLine());
        System.out.println("Roll No: " + file.readLine());
        System.out.println("Class: " + file.readLine());
        System.out.println("Marks: " + file.readLine());
        System.out.println("Address: " + file.readLine());
        System.out.println("Tel. No.: " + Long.parseLong(file.readLine()));
        System.out.println();
      }
      
      file.close();
      showMenu();
      
    } catch (FileNotFoundException e) {
      System.out.println("\nERROR: File not found!");
    }
  }

  public void clear() throws IOException {
    // Create a blank file
    PrintWriter pw = new PrintWriter(new BufferedWriter(new FileWriter("SRecords.txt")));
    pw.close();
    System.out.println("\nAll records cleared successfully!");
    Thread.sleep(1000);  // Short delay
    showMenu();
  }

  public void showMenu() throws IOException {
    System.out.print("1: Add Records\n2: Display Records\n3: Clear All Records\n4: Exit\n\nEnter Your Choice: ");
    int choice = Integer.parseInt(br.readLine());

    switch (choice) {
      case 1:
        addRecords();
        break;
      case 2:
        readRecords();
        break;
      case 3:
        clear();
        break;
      case 4:
        System.exit(0);
        break;
      default:
        System.out.println("\nInvalid Choice!");
        showMenu();
        break;
    }
  }

  public static void main(String args[]) throws IOException {
    StudentRecords1 call = new StudentRecords1();
    call.showMenu();
  }
}
Output:








---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
    9.Case Study:
Using concepts of Object Oriented programming develop solution for any one application
1) Banking system having following operations :
1. Create an account 2. Deposit money 3. Withdraw money 4. Honor daily withdrawal limit 5. Check the balance 6. Display Account information.


import java.util.Scanner;

class Customer {
  private String customerName;
  private int customerAge;

  public void setCustomerName(String customerName) {
    this.customerName = customerName;
  }

  public String getCustomerName() {
    return customerName;
  }

  public void setCustomerAge(int customerAge) {
    this.customerAge = customerAge;
  }

  public int getCustomerAge() {
    return customerAge;
  }
}

abstract class Account {
  protected double balance;
  protected int accountId;
  protected String accountType;
  protected Customer custobj;

  void setBalance(double balance) {
    this.balance = balance;
  }

  double getBalance() {
    return balance;
  }

  void setAccountId(int accountId) {
    this.accountId = accountId;
  }

  int getAccountId() {
    return accountId;
  }

  void setAccountType(String accountType) {
    this.accountType = accountType;
  }

  String getAccountType() {
    return accountType;
  }

  void setCustomerObject(Customer custobj) {
    this.custobj = custobj;
  }

  Customer getCustomerObject() {
    return custobj;
  }

  public abstract boolean withdraw(double amount);
}

class SavingsAccount extends Account {
  private double minimumBalance;

  public void setMinimumBalance(double minimumBalance) {
    this.minimumBalance = minimumBalance;
  }

  public double getMinimumBalance() {
    return minimumBalance;
  }

  public boolean withdraw(double amount) {
    if ((balance - amount) > minimumBalance) {
      balance -= amount;
      return true;
    } else
      return false;
  }
}

class Bank {
  public static Scanner sc = new Scanner(System.in);
  public SavingsAccount a = new SavingsAccount();
  public Customer c = new Customer();

  public SavingsAccount createAccount() {
    sc.nextLine();
    System.out.print("Enter your name: ");
    String customername = sc.nextLine();
    c.setCustomerName(customername);

    System.out.print("Enter your age: ");
    int customerage = sc.nextInt();
    while (customerage < 18) {
      System.out.print("Minimum age should be 18 to create an account.\nPlease enter valid age: ");
      customerage = sc.nextInt();
    }
    c.setCustomerAge(customerage);

    a.setCustomerObject(c);

    System.out.print("Enter your account ID: ");
    int accountid = sc.nextInt();
    a.setAccountId(accountid);

    System.out.print("Enter your account type: ");
    String accounttype = sc.next();
    a.setAccountType(accounttype);

    System.out.print("Enter balance: ");
    double balance = sc.nextDouble();
    a.setBalance(balance);

    System.out.print("Enter minimum balance: ");
    double minbalance = sc.nextDouble();
    a.setMinimumBalance(minbalance);

    return a;
  }

  void getWithdrawAmount() {
    System.out.print("Enter the amount you want to withdraw: ");
    double amount = sc.nextDouble();
    if (amount > 20000) {
      System.out.println("Withdrawal failed. Maximum limit of withdrawal in one transaction is Rs.20000.");
    } else {
      if (a.withdraw(amount)) {
        System.out.println("Withdrawal successful. Balance is: " + a.getBalance());
      } else {
        System.out.println("Sorry!!! Not enough balance");
      }
    }
  }

  public void depositAmount(double amount) {
    double bal = a.getBalance() + amount;
    a.setBalance(bal);
    System.out.println("Amount deposited successfully. Balance is: " + a.getBalance());
  }

  public void checkBalance() {
    System.out.println("Balance is: " + a.getBalance());
  }

  public void displayAccountInformation() {
    System.out.println("Welcome " + c.getCustomerName() + "! Following are your account details:");
    System.out.println("Age: " + c.getCustomerAge());
    System.out.println("Account ID: " + a.getAccountId());
    System.out.println("Account Type: " + a.getAccountType());
    System.out.println("Balance: " + a.getBalance());
    System.out.println("Minimum balance: " + a.getMinimumBalance());
  }
}

public class Banking {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    Bank bm = new Bank();

    while (true) {
      System.out.println("\n\t1. Create Account\n\t2. Display Account\n\t3. Check Balance"
          + "\n\t4. Deposit Amount\n\t5. Withdraw Amount\n\t6. Exit");
      System.out.print("Enter your choice: ");
      int choice = sc.nextInt();
      System.out.println("");

      switch (choice) {
        case 1:
          bm.createAccount();
          System.out.println("=================================================");
          break;
        case 2:
          bm.displayAccountInformation();
          System.out.println("=================================================");
          break;
        case 3:
          bm.checkBalance();
          System.out.println("=================================================");
          break;
        case 4:
          System.out.print("Enter the amount you want to deposit: ");
          double amount = sc.nextDouble();
          bm.depositAmount(amount);
          System.out.println("=================================================");
          break;
        case 5:
          bm.getWithdrawAmount();
          System.out.println("=================================================");
          break;
        case 6:
          System.out.println("Exiting the program. Thank you!");
          sc.close();
          return;
        default:
          System.out.println("INVALID INPUT !!");
          System.out.println("=================================================");
          break;
      }
    }
  }
}
Output:









---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
10.	Factory Design Pattern
Implement Factory design pattern for the given context. Consider Car building process,which requires many steps from allocating accessories to final makeup. These steps should be written as methods and should be called while creating an instance of a specific car type.
  Hatchback, Sedan, SUV could be the subclasses of Car class. Car class and its subclasses
import java.util.Scanner;

abstract class CarFactory {

  String company, carName;
  double budget;

  abstract void getPrice(double price);

  abstract void detail(String companyName, String carName);

  abstract void accessories();

  void input() {
    try (Scanner scan = new Scanner(System.in)) {
      System.out.print("Company: ");
      company = scan.next();
      System.out.print("Car: ");
      carName = scan.next();
      System.out.print("Rough Budget (in Lakhs): ");
      budget = scan.nextDouble();
    }
  }

  void display() {
    getPrice(budget);
    System.out.println("\n-----------------------------------");
    detail(company, carName);
    System.out.println("\n-----------------------------------");
    accessories();
    System.out.println("\n-----------------------------------");
  }

}

class SmallCar extends CarFactory {
  private String hasFeature;

  private static final double MIN_PRICE = 2;
  private static final double MAX_PRICE = 5;

  public void getPrice(double price) {
    hasFeature = (price >= MIN_PRICE && price <= MAX_PRICE) ? "Yes" : "No";
  }

  public void detail(String companyName, String carName) {
    System.out.println("Company: " + companyName);
    System.out.println("Name of Car: " + carName);
    System.out.println("Color: Black/White/Orange/Red");
    System.out.println("Fuel: Petrol");
    System.out.println("Gears: Manual");
  }

  public void accessories() {
    System.out.println("Types of Tyres: Alloy Wheels");
    System.out.println("Airbags: " + hasFeature);
    System.out.println("Back Wiper: " + hasFeature);
    System.out.println("Side Mirror: Two");
    System.out.println("Touch Screen Music Player: " + hasFeature);
  }
}

class Sedan extends CarFactory {
  private String hasFeature;

  private static final double MIN_PRICE = 6;
  private static final double MAX_PRICE = 10;

  public void getPrice(double price) {
    hasFeature = (price >= MIN_PRICE && price <= MAX_PRICE) ? "Yes" : "No";
  }

  public void detail(String companyName, String carName) {
    System.out.println("Company: " + companyName);
    System.out.println("Name of Car: " + carName);
    System.out.println("Color: Black/White/Orange/Red");
    System.out.println("Fuel: Petrol/Diesel");
    System.out.println("Gears: Auto/Manual");
  }

  public void accessories() {
    System.out.println("Types of Tyres: Alloy Wheels");
    System.out.println("Airbags: Yes");
    System.out.println("Back Wiper: Yes");
    System.out.println("Side Mirror: Two");
    System.out.println("Touch Screen Music Player: Yes");
    System.out.println("Roof Window: " + hasFeature);
  }
}

class Luxury extends CarFactory {
  private String hasFeature;

  private static final double MIN_PRICE = 10;
  private static final double MAX_PRICE = 14;

  public void getPrice(double price) {
    hasFeature = (price >= MIN_PRICE && price <= MAX_PRICE) ? "Yes" : "No";
  }

  public void detail(String companyName, String carName) {
    System.out.println("Company: " + companyName);
    System.out.println("Name of Car: " + carName);
    System.out.println("Color: Black/White/Orange/Red");
    System.out.println("Fuel: Diesel");
    System.out.println("Gears: Auto");
  }

  public void accessories() {
    System.out.println("Types of Tyres: Alloy Wheels");
    System.out.println("Airbags: Yes");
    System.out.println("Back Wiper: Yes");
    System.out.println("Side Mirror: Two");
    System.out.println("Touch Screen Music Player: Yes");
    System.out.println("Roof Window: Yes");
    System.out.println("Automotive Garbage Cans: " + hasFeature);
    System.out.println("Automotive Air Freshener: " + hasFeature);
    System.out.println("Button Start: " + hasFeature);
  }
}

public class Main10 {
  public static void main(String[] args) {
    Scanner scan = new Scanner(System.in);
    CarFactory car;

    while (true) {
      System.out.println("Which Car do you want to see?");
      System.out.println("\n\t1. Small Car\n\t2. Sedan Car\n\t3. Luxury Car\n\t4. Exit");
      System.out.print("Enter your choice: ");
      int choice = scan.nextInt();
      System.out.println();

      switch (choice) {
        case 1:
          car = new SmallCar();
          car.input();
          car.display();
          break;

        case 2:
          car = new Sedan();
          car.input();
          car.display();
          break;

        case 3:
          car = new Luxury();
          car.input();
          car.display();
          break;

        case 4:
          System.out.println("Exiting... Thank you!");
          scan.close();
          return;

        default:
          System.out.println("INVALID CHOICE !!");
          System.out.println("\n-----------------------------------");
          break;
      }
    }
  }
}
Output:













----------------------------------------------------------------------------------------------------------------------------------------------------------------
11.	  Strategy Design Pattern
Implement and apply Strategy Design pattern for simple Shopping Cart where three payment strategies are used such as Credit Card, PayPal, BitCoin. Create an interface for strategy pattern and give concrete implementation for payment.


import java.util.Scanner;

interface PaymentProcessor {
  void pay(int amount);
}

class CreditCard implements PaymentProcessor {
  Scanner sc = new Scanner(System.in);
  String name, ExpDate;
  double CardNo;

  CreditCard() {
    super();
    System.out.println("--------------------------------------------------");
    System.out.print("\tCard holder Name :: ");
    this.name = sc.next();
    System.out.print("\tCard Number :: ");
    this.CardNo = sc.nextDouble();
    System.out.print("\tCard Expire Date :: ");
    this.ExpDate = sc.next();
    System.out.println("--------------------------------------------------");
  }

  @Override
  public void pay(int amount) {
    System.out.println("---------------------------------------------------");
    System.out.println("Paying through CreditCard payment: Charging $" + amount);
    System.out.println("----------------------------------------------------");
  }
}

class PayPal implements PaymentProcessor {
  PayPal() {
    super();
    System.out.println("\nChecking Internet Connection........");
  }

  @Override
  public void pay(int amount) {
    System.out.println("----------------------------------------------");
    System.out.println("Paying through PayPal payment: Charging Rs." + amount);
    System.out.println("----------------------------------------------");
  }
}

class BitCoin implements PaymentProcessor {
  Scanner sc = new Scanner(System.in);
  String add;

  BitCoin() {
    super();
    System.out.print("\nEnter Transaction 'Input Address' :: ");
    add = sc.next();
  }

  @Override
  public void pay(int amount) {
    System.out.println("---------------------------------------------------");
    System.out.println("Paying through BitCoin payment: Charging Rs." + amount);
    System.out.println("----------------------------------------------------");
  }
}

class Order {
  private final PaymentProcessor paymentProcessor;
  private final int amount;

  public Order(int amount, PaymentProcessor paymentProcessor) {
    this.amount = amount;
    this.paymentProcessor = paymentProcessor;
  }

  public void process() {
    paymentProcessor.pay(amount);
  }

}

public class Main_11 {
  public static void main(String[] args) {
    int c, amt = 0;
    Order order;
    Scanner sc = new Scanner(System.in);
    while (true) {
      System.out.println();
      System.out.println("**** SHOPING CART ****");
      System.out.print("1.Credit Card \n2.PayPal \n3.BitCoin \n4.Exit");
      System.out.print("\n\nEnter the Choice ::");
      c = sc.nextInt();
      System.out.println("------------------------------------------------------");
      if (c == 1 || c == 2 || c == 3) {
        System.out.print("\nEnter amount tobe Tranfer :: ");
        amt = sc.nextInt();
        System.out.println("-----------------------------------------------------");
      }

      switch (c) {
        case 1:
          order = new Order(amt, new CreditCard());
          order.process();
          break;

        case 2:
          order = new Order(amt, new PayPal());
          order.process();

        case 3:
          order = new Order(amt, new BitCoin());
          order.process();
          break;

        case 4:
          System.out.println("\nThank you For Shopping !!!! ");
          System.out.println("----------------------------------------------------");
          return;

        default:
          System.out.println("Invalid Payment Mode !!!");
          System.out.println("-----------------------------------------------------");

      }
    }
  }
}
Output:











----------------------------------------------------------------------------------------------------------------------------------------------------------------

