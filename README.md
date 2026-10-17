#include <stdio.h>
#include <math.h>

#define PI 3.14159265358979323846

// Function to calculate factorial
unsigned long long factorial(int n) {
    unsigned long long fact = 1;
    for (int i = 1; i <= n; i++) {
        fact *= i;
    }
    return fact;
}

// Function to approximate sin(x) using Taylor series
double sineSeries(double x) {
    double sum = 0.0;
    double term = x;

    for (int i = 1; i <= 15; i++) {
        sum += term;
        term *= -x * x / ((2 * i) * (2 * i + 1));
    }

    return sum;
}

int main() {
    int choice, n;
    double a, b, result;

    do {
        printf("\n===== SCIENTIFIC CALCULATOR =====\n");
        printf("1. Addition (+)\n");
        printf("2. Subtraction (-)\n");
        printf("3. Multiplication (*)\n");
        printf("4. Division (/)\n");
        printf("5. Modulus (%%)\n");
        printf("6. Power (x^y)\n");
        printf("7. Factorial (n!)\n");
        printf("8. Sine sin(x) using series\n");
        printf("9. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter two numbers: ");
                scanf("%lf %lf", &a, &b);
                printf("Result = %.6f\n", a + b);
                break;

            case 2:
                printf("Enter two numbers: ");
                scanf("%lf %lf", &a, &b);
                printf("Result = %.6f\n", a - b);
                break;

            case 3:
                printf("Enter two numbers: ");
                scanf("%lf %lf", &a, &b);
                printf("Result = %.6f\n", a * b);
                break;

            case 4:
                printf("Enter two numbers: ");
                scanf("%lf %lf", &a, &b);
                if (b != 0)
                    printf("Result = %.6f\n", a / b);
                else
                    printf("Error: Division by zero!\n");
                break;

            case 5:
                printf("Enter two numbers: ");
                scanf("%lf %lf", &a, &b);
                if (b != 0)
                    printf("Result = %.6f\n", fmod(a, b));
                else
                    printf("Error: Modulus by zero!\n");
                break;

            case 6:
                printf("Enter base and exponent: ");
                scanf("%lf %lf", &a, &b);
                result = pow(a, b);
                printf("Result = %.6f\n", result);
                break;

            case 7:
                printf("Enter a non-negative integer (0-20): ");
                scanf("%d", &n);
                if (n >= 0 && n <= 20)
                    printf("Factorial = %llu\n", factorial(n));
                else
                    printf("Error: Enter an integer from 0 to 20.\n");
                break;

            case 8:
                printf("Enter angle in radians: ");
                scanf("%lf", &a);
                printf("sin(%.6f) = %.10f\n",
                       a, sineSeries(a));
                break;

            case 9:
                printf("Exiting calculator. Goodbye!\n");
                break;

            default:
                printf("Invalid choice! Try again.\n");
        }

    } while (choice != 9);

    return 0;
}