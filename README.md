# HelloWorldRepo
class MainClass
{
    public static List<string> nomi = new List<string>();
    public static List<string> password = new List<string> ();
    public static bool startup = true;
    public static bool logged = false;



    public static void Main (string[] args)
    {

        Start ();

    }


    //Starting loop
    public static void Start()
    {
        string choice;

        while (startup == true) 
        {

            Console.WriteLine ("Do you want to login or register?");

            choice = Console.ReadLine ();

            switch (choice) 
            {
            case "register":
                Register ();
                break;
            case "login":
                Login (ref logged, out startup);
                break;
            default:
                Console.WriteLine ("Error, please repeat.");
                Console.WriteLine ();
                break;
            }   

        } 

    }

    //Logged in loop
    public static void Run()
    {

        string app;

        while (logged == true) 
        {
            Console.WriteLine ("Choose an app: Calculator, Logout, Exit.");
            app = Console.ReadLine ();

            if (app == "calculator") {
                Calc ();
            } else if (app == "check") {
                Check();
            }else if (app == "exit") {
                Console.WriteLine ("Goodbye.");
                logged = false;
            } else if (app == "logout") {
                logged = false;
                startup = true;
                Console.WriteLine ();
                Start ();
            } else {
                Console.WriteLine ("Invalid app");
                Console.WriteLine ();
            }

        }

    }


    //Registration and login methods
    public static void Register()
    {
        Console.WriteLine ("Choose a Name: ");
        nomi.Add (Console.ReadLine ());
        Console.WriteLine ("Choose a password: ");
        password.Add (Console.ReadLine ());
        Console.WriteLine ();

    }


    public static bool Login(ref bool logged, out bool startup)
    {
        string name;
        string pwd;


        Console.WriteLine ("Write your username");
        name = Console.ReadLine ();

        foreach (string nome in nomi) {                                 

            if (nome == name) {
                Console.WriteLine ("Write your Password");
                pwd = Console.ReadLine ();

                foreach (string pword in password) {
                    if (pword == pwd) {
                        Console.WriteLine ("You are logged in");
                        Console.WriteLine ();
                        logged = true;
                        startup = false;
                        Run ();
                        return logged;
                    }

                }
                Console.WriteLine ("Incorrect Password");
                Console.WriteLine ();
                startup = true;
                return logged;
            } 
        }       

        Console.WriteLine ("Invalid username");
        Console.WriteLine ();
        startup = true;
        return logged;


    }

    //APPS

    public static void Calc()
    {
        float num1;
        float num2;
        string oper;


        Console.WriteLine ("Write the first number: ");
        num1 = float.Parse (Console.ReadLine ());
        Console.WriteLine ("Write the second number:");
        num2 = float.Parse (Console.ReadLine ());
        Console.WriteLine ("Select the operator: +, -, *, /");
        oper = Console.ReadLine ();
        switch (oper)
        {
        case "+":
            Console.WriteLine ("The result is: " + num1 + num2);
            Console.WriteLine ();
            break;
        case "-":
            Console.WriteLine ("The result is: " + (num1 - num2));
            Console.WriteLine ();
            break;
        case "*":
            Console.WriteLine ("The result is: " + num1 * num2);
            Console.WriteLine ();
            break;
        case "/":
            Console.WriteLine ("The result is: " + num1 / num2);
            Console.WriteLine ();
            break;
        default:
            Console.WriteLine ("Invalid Operator");
            Console.WriteLine ();
            break;
        }
    }


    public static void Check()
    {
        Console.WriteLine ("Names:");
        foreach (string name in nomi)
            Console.WriteLine (name);
        Console.WriteLine ("Passwords:");
        foreach (string pwd in password)
            Console.WriteLine (pwd);


    }


}
