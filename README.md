# Task-2
#include <stdio.h>

// Function prototypes

void readMatrix(int a[10][10], int r, int c);
void printMatrix(int a[10][10], int r, int c);
void addMatrix(int a[10][10], int b[10][10], int r, int c);
void multiplyMatrix(int a[10][10], int b[10][10], int r1, int c1, int r2, int c2);
void transposeMatrix(int a[10][10], int r, int c);

int main() {
    int a[10][10], b[10][10];
    int r1, c1, r2, c2;
    int choice;

    do {
        printf("\n--- Matrix Operations ---");
        printf("\n1. Matrix Addition");
        printf("\n2. Matrix Multiplication");
        printf("\n3. Transpose");
        printf("\n4. Exit");
        printf("\nEnter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter rows and columns: ");
                scanf("%d %d", &r1, &c1);

                printf("Enter first matrix:\n");
                readMatrix(a, r1, c1);

                printf("Enter second matrix:\n");
                readMatrix(b, r1, c1);

                addMatrix(a, b, r1, c1);
                break;

            case 2:
                printf("Enter rows and columns of first matrix: ");
                scanf("%d %d", &r1, &c1);

                printf("Enter rows and columns of second matrix: ");
                scanf("%d %d", &r2, &c2);

                if (c1 != r2) {
                    printf("Matrix multiplication not possible!\n");
                } else {
                    printf("Enter first matrix:\n");
                    readMatrix(a, r1, c1);

                    printf("Enter second matrix:\n");
                    readMatrix(b, r2, c2);

                    multiplyMatrix(a, b, r1, c1, r2, c2);
                }
                break;

            case 3:
                printf("Enter rows and columns: ");
                scanf("%d %d", &r1, &c1);

                printf("Enter matrix:\n");
                readMatrix(a, r1, c1);

                transposeMatrix(a, r1, c1);
                break;

            case 4:
                printf("Exiting program.\n");
                break;

            default:
                printf("Invalid choice!\n");
        }
    } while (choice != 4);

    return 0;
}

// Function to read a matrix
void readMatrix(int a[10][10], int r, int c) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            scanf("%d", &a[i][j]);
        }
    }
}

// Function to print a matrix
void printMatrix(int a[10][10], int r, int c) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            printf("%d ", a[i][j]);
        }
        printf("\n");
    }
}

// Function for matrix addition
void addMatrix(int a[10][10], int b[10][10], int r, int c) {
    int sum[10][10];
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            sum[i][j] = a[i][j] + b[i][j];
        }
    }
    printf("Resultant Matrix (Addition):\n");
    printMatrix(sum, r, c);
}

// Function for matrix multiplication
void multiplyMatrix(int a[10][10], int b[10][10], int r1, int c1, int r2, int c2) {
    int mul[10][10] = {0};

    for (int i = 0; i < r1; i++) {
        for (int j = 0; j < c2; j++) {
            for (int k = 0; k < c1; k++) {
                mul[i][j] += a[i][k] * b[k][j];
            }
        }
    }

    printf("Resultant Matrix (Multiplication):\n");
    printMatrix(mul, r1, c2);
}

// Function for transpose
void transposeMatrix(int a[10][10], int r, int c) {
    int t[10][10];

    for (int i = 0; i < r; i++) {
        for (int j = 0; j < c; j++) {
            t[j][i] = a[i][j];
        }
    }

    printf("Transpose of Matrix:\n");
    printMatrix(t, c, r);
}
