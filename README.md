# Ex-5 Rail-Fence-Program

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
```.py
#include <stdio.h>
#include <string.h>

int main() {
    int rails, len, i, j, dir;
    char str[1000];

    printf("Enter a Secret Message: ");
    fgets(str, sizeof(str), stdin);

    // remove newline
    str[strcspn(str, "\n")] = '\0';

    len = strlen(str);

    printf("Enter number of rails: ");
    scanf("%d", &rails);

    char rail[rails][len];

    // fill with newline marker
    for(i = 0; i < rails; i++)
        for(j = 0; j < len; j++)
            rail[i][j] = '\n';

    dir = 1;  // 1=down, -1=up
    int row = 0;

    // place characters in zig-zag
    for(i = 0; i < len; i++) {
        rail[row][i] = str[i];

        if(row == 0)
            dir = 1;
        else if(row == rails - 1)
            dir = -1;

        row += dir;
    }

    printf("\nEncrypted Message: ");

    // read row-wise
    for(i = 0; i < rails; i++)
        for(j = 0; j < len; j++)
            if(rail[i][j] != '\n')
                printf("%c", rail[i][j]);

    printf("\n");

    return 0;
}
```

# OUTPUT
<img width="411" height="165" alt="image" src="https://github.com/user-attachments/assets/d429ad69-7cff-499f-a007-21b4e0d32c61" />

# RESULT
The program is executed successfully


