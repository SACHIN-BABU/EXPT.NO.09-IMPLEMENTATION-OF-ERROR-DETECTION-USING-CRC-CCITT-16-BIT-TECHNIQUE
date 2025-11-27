# EXPT.NO.09-IMPLEMENTATION-OF-ERROR-DETECTION-USING-CRC-CCITT-16-BIT-TECHNIQUE
# AIM:
To write a program for error Detection using Cyclic Redundancy Check (CRC-16 bit) technique.

# EQUIPMENTS REQUIRED:
1.	Personal Computer
2.	C++ compiler

# ALGORITHM:
1] Open code blocks application and create a new file. 2] After creating the file type the codes.
3] After typing the codes save the file using the .c extension in the desired location. 4] Run the program using build and run.
5] Give polynomial values and the generated polynomial is obtained, and by other means arraive	at the desired output which uses the error detection technique. 6] Thus the output polynomial is obtained through this technique.

# PROGRAM:
```
#include <stdio.h> 
#include <string.h> 
char t[128], cs[128], g[128]; 
int a, e, c, N; 
void xorOperation() 
{ 
for (c = 1; c < N; c++) 
cs[c] = ((cs[c] == g[c]) ? '0' : '1'); 
} 
void crc() 
{ 
for (e = 0; e < N; e++) 
cs[e] = t[e]; 
do 
{ 
if (cs[0] == '1') 
xorOperation(); 
for (c = 0; c < N - 1; c++) 
cs[c] = cs[c + 1]; 
cs[c] = t[e++]; 
} while (e <= a + N - 1); 
} 
int main() 
{ 
printf("\nEnter Data: "); 
scanf("%s", t);
printf("Enter Generator Polynomial: "); 
scanf("%s", g); 
a = strlen(t); 
N = strlen(g); 
for (e = a; e < a + N - 1; e++) 
t[e] = '0'; 
t[e] = '\0'; 
printf("\nModified Data: %s", t); 
crc(); 
printf("\nChecksum (Remainder): "); 
for (e = 0; e < N - 1; e++) 
printf("%c", cs[e]); 
printf("\n"); 
for (e = a; e < a + N - 1; e++) 
t[e] = cs[e - a]; 
t[e] = '\0'; 
printf("\nFinal Code Word: %s\n", t); 
printf("\nTest Error Detection? (0 = Yes, 1 = No): "); 
scanf("%d", &e); 
if (e == 0) 
{ 
int pos; 
printf("Enter position where error is to be inserted (0-based index): "); 
scanf("%d", &pos); 
if (t[pos] == '0') 
t[pos] = '1'; 
else 
t[pos] = '0'; 
printf("Erroneous Data: %s\n", t); 
}
crc(); 
for (e = 0; e < N - 1; e++) 
{ 
if (cs[e] == '1') 
{ 
printf("\nError detected!\n"); 
return 0; 
} 
} 
printf("\nNo error detected.\n"); 
return 0; 
}

``` 
# OUTPUT:
<img width="1120" height="667" alt="Screenshot 2025-10-14 114814" src="https://github.com/user-attachments/assets/2bf2fd6f-d1cc-4a6a-8d90-c13ba7f684e7" />


# RESULT:
Thus the error detection using CRC-CCITT[16 bit] technique is implemented and the output is obtained and verified successfully.
