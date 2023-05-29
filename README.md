Source code: 

using System;
using System.Collections.Generic;

namespace RecipeApp
{
    class Program
    {
        static Recipe recipe;

        static void Main(string[] args)
        {
            bool runProgram = true;

            while (runProgram)
            {
                Console.WriteLine("Please select an option:");
                Console.WriteLine("1. Enter a new recipe");
                Console.WriteLine("2. Display recipe");
                Console.WriteLine("3. Scale recipe quantities");
                Console.WriteLine("4. Reset recipe quantities");
                Console.WriteLine("5. Clear recipe");
                Console.WriteLine("6. Exit program");

                string input = Console.ReadLine();
                switch (input)
                {
                    case "1":
                        EnterRecipe();
                        break;
                    case "2":
                        DisplayRecipe();
                        break;
                    case "3":
                        ScaleRecipe();
                        break;
                    case "4":
                        ResetRecipe();
                        break;
                    case "5":
                        ClearRecipe();
                        break;
                    case "6":
                        runProgram = false;
                        break;
                }
            }
        }

        static void EnterRecipe()
        {
            recipe = new Recipe();

            Console.WriteLine("Please enter the number of ingredients: ");
            int ingredientCount = int.Parse(Console.ReadLine());
            for (int i = 0; i < ingredientCount; i++)
            {
                Console.WriteLine($"Ingredient {i + 1}:");
                Console.Write("Name: ");
                string name = Console.ReadLine();
                Console.Write("Quantity: ");
                double quantity = double.Parse(Console.ReadLine());
                Console.Write("Unit of measurement: ");
                string unit = Console.ReadLine();
                recipe.AddIngredient(new Ingredient(name, quantity, unit));
            }

            Console.WriteLine("Please enter the number of steps: ");
            int stepCount = int.Parse(Console.ReadLine());
            for (int i = 0; i < stepCount; i++)
            {
                Console.WriteLine($"Step {i + 1}:");
                Console.Write("Description: ");
                string description = Console.ReadLine();
                recipe.AddStep(new Step(description));
            }
        }
    }
}
