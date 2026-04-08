Public/private key pairs. We start with a private key and then derive the
public key from it.

## RSA
1. Pick two large primes
2. Multiply them to get `n`
3. Public key is `n` and a public exponent `e` (usually 65537)
4. Private key is `n` and `d` which has the property of `e × d ≡ 1 (mod φ(n))`.

### Why it works
Euler's theorem: `a^φ(n) ≡ 1 (mod n)` if `a` and `n` are coprime positive
integers. From this... something....

#### Euler's theorem Proof
If we multiply all of the coprimes with `n` up to `n` (`φ(n)`) by `a` then if we
modulo all of those numbers by `n`, we end up with the same set of numbers in a
different order.
```
# From Claude
Let's use a small example. Take n = 15, a = 2.
Coprimes of 15 (less than 15): {1, 2, 4, 7, 8, 11, 13, 14}
Multiply each by 2, mod 15:

1×2 = 2
2×2 = 4
4×2 = 8
7×2 = 14
8×2 = 16 → 1 (mod 15)
11×2 = 22 → 7 (mod 15)
13×2 = 26 → 11 (mod 15)
14×2 = 28 → 13 (mod 15)

Result: {2, 4, 8, 14, 1, 7, 11, 13}
```
If we multiply the numbers together in both sets they are equal:
```
((1 × 2) mod 15) × ((2 × 2) mod 15) × ... = 2 × 4 × ...
```
Given the rule that:
```
(a mod n) × (b mod n) ≡ a × b (mod n)
```
Noting that we are now stating an identity where the `≡ (mod n)` means both
sides are `mod n`.
```
((1 × 2) × (2 × 2) × ...) ≡ 2 × 4 × ... (mod n)
((a × c1) × (a × c2) × ...) ≡ P (mod n)
a^φ(n) × P ≡ P (mod n)
a^φ(n) ≡ 1 (mod n)
```
