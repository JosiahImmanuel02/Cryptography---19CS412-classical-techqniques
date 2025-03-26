# Cryptography---19CS412-classical-techqniques

# Hill Cipher
Hill Cipher using with different key values

# Reg no : 212223043003
# Name :   Josiah Immanuel A

## AIM:
To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:
## Step 1:
Design of Hill Cipher algorithnm

## Step 2:
Implementation using C or pyhton code

## Step 3:
Testing algorithm with different key values. 

## ALGORITHM DESCRIPTION: 

The Playfair cipher uses a 5 by 5 table containing a key word or phrase. To generate the key table, first fill the spaces in the table with the letters of the keyword, then fill the remaining spaces with the rest of the letters of the alphabet in order (usually omitting "Q" to reduce the alphabet to fit; other versions put both "I" and "J" in the same space). The key can be written in the top rows of the table, from left to right, or in some other pattern, such as a spiral beginning in the upper-left-hand corner and ending in the centre. The keyword together with the conventions for filling in the 5 by 5 table constitutes the cipher key. To encrypt a message, one would break the message into digrams (groups of 2 letters) such that, for example, "HelloWorld" becomes "HE LL OW OR LD", and map them out on the key table. Then apply the following 4 rules, to each pair of letters in the plaintext:

If both letters are the same (or only one letter is left), add an "X" after the first letter. Encrypt the new pair and continue. Some
variants of Playfair use "Q" instead of "X", but any letter, itself uncommon as a repeated pair, will do.

If the letters appear on the same row of your table, replace them with the letters to their immediate right respectively (wrapping around to the left side of the row if a letter in the original pair was on the right side of the row).

If the letters appear on the same column of your table, replace them with the letters immediately below respectively (wrapping around to the top side of the column if a letter in the original pair was on the bottom side of the column).

If the letters are not on the same row or column, replace them with the letters on the same row respectively but at the other pair of corners of the rectangle defined by the original pair. The order is important – the first letter of the encrypted pair is the one that lies on the same row as the first letter of the plaintext pair. To decrypt, use the INVERSE (opposite) of the last 3 rules, and the 1st as-is (dropping any extra "X"s, or "Q"s that do not make sense in the final message when finished).

## PROGRAM: 
```

#include <stdio.h>
#include <string.h>

int main() {
    unsigned int a[3][3] = {{6, 24, 1}, {13, 16, 10}, {20, 17, 15}};
    unsigned int b[3][3] = {{8, 5, 10}, {21, 8, 21}, {21, 12, 8}};
    int i, j, t = 0;
    unsigned int c[3], d[3];
    char msg[4]; 

    printf("Enter plain text (3 letters): ");
    scanf("%3s", msg); 

   
    if (strlen(msg) != 3) {
        printf("Error: The plain text must be exactly 3 letters.\n");
        return 1;
    }

    
    for (i = 0; i < 3; i++) {
        c[i] = msg[i] - 'A';
        printf("%d ", c[i]); 
'
    for (i = 0; i < 3; i++) {
        t = 0;
        for (j = 0; j < 3; j++) {
            t += a[i][j] * c[j];
        }
        d[i] = t % 26; 
    }


    printf("\nEncrypted Cipher Text: ");
    for (i = 0; i < 3; i++) {
        printf("%c", d[i] + 'A');
    }

    
    for (i = 0; i < 3; i++) {
        t = 0;
        for (j = 0; j < 3; j++) {
            t += b[i][j] * d[j];
        }
        c[i] = t % 26; 
    }

   
    printf("\nDecrypted Cipher Text: ");
    for (i = 0; i < 3; i++) {
        printf("%c", c[i] + 'A');
    }

    getchar(); 
    return 0;
}
     
```



## OUTPUT:
OUTPUT: Simulating Hill Cipher ![Screenshot 2025-03-26 085207](https://github.com/user-attachments/assets/0a78b4ac-9f07-40ac-b9b2-54d11e41180a)


## RESULT:
The program is executed successfully


