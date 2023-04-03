# Strong-number-or-not-using-Java

Strong number or not using Java
Check Whether or Not the Number is a Strong Number in Java
Given an integer  input the objective is to check whether or not the number is a strong number. Therefore we’ll write a code to Check whether or Not the Number is a Strong Number in Java Language.

Example
Input : 145
Output : Yes, it's a strong number
java program to check strong number or not
Check Whether or Not the Given Number is a Strong Number in Java Language
Given an integer input as the number, the objective is to Check Whether or Not the Given Number is a Strong Number in Java Language.

To do so we’ll check if the sum of the factorial of each individual digit of the number is equal to the number itself or not.

For a number to be a Strong Number, the sum of Factorial of each digit of the number must be equal to the number itself. Here are a few method to Check Whether or Not the Given Number is a Strong Number or Not in Java Language,

Method 1: Using Simple Iteration
Method 2: Using Recursive Function
We’ll discuss the above mentioned methods in detail in the upcoming sections. Do check out the blue box given below for better understanding of the problem.

Strong Number in Java
Strong Number
A Number that can be represented as the sum of the factorial of it's individual digits is known as a Strong Number.
Let's try and understand the concept better using an example

Example
Input : 145
Output : Yes, it's a strong number
Explanation : Number = 145
145 = 1! + 4! + 5!
145 = 1 + 24 + 120
output number  = 145.
As the number could be represented as the sum of the factorials of it's digits, it's a Strong Number.
Method 1: Using Simple Iteration
In this method we’ll sue the concept of loops and iteration to check whether the number is a strong number or not. To do so we’ll declare a function that takes the number and returns the factorial value. We split the number into individual digits using modulo and divide operators. We then find their factorial using the user defined function. We sum all the factorial values and check if it matches the original number.

Java Code
Run
public class Main
 {
   public static void main (String[]args)
   {

     int num = 145;

     if (detectStrong (num))
         System.out.println (num + " is Strong Number");
     else
         System.out.println (num + " is not a Strong Number");
   }

   // function to calculate factorial
   static int facto (int n)
   {
     int fact = 1;

     for (int i = 1; i <= n; i++)
       fact = fact * i;

     return fact;
   }

   static boolean detectStrong (int num)
   {

     int digit, sum = 0;
     int temp = num;
     boolean flag = false;

     // calculate 1! + 4! + 5!
     while (temp != 0)
       {
     	digit = temp % 10;

     	sum = sum + facto (digit);
 	    temp /= 10;
       }

     // returns 1 if both equal else 0
     if (sum == num)
       flag = true;
     else
       flag = false;

     return flag;


   }
 }
Output
145 is a Strong Number
Related Pages
Factor of a number

Finding Prime Factors of a number

Strong number

Perfect number

Perfect Square

Automorphic number

Method 2: Using Recursive Function
In this method we’ll use the concept of recursion to check whether the number is a strong number or not. To do so we’ll first declare a recursive function that takes the number as an argument and returns it’s factorial value. Then we break down the number using the modulo and the divide operator for extracting the digits and shortening the number respectively. We then call the factorial function that we declared before for each number. In the end we sum up all the factorial values and check whether they match the original number.

Java Code
Run
public class Main
{
  public static void main (String[]args)
  {

    int num = 145;

    if (detectStrong (num))
        System.out.println (num + " is Strong Number");
    else
        System.out.println (num + " is not a Strong Number");
  }

  // function to calculate factorial
  static int facto (int num)
  {
     if(num == 0)
        return 1;
        
    return num * facto(num-1);
  }

  static boolean detectStrong (int num)
  {

     int digit, sum = 0;
    int temp = num;
    
    // calculate 1! + 4! + 5!
    while(temp!=0){
        digit = temp % 10;
        
        sum = sum + facto(digit);
        temp /= 10;
    }
    
    // returns 1 if both equal else 0
    return sum == num;

  }
}
Output
145 is a Strong Number
Method 3: Smart Dynamic Programming Approach
This method kind of uses dynamic programming to pre-compute factorial values. This helps us as we may not need to re-calculate factorial again and again for new digits

Run
class Main
{
    static int f[] = new int[10];
    // Finding factorial for number 0 to 9
    // to precompute factorials without needing them to be calculated again and again
    // you can change this 0 to 15 or 0 to 20 for larger values
    // in this case change to long
    static void preComputer()
    {
        f[0] = f[1] = 1;
        for (int i = 2; i<10; ++i)
            f[i] = f[i-1] * i;
    }

    static boolean checkStrong(int num)
    {
        int sum = 0;

        // traverse individual digits of num
        int temp = num;

        while (temp > 0)
        {
            sum += f[temp % 10];
            temp = temp / 10;
        }
        return (sum == num);
    }

    public static void main (String[] args)
    {
        // calling preCompute
        // this way we do not need to calculate factorial again and again
        // we can directly use saved up values like dynamic programming
        preComputer();
        int val = 145;

        if(checkStrong(val))
            System.out.println("Its a strong number");
        else
            System.out.println("Its not a strong number");
    }
Output
Its a strong number
