# lab8

rational number

package assignments;

public class RationalNumber {
    private int numerator;
    private int denominator;

    // Constructor
    public RationalNumber(int numerator, int denominator) {
        if (denominator == 0) {
            throw new IllegalArgumentException("Denominator cannot be zero.");
        }
        this.numerator = numerator;
        this.denominator = denominator;
    }

    // Recursive method to find the GCD using Euclid's algorithm
    public int gcd(int a, int b) {
        if (b == 0) {
            return a;
        }
        return gcd(b, a % b); // Recursive call
    }

    // Method to get the GCD of numerator and denominator
    public int computeGCD() {
        return gcd(numerator, denominator);
    }
}




driver

package assignments;

import java.util.Scanner;

public class driver {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        try {
            // Prompt user for numerator
            System.out.print("Enter positive integer as numerator: ");
            int numerator = scanner.nextInt();

            // Prompt user for denominator
            System.out.print("Enter positive integer as denominator: ");
            int denominator = scanner.nextInt();

            // Ensure both numbers are positive
            if (numerator <= 0 || denominator <= 0) {
                System.out.println("Please enter positive integers only.");
            } else {
                // Create RationalNumber object
                RationalNumber rationalNumber = new RationalNumber(numerator, denominator);

                // Compute GCD
                int gcd = rationalNumber.computeGCD();

                // Print result
                System.out.println("Greatest common denominator of " + numerator + "/" + denominator + " is " + gcd);
            }
        } catch (Exception e) {
            System.out.println("EXCEPTION: Invalid input. Please enter valid positive integers.");
        } finally {
            scanner.close();
        }
    }
}
