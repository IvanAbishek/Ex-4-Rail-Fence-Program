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
    char text[100];
    int i, key, len;

    printf("Enter plaintext: ");
    fgets(text, sizeof(text), stdin);
    text[strcspn(text, "\n")] = '\0';

    printf("Enter key (number of rails): ");
    scanf("%d", &key);

    len = strlen(text);

    if (key <= 1 || key > len)
    {
        printf("Invalid key\n");
        return 0;
    }

    printf("Encrypted text: ");

    for (i = 0; i < key; i++)
    {
        int j;

        for (j = i; j < len; j += 2 * (key - 1))
        {
            printf("%c", text[j]);

            if (i != 0 && i != key - 1)
            {
                int k = j + 2 * (key - 1 - i);

                if (k < len)
                    printf("%c", text[k]);
            }
        }
    }

    printf("\n");
    return 0;
}
```
# OUTPUT
<img width="765" height="157" alt="image" src="https://github.com/user-attachments/assets/15e463b7-1799-4b72-bebd-30da53371fe6" />

# RESULT
The C program for Rail fence program is executed sucessfully and the output is verified
