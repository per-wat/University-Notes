# This one is for Cryptography

### 17<sup>th</sup> March 2022

> **Definition**
> Unconditional Security
> : One Time Pad, no matter how much resources and time you have now and in the future, it will never be broken
> : Even if you have the resources, you still cannot decrypt it since it produce lots of plaintext
>
> Computational Security
> : Right now maybe cannot but in the future it have a chance it will be broken
>

In cryptography we have, symetric, asymetric.
Symetric
: Sender receiver have same one same key

***

**Classical Encryption**

Example of symetric is *Substitution Cipher* or called **Caesar Cipher**
- We shifting the letter based on the key which is the shift number
- example A -> shift 3 -> D
- to solve it we can just brute force shift it one by one
- Dr. Imad just brain boozled his students with simple Caesar Cipher question

*Simple Substitution* or **Monoalphabetic Cipher**
- each character maps to other one explicit letter
- complete random and jumble
- key is 26 letters long
- in every natural language, we have redundancy, where certain letter is higher usage than others

***

### 22<sup>nd</sup> March 2022

To combat the problem, they introduced **Playfair**  
- They substitute by pair
- They uses matrix as key; a 5x5 matrix
- How do they contruct the matrix:
  - It started with keyword, it can be a word, a sentence, a paragraph, write it down
  - If there any character repeated, filter it out, only take the 1st apparance of the character
  - We consider I/J as a single letter, since we want only 25(5x5 matrix) but we have 26 alphabets
    - Since I is a reasonable frequence letter, j is a low frequency letter, it chosen to combine as 1
  - So to do it better, we wrote down the whole alphabet first, then we cross the one appared in the keyword
  - After fill in the key matrix with the filtered keyword, we fill in the rest of the alphabet in order
- How to encrpyt:
  - Encrypt 2 letters at a time
    - If a pair is repeated letter, inset filler like 'X'; "balloon" "ba lx lo on"
    - 3 scenarios can be seen:
      - If the 2 characters is on the same row, take the character to the right of it,
      - If the 2 characters is on the same column, take the character below of it,
      - If the 2 characters on different row n column, imagine a rectangle be drawn on the matrix
      - the 2 characters is the corner of the rectangle, the other corresponding is the cypher(left or right of the plaintext)
- How to decrypt:
  - Decrypt 2 letter at a time
    - 3 scenarios can be seen:
      - If same row, take to the to the left
      - If same column, take the upper
      - If different row and column, same method with encrypt
- The frequency of repeating letter is since it could be difference
- But the repetion of same plaintext is still there
  - with condition the sequence of the pair is the same

***

### 29<sup>th</sup> March 2022

**Polyalphabet**

We have a set of alphabets, for example 3, then we will have 3 different arrangment of alphabets  
Does repition work?
- Yes, it still work with the case of it is in the same key arrangement
- For example the falls, in 1,2,3 thus if the repeated word comes in the same position under the 1st one

***

### 31 <sup>st</sup> March 2022

**Polyalphabet**

Frequency
 : Counting how many times an alphabet is appearing

Kasiski Method
 : **Guess** the size of the key
 : By calculating the distance of repeated character in cyphertext (eg. 13, 64, 228)
 : Repition only occur when it falls under the same key
 : If we have multiple repition, we get the same multiple of the key
 : The distance is the multiple of the key
 : So to find it we just factorise with prime factor
 : Then get the greatest common divisor, thus it's the guess of size of the key
 : Then we write down the cyphertext, according to the size
 : ZHQ
 : LKU
 : IOP
 : Example size of 3, then we just need to find like normal substitution

**Vigenere Cypher**
- The simplest polyalphabet, we use **Vigenere Table**
- where it list out every possible shift in **Caesar Cypher**
- We repeat the key onto the plaintext
- using the table, the row is the key, column is the plaintext, content is the cyphertext

**Different of Vigenere and Poly**
- Vigenere is all shift, but Poly is monoalphabet thus Poly is more complex

- Based on 26<sup>9</sup> assumption, that we have the exact, we actually can solve decipher the whole ciphertext

**Autokey Cipher**
- We only use key once, after that we use plaintext as the key

***

### 7<sup>th</sup> April 2022

**Transposition Cipher**

- The another classification of cryptography is **Transposition**
- This is still symetric 
- We rearrange the letter not replacing them
- Thus if we do frequency test, we will get the same result with the plaintext frequency test

**Row Transposition**

- Decide on the key, either word or permutation; eg 7, this will be the column
- Then 1st person will write the plaintext in the rows
- Extract the plaintext based on which column agreed to extracted first
- Then send to 2nd person
- Count the lenght of ciphertext and divide with column number
- Then we seperate into groups with the result from before
- When we have the groups, we arrange them based on the agreed permutation
- After that we extract them out again

**QnA**

- Can we use incomplete frame
  - Yes, we can, the decrypter can just divide, then the remainder will be the number of column that is empty
  - Since we know the permutation, we will know which group will have less letter
- Which one is better in term of complexity
  - The incomplete one since the attacker don't have the permutation, they will have a hard time to know which one has less letters
- Few rules of encryption
  - Don't use same key more than once
  - Break plain text into pieces

***

### 21<sup>st</sup> April 2022

**One Time Pad**

- Problem with classical cryptography, we can get information from it even a bit.
- Have 3 characteristics
  - Key is purely random
    - Means that it cannot be repeated the output
    - example coin toss
    - Need to record to make sure receiver get the same key
  - Key is as long as the plaintext mmessage
    - The key will not be repeated
  - Key should be use only once
    - No any other message ecnrypted using the same key
- This leads to no indication either if it's correct or not
- Why people don't use one time pad?
  - If you find a way to send the key securely, might as well send the message the same way
- **Stream Cipher** is derived from One Time Pad
  - There's only no pure random in Stream Cipher

***

### 12<sup>th</sup> May 2022

**DES**

**MEMORIZE DEFINITION**

Confusion
: Removing the relation between the key and the cipher / obscured
: One of the example is substituition

Diffusion
: If you change 1 bit from the plain, it will affect many bits from the cipher
: One of the example is permutation

**What is DES?**

- Input is 64, and the output is 64, but the key is 56bit
- DES will do **16 operations** onto 1 block of input
- Those operations are the confusion and diffusion

**The Operation**

- Plaintext will go into *permutation*
- then will be splitted into 2 L0, R0
- R0 will go directly into the next L1
- L0 will b XOR with the output of the *f function* and will be the next R1
- The inputs of the *f function* are the R0 and the key from the transformation
- After going through the 16 rounds, it will end with *Final Permutation* (inverse of initial permutation)

**The F Function**

1. Expansion E
- The initial input is 32 bits
- Since we want to do XOR with the key we need 48 bits
- Thus, we will expand to 48
- Some of the bits will be repeated 
2. XOR with round key
- XOR 48bits of key with the Expansion output
3. S-box Substituition
- A table of 4 x 16
- They have special design
- The input 48 bits will be splitted into 8, leave 6 bits as inputs
- The 1st and last bit is the row indcator, the 4 bits in the middle are the column indicator
4. Permutation

**Key Generation**

- The initial key input is 64 bits or 8 bytes
- The last bit in each bytes is excluded (parity bit)
- Then we left with 56 bits
- We will split into half
- In rounds **i = 1,2,9,16** the key are rotated to the left by **one bit**
- In other rounds, the key are rotated to the left by **two bits**
- Then that will be that key round
- This process will be repeated for 16 rounds

***

### 17<sup>th</sup> May 2022

**AES**

- *National Institute of Standard and Technology* (NIST)announced a competition in 1997
- The requirements are
  - Block chipher with **128-bit block size**
  - **3 supported key lenght** 128,192,256
  - **Efficient** in software and hardware
- 15 candidates accepted in 1998
- 5 finalists announced in 1999
  - Mars - IBM Corporation
  - RC6 - RSA Lab
  - Rjindael - J. Daemen & V. Rijmen
  - Serpent - Eli BIham et al.
  - Twofish - B. Schneier et al.
- October 2000, Rjindael was chosen with the AES
- Become federal standard in November 2001

**Overview**

- Input and output are **128 bits**
- Key length - rounds
  - 128 - 10
  - 192 - 12
  - 256 - 14

**Internal Structure of AES**

- AES are byte-oriented
- 128 bits are arranged into 16 bytes of 4x4 matrix **column wise**
- Will go through **Byte Substitution**, **Shift rows**, **Mix Column**, **Key Addition**
- In the last round, Mix Column is **omitted**

**Byte Substitution Layer**

- Consist 16 **S-Boxes** that are *identical*
- unique S-Box
- uses lookup table

**Diffusion Layer**

- Consist of 2 sublayers
  - ShiftRows Sublayer
    - Permutation of data on byte level
    - Based on the input matrix, it will be shifted
    - 1st row: no shift
    - 2nd row: shift left by 1
    - 3rd row: shift left by 2
    - 4th row: shift left by 3
  - MixColumn Sublayer
    - Matrix operation which combines blocks of 4 bytes
    - Each 4-byte column will be taken and multiplied with fixed 4x4 matrix

**Key Addition Layer**

- Inputs are 16-byte matrix and 16-byte subkey
- Output are the XOR

**Key Schedule**

- Each round has 1 subkey, plus 1 subkey at the begining
- Thus total of subkey is plus 1 of rounds
- There are different key schedules???
- Example for 128-bits or 16-bytes
  - Will be divided into word (each word consist 32-bits or 4-bytes)
  - First subkey W[0] ... W[3] is the original AES key
  - Then W[0] will be XOR with W[3] that gone through *g-fx* and become the next W[0] (W[4])
  - W[1] will be XOR with the output above from W[0] to become the next W[1] (W[5])
  - and the rest is like mentioned above
  - Ask more about the *g-fx* 

**Decryption**

- AES is not based on *Feistel Network* like DES
- Thus all layers need to inverted
- Inv MixColumn Layer
  - Inverse of the 4x4 matrix that is used to multipled
- Inv ShiftRows Layer
  - Instead of shifting left, it will **shift right**
- Inv S-Box
  - Just a built inverse S-Box, no need to memorize

***

### 19<sup>th</sup> May 2022



***
