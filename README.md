'''csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Welcome to the Basic Console Calculator!");
        bool continueCalculating = true;

        do
        {
            double num1 = GetNumber("Enter the first number: ");
            double num2 = GetNumber("Enter the second number: ");
            Console.Write("Enter an operator (+, -, *, /): ");
            string op = Console.ReadLine();

            double? result = PerformCalculation(num1, num2, op);

            if (result.HasValue)
            {
                Console.WriteLine($"Result: {num1} {op} {num2} = {result.Value}");
            }
            else
            {
                Console.WriteLine("Invalid operation or division by zero. Please try again.");
            }

            Console.Write("Do you want to perform another calculation? (yes/no): ");
            string choice = Console.ReadLine().ToLower();
            if (choice != "yes" && choice != "y")
            {
                continueCalculating = false;
            }

        } while (continueCalculating);

        Console.WriteLine("Thank you for using the calculator. Goodbye!");
    }

    static double GetNumber(string message)
    {
        double number;
        while (true)
        {
            Console.Write(message);
            if (double.TryParse(Console.ReadLine(), out number))
            {
                return number;
            }
            else
            {
                Console.WriteLine("Invalid input. Please enter a valid number.");
            }
        }
    }

    static double? PerformCalculation(double num1, double num2, string op)
    {
        if (op == "+")
        {
            return num1 + num2;
        }
        else if (op == "-")
        {
            return num1 - num2;
        }
        else if (op == "*")
        {
            return num1 * num2;
        }
        else if (op == "/")
        {
            if (num2 != 0)
            {
                return num1 / num2;
            }
            else
            {
                return null;
            }
        }
        else
        {
            return null;
        }
    }
}
