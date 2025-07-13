# Advance calculator This is my first C project — an Advanced Calculator that performs mathematical operations like basic arithmetic to include matrix operations, digit-based calculations, and more
#include <stdio.h>
#include <stdlib.h>


void addition();
void subtraction();
void multiplication();
void division();
void modulus();
void matrixAddition();
void matrixMultiplication();
void sumOfDigits();
void productOfDigits();
void percentageCalculator();
void displayMenu();

int main() {
    printf("welcome boss! i am your calculator,ready to solve your problems");
    int choice;
    
    while (1) {
        displayMenu();
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1: addition(); break;
            case 2: subtraction(); break;
            case 3: multiplication(); break;
            case 4: division(); break;
            case 5: modulus(); break;
            case 6: matrixAddition(); break;
            case 7: matrixMultiplication(); break;
            case 8: sumOfDigits(); break;
            case 9: productOfDigits(); break;
            case 10: percentageCalculator(); break;
            case 0: 
                printf("Exiting program...\n");
                exit(0);
            default: 
                printf("Invalid choice! Please try again.\n");
        }
        
        printf("\nPress any key to return to menu...\n");
        getchar();
        getchar();
    }
    
    return 0;
}

// Function to display menu
void displayMenu() {
    printf("\n----> ADVANCED CALCULATOR <----\n");
    printf("1. Addition\n");
    printf("2. Subtraction\n");
    printf("3. Multiplication\n");
    printf("4. Division\n");
    printf("5. Modulus\n");
    printf("6. Matrix Addition\n");
    printf("7. Matrix Multiplication\n");
    printf("8. Sum of Digits\n");
    printf("9. Product of Digits\n");
    printf("10. Percentage Calculator\n");
    printf("0. Exit\n");
}
void addition() {
    double a, b;
    printf("Enter two numbers: ");
    scanf("%lf %lf", &a, &b);
    printf("Result: %.2lf\n", a + b);
}
void subtraction() {
    double a, b;
    printf("Enter two numbers: ");
    scanf("%lf %lf", &a, &b);
    printf("Result: %.2lf\n", a - b);
}
void multiplication() {
    double a, b;
    printf("Enter two numbers: ");
    scanf("%lf %lf", &a, &b);
    printf("Result: %.2lf\n", a * b);
}
void division() {
    double a, b;
    printf("Enter two numbers: ");
    scanf("%lf %lf", &a, &b);
    if (b == 0)
        printf("Error! Division by zero is not allowed.\n");
    else
        printf("Result: %.2lf\n", a / b);
}
void modulus() {
    int a, b;
    printf("Enter two integers: ");
    scanf("%d %d", &a, &b);
    if (b == 0)
        printf("Error! Modulus by zero is not allowed.\n");
    else
        printf("Result: %d\n", a % b);
}

void matrixAddition() {
    int r, c, i, j;
    printf("Enter number of rows and columns: ");
    scanf("%d %d", &r, &c);
    int A[r][c], B[r][c], sum[r][c];

    printf("Enter elements of first matrix:\n");
    for (i = 0; i < r; i++)
        for (j = 0; j < c; j++)
            scanf("%d", &A[i][j]);

    printf("Enter elements of second matrix:\n");
    for (i = 0; i < r; i++)
        for (j = 0; j < c; j++)
            scanf("%d", &B[i][j]);

    printf("Resultant Matrix:\n");
    for (i = 0; i < r; i++) {
        for (j = 0; j < c; j++) {
            sum[i][j] = A[i][j] + B[i][j];
            printf("%d ", sum[i][j]);
        }
        printf("\n");
    }
}

void matrixMultiplication() {
    int r1, c1, r2, c2, i, j, k;
    printf("Enter rows and columns for first matrix: ");
    scanf("%d %d", &r1, &c1);
    printf("Enter rows and columns for second matrix: ");
    scanf("%d %d", &r2, &c2);

    if (c1 != r2) {
        printf("Matrix multiplication not possible!\n");
        return;
    }

    int A[r1][c1], B[r2][c2], result[r1][c2];

    printf("Enter elements of first matrix:\n");
    for (i = 0; i < r1; i++)
        for (j = 0; j < c1; j++)
            scanf("%d", &A[i][j]);

    printf("Enter elements of second matrix:\n");
    for (i = 0; i < r2; i++)
        for (j = 0; j < c2; j++)
            scanf("%d", &B[i][j]);
    for (i = 0; i < r1; i++)
        for (j = 0; j < c2; j++)
            result[i][j] = 0;
    for (i = 0; i < r1; i++)
        for (j = 0; j < c2; j++)
            for (k = 0; k < c1; k++)
                result[i][j] += A[i][k] * B[k][j];

    printf("Resultant Matrix:\n");
    for (i = 0; i < r1; i++) {
        for (j = 0; j < c2; j++)
            printf("%d ", result[i][j]);
        printf("\n");
    }
}
void sumOfDigits() {
    int num, sum = 0;
    printf("Enter a number: ");
    scanf("%d", &num);
    
    while (num > 0) {
        sum += num % 10;
        num /= 10;
    }
    
    printf("Sum of digits: %d\n", sum);
}
void productOfDigits() {
    int num, product = 1;
    printf("Enter a number: ");
    scanf("%d", &num);
    
    while (num > 0) {
        product *= num % 10;
        num /= 10;
    }
    
    printf("Product of digits: %d\n", product);
}
void percentageCalculator() {
    double marksObtained, totalMarks;
    printf("Enter marks obtained: ");
    scanf("%lf", &marksObtained);
    printf("Enter total marks: ");
    scanf("%lf", &totalMarks);
    
    if (totalMarks == 0)
        printf("Error! Total marks cannot be zero.\n");
    else
        printf("Percentage: %.2lf%%\n", (marksObtained / totalMarks) * 100);
}
