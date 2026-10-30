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

int main()
{
    char text[] = "BHARGAVI";
    char encrypted[100], decrypted[100];
    int key[2][2] = {{3, 3}, {2, 5}};
    int i, a, b, c, d;

    printf("Plaintext: %s\n", text);

    // Encryption
    for(i = 0; i < strlen(text); i += 2)
    {
        a = text[i] - 'A';
        b = text[i+1] - 'A';

        encrypted[i] = ((key[0][0]*a + key[0][1]*b) % 26) + 'A';
        encrypted[i+1] = ((key[1][0]*a + key[1][1]*b) % 26) + 'A';
    }
    encrypted[i] = '\0';

    printf("Encrypted Text: %s\n", encrypted);

    // Decryption (Inverse Key = {{15, 17}, {20, 9}})
    for(i = 0; i < strlen(encrypted); i += 2)
    {
        a = encrypted[i] - 'A';
        b = encrypted[i+1] - 'A';

        c = (15*a + 17*b) % 26;
        d = (20*a + 9*b) % 26;

        decrypted[i] = c + 'A';
        decrypted[i+1] = d + 'A';
    }
    decrypted[i] = '\0';

    printf("Decrypted Text: %s\n", decrypted);

    return 0;
}

```
## OUTPUT
<img width="921" height="478" alt="image" src="https://github.com/user-attachments/assets/57c9e89a-2fd6-4a1e-a8b9-0030c198b1d9" />

## RESULT
Thus, the Hill Cipher encryption and decryption program was implemented successfully using C.
