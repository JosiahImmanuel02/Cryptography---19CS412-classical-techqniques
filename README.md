# Cryptography---19CS412-classical-techqniques

## Name: Josiah Immanuel A
## Reg no: 212223043003

# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To encrypt and decrypt the given message by using Ceaser Cipher encryption algorithm.


## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

1.	In Ceaser Cipher each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet.
2.	For example, with a left shift of 3, D would be replaced by A, E would become B, and so on.
3.	The encryption can also be represented using modular arithmetic by first transforming the letters into numbers, according to the   
    scheme, A = 0, B = 1, Z = 25.
4.	Encryption of a letter x by a shift n can be described mathematically as,
                       En(x) = (x + n) mod26
5.	Decryption is performed similarly,
                       Dn (x)=(x - n) mod26


## PROGRAM:
```
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char plain[100], cipher[100];
    int key, i, length;

    printf("Enter the plain text: ");
    scanf("%s", plain);

    printf("Enter the key value: ");
    scanf("%d", &key);

    printf("\nPLAIN TEXT: %s", plain);
    printf("\nENCRYPTED TEXT: ");

    length = strlen(plain);
    
    for (i = 0; i < length; i++) {
        cipher[i] = plain[i] + key;

        
        if (isupper(plain[i]) && cipher[i] > 'Z') {
            cipher[i] = cipher[i] - 26;
        }

        
        if (islower(plain[i]) && cipher[i] > 'z') {
            cipher[i] = cipher[i] - 26;
        }

        printf("%c", cipher[i]);
    }

    cipher[length] = '\0'; 
    printf("\nDECRYPTED TEXT: ");

    for (i = 0; i < length; i++) {
        plain[i] = cipher[i] - key;

        
        if (isupper(cipher[i]) && plain[i] < 'A') {
            plain[i] = plain[i] + 26;
        }

       
        if (islower(cipher[i]) && plain[i] < 'a') {
            plain[i] = plain[i] + 26;
        }

        printf("%c", plain[i]);
    }

    plain[length] = '\0'; 
    return 0;
}
```


## OUTPUT:
![Screenshot 2025-03-19 090622](https://github.com/user-attachments/assets/4582d85b-d56d-4844-b999-9419b844303a)



## Input : Josiah
Encrypted Message : Nswmel 
Decrypted Message :Josiah

## RESULT:
The program is executed successfully

