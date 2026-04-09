## What is RSA? 
Rivest Shamir Adleman's Algorithm is an asymmetric cryptographic algorithm. It's asymmetric in the sense that it works with a public key used for encryption and is known to everyone and a private key with is known only be the receiver for decryption. Ron Rivest publishes the algo in 1977. 

## Algorithm's structure 
It consists of factorisation of large numbers and modular arithmetic. 
The process uses three main stages for encryption and decryption 

## 1. Key generation 
- Choose two large prime numbers that are kept secret 
- Then produce the product of the two large primes = n
- Calculate the Euler Totient Function of the product = Φ(n)
- Make sure that the Φ(n) is larger than e and that the highest common factor of e and Φ(n)) should be 1. This is for the encryption key. 
- For decryption, the decryption exponent multiplied by e should be equal to 1 mod Φ(n). Where d is a modular multiplicative inverse of e mod Φ(n). To calculate this you can use Fermat's little theorem: a^(p-1) = 1 mod (p) where p is a prime int and a is an int that is not a multiple of p 
	- Note multiple values can be produced with (d * e) ≡ 1 mod Φ(n) but it does not matter which value you choose 
- Finally to define both keys 
	- Public key: (n, e) 
	- Private key: (n, d)
## 2. Encryption 
After converting a message to ASCII, use the public key to encrypt the cypher text with the formula: C = M^e mod n where C is the cipher text and e and n are the parts of the public key 

## 3. Decryption 
To get the original message M you must use the cipher text C and the private key to get M using the formula: M = C^d mod n where M is the message and d and n are parts of the private key. 

## Security and legitimacy 
While the only thing you would need to get the private key is d, and we know that (d * e) ≡ 1 mod Φ(n), so if we can calculate the value of Φ(n) then we can find d. But Φ(n) = (p - 1) * (q -1). So we need the value of p and q and since the the value of n = p * q this makes it seem east to find as n is already known as it's sat in the public key. However remember that p and q are supposed to be very large and in turn makes the value of n extremely large, so much so that factorising such a large number is computationally impossible. 