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
