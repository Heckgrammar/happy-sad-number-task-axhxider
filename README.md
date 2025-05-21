using System;
using System.Collections.Generic;

class Program
{
    // calculates the sum of the squares of the digits of a number
    static int SumOfSquares(int number)
    {
        int sum = 0;
        while (number > 0)
        {
            int digit = number % 10;      // Get the last digit
            sum += digit * digit;         // Square it and add to sum
            number = number / 10;         // Remove the last digit
        }
        return sum;
    }

    //  determines whether a number is happy or sad
    static bool IsHappyNumber(int number)
    {
        HashSet<int> seenNumbers = new HashSet<int>(); // Stores numbers we've already seen to detect loops

        while (number != 1 && !seenNumbers.Contains(number))
        {
            seenNumbers.Add(number);         // Remember the number we've seen
            number = SumOfSquares(number);   // Replace number with the sum of the squares of its digits
        }

        return number == 1;
    }

    static void Main(string[] args)
    {
        // Test with 19 and 20
        int[] testNumbers = { 19, 20 };

        foreach (int num in testNumbers)
        {
            if (IsHappyNumber(num))
            {
                Console.WriteLine(num + " is a Happy number!");
            }
            else
            {
                Console.WriteLine(num + " is a Sad number.");
            }
        }

        // Optionally, allow user to input their own number
        Console.WriteLine("Enter a number to check if it's Happy or Sad:");
        int userNumber = Convert.ToInt32(Console.ReadLine());

        if (IsHappyNumber(userNumber))
        {
            Console.WriteLine(userNumber + " is a Happy number!");
        }
        else
        {
            Console.WriteLine(userNumber + " is a Sad number.");
        }
    }
}
