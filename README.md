using System;
using System.Collections.Generic;
using System.Linq;

namespace search_task
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // ==========================================
            // Task 1: Read numbers & throw exception on duplicates
            // ==========================================
            Console.WriteLine("=== Task 1: Check Duplicate Numbers ===");
            try
            {
                Console.Write("Enter integers separated by spaces: ");
                string input = Console.ReadLine();

                if (!string.IsNullOrWhiteSpace(input))
                {
                    List<int> numbers = input.Split(' ', StringSplitOptions.RemoveEmptyEntries)
                                             .Select(int.Parse)
                                             .ToList();

                    CheckDuplicates(numbers);
                    Console.WriteLine("Success: No duplicate numbers found!");
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error: {ex.Message}");
            }

            Console.WriteLine("\n-----------------------------------\n");

            // ==========================================
            // Task 2: Check string for vowels
            // ==========================================
            Console.WriteLine("=== Task 2: Check Vowels in String ===");
            try
            {
                Console.Write("Enter a string: ");
                string text = Console.ReadLine();

                CheckVowels(text);
                Console.WriteLine("Success: The string contains vowels!");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error: {ex.Message}");
            }

            Console.ReadLine();
        }

        // Method for Task 1
        public static void CheckDuplicates(List<int> numbers)
        {
            HashSet<int> seenNumbers = new HashSet<int>();

            foreach (int number in numbers)
            {
                if (!seenNumbers.Add(number))
                {
                    throw new Exception($"Duplicate number found: {number}");
                }
            }
        }

        // Method for Task 2
        public static void CheckVowels(string str)
        {
            string vowels = "aeiouAEIOU";

            if (string.IsNullOrEmpty(str) || !str.Any(c => vowels.Contains(c)))
            {
                throw new Exception("The string does not contain any vowels!");
            }
        }
    }
}
