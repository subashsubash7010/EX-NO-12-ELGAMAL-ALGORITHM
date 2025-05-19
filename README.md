# EX-NO-12-ELGAMAL-ALGORITHM
## DATE: 19.05.2025
## NAME: SUBASH M
## REG NO: 212224220109
## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
def mod_exp(base, exp, mod):
    result = 1
    base = base % mod
    while exp > 0:
        if exp % 2 == 1:
            result = (result * base) % mod
        base = (base * base) % mod
        exp //= 2
    return result

def main():
    # Input prime number and generator
    p = int(input("Enter a large prime number (p): "))
    g = int(input("Enter a generator (g): "))

    # Input Alice's private key and compute public key
    private_key_a = int(input("Enter Alice's private key: "))
    public_key_a = mod_exp(g, private_key_a, p)
    print(f"Alice's public key: {public_key_a}")

    # Input message and random number k
    message = int(input("Enter the message to encrypt (as a number): "))
    k = int(input("Enter a random number k: "))

    # ElGamal Encryption
    c1 = mod_exp(g, k, p)
    c2 = (message * mod_exp(public_key_a, k, p)) % p
    print(f"Encrypted message (c1, c2): ({c1}, {c2})")

    # ElGamal Decryption
    decrypted_message = (c2 * mod_exp(c1, p - 1 - private_key_a, p)) % p
    print(f"Decrypted message: {decrypted_message}")

if __name__ == "__main__":
    main()

```

## Output:
![image](https://github.com/user-attachments/assets/7e76e24a-f8e4-4599-a07b-2ca02223ff0e)


## Result:
The program is executed successfully.
