# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```python
#include <stdio.h>
#include <math.h>

// Power function to return (a^b) mod P using modular exponentiation
long long int power(long long int a, long long int b, long long int P)
{
    long long int result = 1;
    a = a % P; // Reduce 'a' first

    while (b > 0)
    {
        if (b % 2 == 1) // If b is odd, multiply result with a
            result = (result * a) % P;

        b = b / 2;
        a = (a * a) % P; // Square 'a'
    }

    return result;
}

int main()
{
    long long int P, G, x, a, y, b, ka, kb;

    printf("\n***** Diffie-Hellman Key Exchange Algorithm *****\n\n");

    printf("Enter the value of P (a prime number): ");
    scanf("%lld", &P);

    printf("Enter the value of G (a primitive root of P): ");
    scanf("%lld", &G);

    // Alice chooses private key 'a'
    a = 4;
    printf("\nPrivate key a for Alice: %lld\n", a);
    x = power(G, a, P); // Public key for Alice
    printf("Public key x (for Alice): %lld\n", x);

    // Bob chooses private key 'b'
    b = 3;
    printf("\nPrivate key b for Bob: %lld\n", b);
    y = power(G, b, P); // Public key for Bob
    printf("Public key y (for Bob): %lld\n\n", y);

    // Generate the shared secret keys
    ka = power(y, a, P); // Secret key for Alice
    kb = power(x, b, P); // Secret key for Bob

    printf("Secret key for Alice: %lld\n", ka);
    printf("Secret key for Bob: %lld\n", kb);

    return 0;
}
```

## Output:

<img width="1631" height="884" alt="image" src="https://github.com/user-attachments/assets/405d8638-4278-4a7b-8310-712913caeebb" />


## Result:
  The program is executed successfully

