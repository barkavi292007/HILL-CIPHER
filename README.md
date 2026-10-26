# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user.
STEP-2: Split the plain text into groups of length three.
STEP-3: Arrange the keyword in a 3*3 matrix.
STEP-4: Multiply the two matrices to obtain the cipher text of length three.
STEP-5: Combine all these groups to get the complete cipher text.

## PROGRAM
```

#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char plain[100], cipher[100];
    int key[2][2] = {{3, 3}, {2, 5}};
    int inv[2][2] = {{15, 17}, {20, 9}};
    int i, a, b, x, y, n;

    printf("Enter plaintext: ");
    scanf("%99s", plain);

    n = strlen(plain);

    if (n % 2 != 0) {
        printf("Plaintext length must be even.\n");
        return 0;
    }

    for (i = 0; i < n; i++) {
        if (!isalpha((unsigned char)plain[i])) {
            printf("Enter alphabets only.\n");
            return 0;
        }
        plain[i] = toupper((unsigned char)plain[i]);
    }

    for (i = 0; i < n; i += 2) {
        a = plain[i] - 'A';
        b = plain[i + 1] - 'A';

        x = (key[0][0] * a + key[0][1] * b) % 26;
        y = (key[1][0] * a + key[1][1] * b) % 26;

        cipher[i] = x + 'A';
        cipher[i + 1] = y + 'A';
    }
    cipher[n] = '\0';

    printf("Encrypted text: %s\n", cipher);

    for (i = 0; i < n; i += 2) {
        a = cipher[i] - 'A';
        b = cipher[i + 1] - 'A';

        x = (inv[0][0] * a + inv[0][1] * b) % 26;
        y = (inv[1][0] * a + inv[1][1] * b) % 26;

        plain[i] = x + 'A';
        plain[i + 1] = y + 'A';
    }
    plain[n] = '\0';

    printf("Decrypted text: %s\n", plain);

    return 0;
}

```
## OUTPUT

<img width="1913" height="775" alt="Screenshot 2026-10-26 110018" src="https://github.com/user-attachments/assets/aa76aa4e-5ce3-43a4-9294-5d54ffe3400d" />


## RESULT
Thus, the Hill Cipher encryption and decryption program was implemented successfully using C.
