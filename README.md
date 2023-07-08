# C_Sharp

Design a class named Person with properties for holding a person's name, address, and telephone number.
Next, design a class named Customer, which is derived from the Person class. The Customer class should
have a property for a customer number and a Boolean property indicating whether the customer wishes to
be on a mailing list. A retall store has a preferred customer plan where a customer can ear discounts on all
purchases. The amount of a customer's discount is determined by the amount of the customer's overall
purchases in the store as follows:
•Ihen a preferred customer spends TK. 500, he or she gets I percent discount on future purchases.
• When a preferred customer spends TK. 1000, he or she gets 2 percent discount on future purchases.
•When a preferred customer spends TK. 1500, he or she gets 5 percent discount on future purchases.
•When a preferred customer spends TK. 2000, he or she gets 7 percent discount on future purchases.
Design a class named PreferredCustomer, which is derived from the Customer class. The
PreferredCustomer class should have properties for the customer's overall purchases and customer '§
discount level.
The Main method is atready given for you, iry to write other classes to make ir happen, write approp
fields, methods, properties etc. Use proper access modifiers, lypes etc.



using System;

class Person
{
    public string Name { get; }
    public string Address { get; }
    public string TelephoneNumber { get; }

    public Person(string name, string address, string telephoneNumber)
    {
        Name = name;
        Address = address;
        TelephoneNumber = telephoneNumber;
    }
}

class Customer : Person
{
    public int CustomerNumber { get; }
    public bool OnMailingList { get; }

    public Customer(string name, string address, string telephoneNumber, int customerNumber, bool onMailingList)
        : base(name, address, telephoneNumber)
    {
        CustomerNumber = customerNumber;
        OnMailingList = onMailingList;
    }
}

class PreferredCustomer : Customer
{
    public double OverallPurchases { get; }
    public int DiscountLevel { get; }

    public PreferredCustomer(string name, string address, string telephoneNumber, int customerNumber, bool onMailingList, double overallPurchases)
        : base(name, address, telephoneNumber, customerNumber, onMailingList)
    {
        OverallPurchases = overallPurchases;
        CalculateDiscountLevel();
    }

    private void CalculateDiscountLevel()
    {
        if (OverallPurchases >= 2000)
        {
            DiscountLevel = 7;
        }
        else if (OverallPurchases >= 1500)
        {
            DiscountLevel = 5;
        }
        else if (OverallPurchases >= 1000)
        {
            DiscountLevel = 2;
        }
        else if (OverallPurchases >= 500)
        {
            DiscountLevel = 1;
        }
        else
        {
            DiscountLevel = 0;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        PreferredCustomer customer = new PreferredCustomer("John Doe", "123 Main St", "555-1234", 12345, true, 2500.0);

        Console.WriteLine("Customer Information:");
        Console.WriteLine("Name: " + customer.Name);
        Console.WriteLine("Address: " + customer.Address);
        Console.WriteLine("Telephone Number: " + customer.TelephoneNumber);
        Console.WriteLine("Customer Number: " + customer.CustomerNumber);
        Console.WriteLine("On Mailing List: " + (customer.OnMailingList ? "Yes" : "No"));
        Console.WriteLine("Overall Purchases: TK. " + customer.OverallPurchases);
        Console.WriteLine("Discount Level: " + customer.DiscountLevel + "%");
    }
}
