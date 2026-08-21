# Strategy

We want to construct a list of prime numbers below 100. To do this, we create a list we intend to populate with primes, and proceed to consider every number from the smallest prime (2) up to 100 as a candidate for being prime. If the candaidate number is prime, we can add it to the list. To check if the currently considered candidate is prime, we test to see if it is divisible by any existing prime in our list. If it is divisible by any of the existing primes, we know it is not prime and can immediately move on to the next candidate.

# Sample Solution

```py-cell
 # Create an empty list that we will populate with primes
primes = []

# Loop over candidate numbers from 2 to 100
for candidate in range(2, 101):
    # Initially, we assume the candidate is prime until we find a divisor
    not_a_prime = False
    for prime in primes:
        # Check if the candidate is divisible by any existing prime
        # If candidate is divisible by prime, candidate % prime will be 0
        if candidate % prime == 0:
            # If it is divisible, it is not a prime number
            not_a_prime = True
            # Record it is not prime, then break out of the inner loop - we don't need to check divisibility by any more primes
            break
    if not not_a_prime:
        # If we have not found any divisor, the candidate is prime and we can add it to our list
        primes.append(candidate)
    # If we found a divisor, we don't need to do anything - we just move on to the next candidate number

print(primes)
```