# Ex-1 IMPLEMENTATION-OF-SYMBOL-TABLE
# Register Number :
# Date : 
# AIM :
## To write a C program to implement a symbol table.
# ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol and memory address are inserted into the symbol table.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and the symbol table has been checked for the corresponding variable, the variable along with its address is displayed as a result.
8.	Stop the program. 
# PROGRAM
```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_SYMBOLS 100

// Structure to represent a symbol table entry
typedef struct {
    char name[50];
    void *address;
} Symbol;

Symbol symbolTable[MAX_SYMBOLS];
int symbolCount = 0;

// Function to insert a symbol into the table
void insertSymbol(char *name) {
    if (symbolCount >= MAX_SYMBOLS) {
        printf("Symbol table is full!\n");
        return;
    }
    symbolTable[symbolCount].address = malloc(sizeof(int)); // Allocating memory dynamically
    if (symbolTable[symbolCount].address == NULL) {
        printf("Memory allocation failed!\n");
        return;
    }
    strcpy(symbolTable[symbolCount].name, name);
    printf("Inserted: %s at address %p\n", name, symbolTable[symbolCount].address);
    symbolCount++;
}

// Function to search for a symbol in the table
void searchSymbol(char *name) {
    for (int i = 0; i < symbolCount; i++) {
        if (strcmp(symbolTable[i].name, name) == 0) {
            printf("Symbol found: %s at address %p\n", name, symbolTable[i].address);
            return;
        }
    }
    printf("Symbol not found!\n");
}

int main() {
    char input[50];
    printf("Enter symbols (end with $):\n");
    
    while (1) {
        scanf("%s", input);
        if (strcmp(input, "$") == 0) {
            break;
        }
        insertSymbol(input);
    }
    
    // Search functionality
    printf("\nEnter variable to search: ");
    scanf("%s", input);
    searchSymbol(input);
    
    // Free allocated memory
    for (int i = 0; i < symbolCount; i++) {
        free(symbolTable[i].address);
    }
    
    return 0;
}
```
# OUTPUT
![asssigent 1 screen 1](https://github.com/user-attachments/assets/c7cee24c-ec7f-4014-aff8-f96e1e37d872)

# RESULT
### The program to implement a symbol table is executed and the output is verified.
