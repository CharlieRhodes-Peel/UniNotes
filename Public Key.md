### How it works:
1. The send encrypts a piece of information x with the public key of the recipient
2. The recipient decrypts with their private key
## PK Composition:
PU : (N, e) (public key)
PR :  (N, d) (private key)
	where: p, q = prime numbers
		   N = (p * q)
		   T = (p - 1) * (q - 1)
		   e, d = Two numbers such that: (e * d) mod T = 1
	Note: The 1 is not arbitrary! It's needed to be that way
## Sending Encryption:
Say b sending message to a:
### Steps:
##### Sending:

	EncryptedMSG = Encrypt(Message, PU_a);
EncryptedMSG also = $(Message)^e \space mod \space N$
Remember PU = (N, e)!
##### Decrypting:

	Decrypt[EncryptedMSG, PR_a] = (EncryptedMSG)^d mod N
# Diffie-Hellman
Its purpose is to enable 2 users to securely exchange a key that can then be used for subsequent symmetric encryption of messages
- Its effectiveness depends on the difficulty of computing discrete logarithms 
### Discrete Logarithm:
- Prime No. = A number q that is only divisible by 1 & q
- Primitive Root of a prime number q = a num whose 
		num^(i) mod q 
	generates integers from 1 to q- 1 (where 0 <= i <= q-1)
	- Eg. If q = 13 a primitive root of 13 is 2 as 
#### Discrete logarithm:
Given an integer b, a primative root a, and a prime bumber q, we define i as the **discrete logarithm** of b for hte base a and modulo q
	b = a^i mod q
		where 0 <= i <= q-1
### Diagrams:
![[Pasted image 20250507133157.png]]
^ this also explains the math behind it

##### Rephrasing:
(q, a)  = prime numbers in the public domain where a is primitive root of q
private key must be < q
public key = a ^ (private_key) mod q
Then each party swaps public keys
Then they reach a shared secret using their own private key
Shared Secret key = Others_publicKey ^ (our_privateKey) mod q
(Based on math these will both be the same thing for each person)
Ends up being:
Shared Secret key = a ^ (our_privateKey * Others_privateKey) mod q
if you re arrange stuff

#### Security Issues
q & a (the prime number and primitive root) are in the public domain
But what is to stop somebody just using their own private key to be a "man in the middle" and steal the information transferred?
NOTHING! That is we use [[Certificate]]s!!


