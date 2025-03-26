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
#include <ctype.h> 

int keymat[3][3] = {
    { 1, 2, 1 },
    { 2, 3, 2 },
    { 2, 2, 1 }
};

int invkeymat[3][3] = {
    { -1, 0, 1 },
    { 2, -1, 0 },
    { -2, 2, -1 }
};

char key[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";


char* encode(char a, char b, char c) {
    static char ret[4];  
    int x, y, z;
    int posa = (int) a - 65;
    int posb = (int) b - 65;
    int posc = (int) c - 65;
    
    x = posa * keymat[0][0] + posb * keymat[1][0] + posc * keymat[2][0];
    y = posa * keymat[0][1] + posb * keymat[1][1] + posc * keymat[2][1];
    z = posa * keymat[0][2] + posb * keymat[1][2] + posc * keymat[2][2];
    
    ret[0] = key[x % 26];
    ret[1] = key[y % 26];
    ret[2] = key[z % 26];
    ret[3] = '\0';  
    
    return ret;
}


char* decode(char a, char b, char c) {
    static char ret[4];  
    int x, y, z;
    int posa = (int) a - 65;
    int posb = (int) b - 65;
    int posc = (int) c - 65;
    
    x = posa * invkeymat[0][0] + posb * invkeymat[1][0] + posc * invkeymat[2][0];
    y = posa * invkeymat[0][1] + posb * invkeymat[1][1] + posc * invkeymat[2][1];
    z = posa * invkeymat[0][2] + posb * invkeymat[1][2] + posc * invkeymat[2][2];
    
    ret[0] = key[(x % 26 < 0) ? (26 + x % 26) : (x % 26)];
    ret[1] = key[(y % 26 < 0) ? (26 + y % 26) : (y % 26)];
    ret[2] = key[(z % 26 < 0) ? (26 + z % 26) : (z % 26)];
    ret[3] = '\0';  
    
    return ret;
}

int main() {
    char msg[1000];
    char enc[1000] = "";  
    char dec[1000] = "";  
    int n;

    // Get input message from the user
    printf("Enter the message to encrypt: ");
    fgets(msg, sizeof(msg), stdin);
    msg[strcspn(msg, "\n")] = '\0'; 

    printf("Simulation of Hill Cipher\n");
    printf("Input message : %s\n", msg);

    
    for (int i = 0; i < strlen(msg); i++) {
        msg[i] = toupper(msg[i]);
    }

    
    n = strlen(msg) % 3;
    if (n != 0) {
        for (int i = 1; i <= (3 - n); i++) {
            strcat(msg, "X");
        }
    }

    printf("Padded message : %s\n", msg);

   
    for (int i = 0; i < strlen(msg); i += 3) {
        char a = msg[i];
        char b = msg[i + 1];
        char c = msg[i + 2];
        strcat(enc, encode(a, b, c));
    }

    printf("Encoded message : %s\n", enc);

    for (int i = 0; i < strlen(enc); i += 3) {
        char a = enc[i];
        char b = enc[i + 1];
        char c = enc[i + 2];
        strcat(dec, decode(a, b, c));
    }

    printf("Decoded message : %s\n", dec);

    return 0;
}
```



## OUTPUT:
OUTPUT: Simulating Hill Cipher ![Screenshot 2025-03-26 083617](https://github.com/user-attachments/assets/84bf9151-7660-4d66-99a5-4a3b0fd8f102)

## RESULT:
The program is executed successfully


