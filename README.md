# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main()
{
    int i, j, k, l;
    char a[20], c[20], d[20];

    printf("\n\t\tRAIL FENCE TECHNIQUE\n");

    // Input string
    printf("\nEnter the input string: ");
    fgets(a, sizeof(a), stdin);

    // Remove newline character if exists
    a[strcspn(a, "\n")] = '\0';

    l = strlen(a); // length of input

    // ---------------- Encryption ----------------
    j = 0;
    // First collect even indices
    for (i = 0; i < l; i++) {
        if (i % 2 == 0) {
            c[j++] = a[i];
        }
    }
    // Then collect odd indices
    for (i = 0; i < l; i++) {
        if (i % 2 == 1) {
            c[j++] = a[i];
        }
    }
    c[j] = '\0';  // null terminate

    printf("\nCipher text after applying rail fence: %s\n", c);

    // ---------------- Decryption ----------------
    if (l % 2 == 0) {
        k = l / 2;
    } else {
        k = (l / 2) + 1;
    }

    // Place even-position characters back
    for (i = 0, j = 0; i < k; i++) {
        d[j] = c[i];
        j += 2;
    }

    // Place odd-position characters back
    for (i = k, j = 1; i < l; i++) {
        d[j] = c[i];
        j += 2;
    }

    d[l] = '\0';  // null terminate

    printf("\nText after decryption: %s\n", d);

    return 0;
}
```

# OUTPUT
<img width="589" height="357" alt="image" src="https://github.com/user-attachments/assets/4e79e17c-39b7-49b7-a914-9668f5e589b3" />

# RESULT
Thus the implementation of rail fence cipher had been executed successfully.
