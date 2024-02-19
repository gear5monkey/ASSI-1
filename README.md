# CR-for-a-reason1

1.	Aim:  To write a C program that initializes an array of integers with user-input values. The program should then find and print the sum and average of the array elements.
Algorithm: 
1.	Declare necessary variables:
o	An integer array to store user-input values.
o	Variables to store the sum and average of the array elements.
o	Variables for loop control and user input.
2.	Prompt the user to input the size of the array.
3.	Dynamically allocate memory for the array based on the user input.
4.	Use a loop to prompt the user to input values for each element of the array.
5.	Within the same loop, calculate the sum of the array elements.
6.	Calculate the average of the array elements by dividing the sum by the number of elements.
7.	Print the sum and average.
8.	End the program.
Code:

#include <stdio.h>

int main() {
    int arrsize;
    int *arr; /* creating an array that dynamically alloates memory */
    int sum = 0;
    float avg;

    
    printf("Enter the size of the array: ");
    scanf("%d", &arrsize); //we can enter size of the array required

    // Dynamically allocate memory for the array based on arraySize
    arr = (int *)malloc(arrsize * sizeof(int));

    // asking to input values
    printf("Enter %d integer values:\n", arrsize);
    for (int i = 0; i < arrsize; i++) {
        printf("Enter value for element %d: ", i + 1); /* asking the user to enter value for particular element */
        scanf("%d", &arr[i]);

        // Calculate the sum of the array elements
        sum += arr[i];
    }

    // Calculate the average of the array elements
    avg = (float)sum / arrsize;

    // Print the sum and average
    printf("Sum of array elements: %d\n", sum);
    printf("Average of array elements: %.2f\n", avg); //two decimal places

    return 0;
}

Output:
 


2.	Aim: To Implement a C function named find Largest Element that takes an integer array and its size as parameters. The function should find and return the largest element in the array.
Algorithm: 
1.	Include the necessary header file stdio.h.
2.	Define a function named findLargestElement that takes an integer array arr and its size size as parameters.
o	Initialize a variable largestvalue with the value of the first element of the array.
o	Iterate through the array starting from the second element.
	If the current element is greater than largestvalue, update largestvalue with the value of the current element.
o	Return largestvalue.
3.	In the main function:
o	Declare an integer variable elements.
o	Prompt the user to enter the number of elements.
o	Read the input for elements.
o	Declare an integer array arr of size elements.
o	Prompt the user to enter the array elements and store them in the array.
o	Calculate the number of elements in the array using sizeof(arr) / sizeof(arr[0]).
o	Call the findLargestElement function with the array and the number of elements as arguments, and store the result in largest.
o	Print the value of largest as the largest element in the array.
4.	End of the program.

Code:

#include <stdio.h>

int findLargestElement(int arr[], int size) {

    int largestvalue = arr[0]; // Initialize largest element with the first element of the array

    // Iterate through the array to find the largest element
    for (int i = 1; i < size; i++) {
        if (arr[i] > largestvalue) {
            largestvalue = arr[i];
        }
    }

    return largestvalue; // Return the largest element found
}

int main() {
    
    int elements;

    printf("Enter the number of elements \n");
    scanf("%d", &elements);

    int arr[elements];
    printf("Enter the array elemets\n");
    for(int i=0; i<elements; i++)
    {
        scanf("%d", &arr[i]);
    }

    int numberofelements = sizeof(arr) / sizeof(arr[0]); // this will return the number of elements
    //since we divide the total size by size of one element

    // Call the findLargestElement function
    int largest = findLargestElement(arr, numberofelements);

        printf("The largest element in the array is: %d\n", largest);

    return 0;
}
Output:
 


3.	Aim:  Create a C program that performs matrix multiplication. Allow the user to input two matrices, perform the multiplication, and display the result.

Algorithm:

1.	Include the necessary header file stdio.h.
2.	Define a function multMatrices to perform matrix multiplication. This function should take parameters for the two matrices to be multiplied (matrix1 and matrix2), the resulting matrix (resultMatrix), and the dimensions of the matrices (rows1, cols1, rows2, and cols2).
3.	Inside the multMatrices function:
o	Use nested loops to iterate through the rows and columns of the resulting matrix.
o	Within the nested loops, use another loop to iterate through the columns of the first matrix (or rows of the second matrix) to calculate each cell of the resulting matrix.
o	Multiply corresponding elements of the current row of the first matrix (matrix1) with the current column of the second matrix (matrix2) and accumulate the result in the corresponding cell of the resultMatrix.
4.	In the main function:
o	Declare variables for the two input matrices (matrix1 and matrix2), the resulting matrix (resultMatrix), and the dimensions of the matrices (rows1, cols1, rows2, and cols2).
o	Prompt the user to enter the dimensions of the first matrix (rows1 and cols1) and input the elements of the matrix.
o	Prompt the user to enter the dimensions of the second matrix (rows2 and cols2) and input the elements of the matrix.
o	Check if multiplication is possible (i.e., if cols1 equals rows2). If not, print an error message and exit.
o	Call the multMatrices function with the input matrices and dimensions to perform matrix multiplication.
o	Print the resulting matrix.
5.	End of the program.
Code:
6.	
7.	#include <stdio.h>
8.	
9.	// Function to perform matrix multiplication 
10.	void multmatrices(int mat1[][10], int mat2[][10], int result[][10], int rows1, int cols1, int cols2) {
11.	    // Initialize elements of result matrix to 0
12.	    for (int i = 0; i < rows1; i++) {
13.	        for (int j = 0; j < cols2; j++) {
14.	            result[i][j] = 0;
15.	        }
16.	    }
17.	
18.	    // Perform matrix multiplication
19.	    for (int i = 0; i < rows1; i++) {
20.	        for (int j = 0; j < cols2; j++) {
21.	            for (int k = 0; k < cols1; k++) {
22.	                result[i][j] += mat1[i][k] * mat2[k][j];
23.	            }
24.	        }
25.	    }
26.	}
27.	
28.	// Function to display a matrix
29.	void displayMatrix(int matrix[][10], int rows, int cols) {
30.	    for (int i = 0; i < rows; i++) {
31.	        for (int j = 0; j < cols; j++) {
32.	            printf("%d\t", matrix[i][j]);
33.	        }
34.	        printf("\n");
35.	    }
36.	}
37.	
38.	int main() {
39.	    int mat1[10][10], mat2[10][10], result[10][10];
40.	    int rows1, cols1, rows2, cols2;
41.	
42.	    // Input for first matrix
43.	    printf("Enter the number of rows and columns of the first matrix: ");
44.	    scanf("%d %d", &rows1, &cols1);
45.	
46.	    printf("Enter elements of the first matrix:\n");
47.	    for (int i = 0; i < rows1; i++) {
48.	        for (int j = 0; j < cols1; j++) {
49.	            scanf("%d", &mat1[i][j]);
50.	        }
51.	    }
52.	
53.	    // Input for second matrix
54.	    printf("Enter the number of rows and columns of the second matrix: ");
55.	    scanf("%d %d", &rows2, &cols2);
56.	
57.	    printf("Enter elements of the second matrix:\n");
58.	    for (int i = 0; i < rows2; i++) {
59.	        for (int j = 0; j < cols2; j++) {
60.	            scanf("%d", &mat2[i][j]);
61.	        }
62.	    }
63.	
64.	    // Check if multiplication is possible
65.	    if (cols1 != rows2) {
66.	        printf("Matrix multiplication is not possible.\n");
67.	        return 0;
68.	    }
69.	
70.	    // Perform matrix multiplication
71.	    multmatrices(mat1, mat2, result, rows1, cols1, cols2);
72.	
73.	    // Display the result
74.	    printf("Result of matrix multiplication:\n");
75.	    displayMatrix(result, rows1, cols2);
76.	
77.	    return 0;
78.	}

Output:
 



4.	Aim: To write a C function named reverseArray that takes an integer array and its size as parameters. The function should reverse the elements of the array in place.

Algorithm: 
1.	Include the necessary header file stdio.h.
2.	Define a function named reverseArray that takes two parameters: an integer array arr and its size size.
3.	Inside the reverseArray function:
o	Initialize two integers start and end to represent the start and end indices of the array, respectively. Set start to 0 and end to size - 1.
o	Use a while loop to iterate until the start index is less than the end index:
	Swap the elements at indices start and end in the array arr.
	Increment start and decrement end.
4.	In the main function:
o	Prompt the user to enter the number of elements.
o	Read the input for elements.
o	Declare an integer array arr of size elements.
o	Prompt the user to enter the elements of the array and store them in arr.
o	Calculate the size of the array by dividing the total size of the array by the size of one element.
o	Print the original array elements.
o	Call the reverseArray function to reverse the elements of the array arr.
o	Print the reversed array elements.    
    Code:
#include <stdio.h>

void reverseArray(int arr[], int size) {
    int start = 0; // Index of the first element
    int end = size - 1; // Index of the last element

    // Iterate until start index is less than end index
    while (start < end) {
        // Swap elements at start and end indices
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;

        // Move start index forward and end index backward
        start++;
        end--;
    }
}

int main() {
    int elements;

    printf("Enter the number of elements \n");
    scanf("%d", &elements);

    int arr[elements];
    printf("Enter the array elemets\n");
    for(int i=0; i<elements; i++)
    {
        scanf("%d", &arr[i]);
    }
    int size = sizeof(arr) / sizeof(arr[0]); // divide the total size of array by the size of one element to get number of elements

    printf("Original array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Call the reverseArray function
    reverseArray(arr, size);

    printf("Reversed array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}

Output:
 


5.	Aim: To develop a C program that implements a simple banking system. Use an array to store account balances. The program should allow the user to deposit and withdraw money from their account, display their current balance, and exit the system when desired. Ensure proper validation for withdrawal to prevent negative balances.

Algorithm:
1.	Include the necessary header file stdio.h.
2.	Define a constant MAX_ACCOUNTS to represent the maximum number of accounts.
3.	Define functions for displaying the menu options, depositing money into an account, withdrawing money from an account, and checking the balance of an account.
4.	In the main function:
o	Declare an array accounts of size MAX_ACCOUNTS to store account balances, initialized to all zeros.
o	Declare variables choice and accountNumber to store user input.
o	Display a welcome message.
o	Enter a loop to interact with the banking system until the user chooses to exit:
	Prompt the user to enter their account number.
	Check if the entered account number is valid (between 0 and MAX_ACCOUNTS - 1). If not, display an error message and continue to the next iteration of the loop.
	Display the menu options.
	Prompt the user to enter their choice.
	Based on the choice, call the corresponding function to deposit, withdraw, check balance, or exit.
	Repeat the loop until the user chooses to exit.
5.	End of the program.




Code:

#include <stdio.h>

#define MAX_ACCOUNTS 10

// Function to display menu options
void displayMenu() {
    printf("\n===== Simple Banking System =====\n");
    printf("1. Deposit\n");
    printf("2. Withdraw\n");
    printf("3. Check Balance\n");
    printf("4. Exit\n");
    printf("=================================\n");
}

// Function to deposit money into an account
void deposit(double accounts[], int accountNumber) {
    double amount;
    printf("Enter the amount to deposit: ");
    scanf("%lf", &amount);
    accounts[accountNumber] += amount;
    printf("Deposit successful.\n");
}

// Function to withdraw money from an account
void withdraw(double accounts[], int accountNumber) {
    double amount;
    printf("Enter the amount to withdraw: ");
    scanf("%lf", &amount);
    if (amount > accounts[accountNumber]) {
        printf("Insufficient funds.\n");
    } else {
        accounts[accountNumber] -= amount;
        printf("Withdrawal successful.\n");
    }
}

// Function to display the current balance of an account
void checkBalance(double accounts[], int accountNumber) {
    printf("Your current balance: $%.2f\n", accounts[accountNumber]);
}

int main() {
    double accounts[MAX_ACCOUNTS] = {0}; // Initialize all account balances to 0
    int choice, accountNumber;

    printf("Welcome to the Simple Banking System!\n");

    do {
        printf("\nEnter your account number (0-%d): ", MAX_ACCOUNTS - 1);
        scanf("%d", &accountNumber);

        if (accountNumber < 0 || accountNumber >= MAX_ACCOUNTS) {
            printf("Invalid account number. Please try again.\n");
            continue;
        }

        displayMenu();
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                deposit(accounts, accountNumber);
                break;
            case 2:
                withdraw(accounts, accountNumber);
                break;
            case 3:
                checkBalance(accounts, accountNumber);
                break;
            case 4:
                printf("Exiting the system. Thank you!\n");
                break;
            default:
                printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 4);

    return 0;
}


Output:  

6.	Aim: To write a C program that demonstrates the conversion of data types. Prompt the user to enter values of different data types (int, float, char) and convert them to other data types. Display the original and converted values.

Algorithm: 
1.	Include the necessary header files (stdio.h for input/output operations).
2.	Declare variables for storing values of different data types: int, float, and char.
3.	Prompt the user to enter values for each data type.
4.	Read the user input for each data type using scanf.
5.	Display the original values entered by the user.
6.	Perform type conversion for each data type and display the converted values.
7.	Return 0 to indicate successful execution.
8.	End.

Code:

#include <stdio.h>

int main() {
    int intValue;
    float floatValue;
    char charValue;

    // Prompt the user to enter values of different data types
    printf("Enter an integer value: ");
    scanf("%d", &intValue);

    printf("Enter a float value: ");
    scanf("%f", &floatValue);

    printf("Enter a character: ");
    scanf(" %c", &charValue);

    // Display original values
    printf("\nOriginal values:\n");
    printf("Integer: %d\n", intValue);
    printf("Float: %.2f\n", floatValue);
    printf("Character: %c\n", charValue);

    // Convert integer to float and character
    float convertedFloat = (float)intValue;
    char convertedChar = (char)intValue;

    // Convert float to integer and character
    int convertedInt = (int)floatValue;
    char convertedChar2 = (char)floatValue;

    // Convert character to integer and float
    int convertedInt2 = (int)charValue;
    float convertedFloat2 = (float)charValue;

    // Display converted values
    printf("\nConverted values:\n");
    printf("Integer from float: %d\n", convertedInt);
    printf("Character from float: %c\n", convertedChar2);
    printf("Float from integer: %.2f\n", convertedFloat);
    printf("Character from integer: %c\n", convertedChar);
    printf("Integer from character: %d\n", convertedInt2);
    printf("Float from character: %.2f\n", convertedFloat2);

    return 0;
}

Output:
 

7.	Aim: To develop a C program that showcases the use of all four storage classes (auto, register, static, and extern). Create variables with each storage class and demonstrate their scope and lifetime in different functions.

Algorithm: 

1. Include the necessary header files (e.g., <stdio.h>).
2. Declare an external variable with the `extern` storage class.
3. Define a function `function1` to demonstrate the use of `auto` storage class:
    a. Inside `function1`, declare an automatic variable.
    b. Print the value of the automatic variable.
4. Define a function `function2` to demonstrate the use of `static` storage class:
    a. Inside `function2`, declare a static variable.
    b. Print the value of the static variable.
    c. Modify the static variable's value.
5. Define the `main` function:
    a. Declare a register variable.
    b. Print the value of the register variable.
    c. Call `function1`.
    d. Call `function2`.
    e. Print the value of the external variable.
6. Define the external variable with an initial value.


Code: 


#include <stdio.h>

// Global variable with external linkage
extern int externVar;

void function1() {
    // Automatic variable
    auto int autoVar = 29;
    printf("Inside function1 - autoVar: %d\n", autoVar);
}

void function2() {
    // Static variable
    static int staticVar = 10;
    printf("Inside function2 - staticVar: %d\n", staticVar);
    // Modify the static variable
    staticVar++;
}

int main() {
    // Register variable
    register int registerVar = 15;
    printf("Inside main - registerVar: %d\n", registerVar);
    
    function1();
    function2();

    // Global variable
    printf("Inside main - externVar: %d\n", externVar);

    return 0;
}

// Define external variable
int externVar = 125;

Output:

 







8.	Aim: Implement a generic binary search function in C that works for any data type. The program should allow the user to input an array of any data type and a key to search for. Display whether the key is found or not.

Algorithm: 

1. Include the necessary header file <stdio.h>.
2. Define a binary search function `binarySearch` that takes an integer array, its size, and the key to search for:
    a. Initialize low as 0 and high as size - 1.
    b. Repeat while low is less than or equal to high:
        i. Compute mid as low + (high - low) / 2.
        ii. If the key is found at the middle (arr[mid] == key), return mid.
        iii. If the key is in the left half (arr[mid] > key), update high to mid - 1.
        iv. If the key is in the right half (arr[mid] < key), update low to mid + 1.
    c. If the key is not found after the loop, return -1.
3. Define the main function:
    a. Declare variables i, n, and key.
    b. Prompt the user to enter the number of elements and read the input into n.
    c. Declare an integer array arr of size n.
    d. Prompt the user to enter the array elements in ascending order and read them into arr.
    e. Prompt the user to enter the key to be searched and read it into key.
    f. Call the binarySearch function with arr, n, and key, and store the result in index.
    g. If index is not equal to -1, print "Key <key> found at index <index>".
    h. If index is equal to -1, print "Key <key> not found".
4. End of the program.



Code:


#include <stdio.h>

// Binary search function
int binarySearch(int arr[], int size, int key) {
    int low = 0;
    int high = size-1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        // If the key is found at the middle
        if (arr[mid] == key) {
            return mid;
        }
        // If the key is in the left half
        else if (arr[mid] > key) {
            high = mid - 1;
        }
        // If the key is in the right half
        else {
            low = mid + 1;
        }
    }

    // Key not found
    return -1;
}

int main() {
    int i,n, key;
    printf("Enter the number of elements\n");
    scanf("%d", &n);
    int arr[n];
    printf("Enter the array elements in ascending order\n");

    for(int i=0;i<n;i++)
    {
        scanf("%d", &arr[i]);
    }
    printf("Enter the key to be searched\n");
    scanf("%d", &key);
    int index = binarySearch(arr, n, key);
    
    if (index != -1) {
        printf("Key %d found at index %d\n", key, index);
    } else {
        printf("Key %d not found\n", key);
    }

    return 0;
}


Output:

 




9.	Aim: To write a C program to perform bitwise operations on two integers. Prompt the user to enter two integers, perform bitwise AND, OR, XOR, and left shift operations, and display the results.

Algorithm: 
1. Start.
2. Include the necessary header file <stdio.h>.
3. Declare variables num1 and num2 to store the input integers.
4. Prompt the user to enter the first integer and read it into num1.
5. Prompt the user to enter the second integer and read it into num2.
6. Perform bitwise AND operation:
    a. Calculate the result by performing num1 & num2.
    b. Print the result.
7. Perform bitwise OR operation:
    a. Calculate the result by performing num1 | num2.
    b. Print the result.
8. Perform bitwise XOR operation:
    a. Calculate the result by performing num1 ^ num2.
    b. Print the result.
9. Perform left shift operation:
    a. Calculate the result by performing num1 << 1.
    b. Print the result.
10. End.


Code:


#include <stdio.h>

int main() {
    int num1, num2, bits;

    // Prompt the user to enter two integers
    printf("Enter the first integer: ");
    scanf("%d", &num1);
    printf("Enter the second integer: ");
    scanf("%d", &num2);

    // Perform bitwise AND, OR, XOR, and left shift operations
    int result_and = num1 & num2;
    int result_or = num1 | num2;
    int result_xor = num1 ^ num2;
    printf("Enter the number of bits to be left shifted\n");
    scanf("%d", &bits);
    int result_left_shift1 = num1 << bits; // Left shift num1 by number of bits
    
    int result_left_shift2 = num2 << bits; // Left shift num1 by number of bits

    // Display the results
    printf("Bitwise AND result: %d\n", result_and);
    printf("Bitwise OR result: %d\n", result_or);
    printf("Bitwise XOR result: %d\n", result_xor);
    printf("Left shift result for %d: %d\n", num1, result_left_shift1);
    printf("Left shift result for %d: %d\n", num2, result_left_shift2);

    return 0;
}

Output:

 










10.	 Aim: To Create a C program that dynamically allocates memory for a 2D array based on user input for rows and columns. Populate the array with random values and implement a function to find the sum of elements in each row.

Algorithm:

1.	Main Function:
o	Prompt the user to enter the number of rows and columns.
o	Allocate memory for a 2D array using the dynamic2dArray function.
o	Calculate and print the sum of each row using the sumOfRows function.
o	Free dynamically allocated memory.
o	Return 0 to indicate successful execution.
2.	Dynamic2dArray Function:
o	Takes the number of rows and columns as input.
o	Allocate memory for an array of row pointers.
o	Check if memory allocation for rows was successful.
o	Allocate memory for each row.
o	Check if memory allocation for columns was successful.
o	Prompt the user to enter elements for each cell.
o	Return the dynamically allocated 2D array.
3.	SumOfRows Function:
o	Takes the 2D array, number of rows, and number of columns as input.
o	Iterate over each row.
o	For each row, calculate the sum of its elements.
o	Print the sum of elements in each row.

#include<stdio.h>
#include<stdlib.h>
 
// Function prototypes
int **dynamic2dArray(int, int);
void sumOfRows(int **, int, int);
 
int main() {
   int **arr2d, rows, cols;
 
   // Get the number of rows from the user
   printf("Enter the number of rows: ");
   scanf("%d", &rows);
 
   // Get the number of columns from the user
   printf("Enter the number of columns: ");
   scanf("%d", &cols);
 
   // Allocate memory for the 2D array
   arr2d = dynamic2dArray(rows, cols);
 
   // Calculate and print the sum of each row
   sumOfRows(arr2d, rows, cols);
 
   // Free dynamically allocated memory
   for (int i = 0; i < rows; i++) {
       free(arr2d[i]);
   }
   free(arr2d);
 
   return 0;
}
 
// Function to dynamically allocate memory for a 2D array
int **dynamic2dArray(int rows, int cols) {
   // Allocate memory for the array of row pointers
   int **arr = (int **)malloc(rows * sizeof(int *));
   if (arr == NULL) {
       printf("Memory allocation failed for rows\n");
       return NULL;
   }
 
   // Allocate memory for each row
   for (int i = 0; i < rows; i++) {
       arr[i] = (int *)malloc(cols * sizeof(int));
       if (arr[i] == NULL) {
           printf("Memory allocation failed for cols\n");
           // Free previously allocated memory
           for (int j = 0; j < i; j++)
               free(arr[j]);
           free(arr);
           return NULL;
       }
   }
 
   // Get input elements from the user
   printf("Enter the elements\n");
   for (int i = 0; i < rows; i++) {
       for (int j = 0; j < cols; j++) {
           scanf("%d", &arr[i][j]);
       }
   }
 
   return arr;
}
 
// Function to calculate and print the sum of each row
void sumOfRows(int **arr, int row, int col) {
   int sum;
   for (int i = 0; i < row; i++) {
       sum = 0;
       printf("Sum of elements in row %d:", i + 1);
       for (int j = 0; j < col; j++) {
           sum += arr[i][j];
       }
       printf("%d\n", sum);
   }
}

Output:
 
