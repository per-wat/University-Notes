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

**CLassical Encryption**

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
