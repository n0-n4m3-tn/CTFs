# Writeup: Forgotten Exponent Challenge

## Challenge Overview

In this challenge, you are given an RSA public key `(n, e)` and a ciphertext `c`. The flag was encrypted under this public key. Normally, you would need the private key exponent `d` to decrypt and recover the flag.

However, this RSA key was generated with a **small private exponent `d`**, which is considered a cryptographic weakness. Wiener's attack exploits this weakness to efficiently recover `d` from the public key.

---

## What is the Vulnerability?

RSA security relies on the difficulty of factoring `n = p * q` and on keeping the private exponent `d` secret.

* Normally, `d` is large and randomly chosen.
* If `d` is too small, **Wiener's attack** can find `d` from the public exponent `e` and modulus `n`.

Wiener's attack uses the fact that `d` is the denominator of a convergent in the continued fraction expansion of `e/n`. By analyzing these convergents, it recovers `d` efficiently without factoring `n`.

---

## Given Data

You receive three values:

* `n`: RSA modulus (product of two primes)
* `e`: RSA public exponent
* `c`: ciphertext (encrypted flag)

---

## Goal

Recover the private exponent `d` using Wiener's attack, then decrypt the ciphertext `c` to get the original flag message.

---

## Step-by-step Solution

### 1. Understand the RSA setup

* Public key: `(n, e)`
* Private key exponent: `d` such that `e * d ≡ 1 mod φ(n)`, where `φ(n) = (p-1)(q-1)`
* Ciphertext: `c = m^e mod n`, where `m` is the message (flag)

---

### 2. Use continued fractions to approximate `e/n`

* Compute the continued fraction expansion of `e/n`.
* Generate convergents `(k/d)` from this expansion.
* Each convergent is a candidate for `(k, d)` satisfying `e*d - k*φ = 1`.

---

### 3. Test candidates for private exponent `d`

For each candidate `(k, d)`:

* Check if `(e*d - 1) % k == 0`
* Compute `phi = (e*d - 1) / k`
* Solve the quadratic equation to find the primes `p` and `q`:

  $$
  x^2 - (n - \phi + 1) x + n = 0
  $$
* If the roots `x1` and `x2` are integers and multiply to `n`, we found the correct `d`.

---

### 4. Decrypt the ciphertext

Once `d` is recovered:

$$
m = c^d \mod n
$$

Convert `m` back to bytes to get the original flag.

---

## Python Script

```python
from Crypto.Util.number import long_to_bytes
import math

def continued_fraction(n, d):
    cf = []
    while d:
        cf.append(n // d)
        n, d = d, n % d
    return cf

def convergents(cf):
    convergents = []
    for i in range(len(cf)):
        numerator, denominator = 1, 0
        for x in cf[:i+1][::-1]:
            numerator, denominator = denominator + numerator * x, numerator
        convergents.append((numerator, denominator))
    return convergents

def wiener_attack(e, n):
    cf = continued_fraction(e, n)
    convs = convergents(cf)
    for k, d in convs:
        if k == 0:
            continue
        if (e * d - 1) % k == 0:
            phi = (e * d - 1) // k
            a = 1
            b = -(n - phi + 1)
            c = n
            discr = b*b - 4*a*c
            if discr >= 0:
                sqrt_discr = int(math.isqrt(discr))
                if sqrt_discr*sqrt_discr == discr:
                    x1 = (-b + sqrt_discr) // (2*a)
                    x2 = (-b - sqrt_discr) // (2*a)
                    if x1 * x2 == n:
                        return d
    return None

# Given values from challenge
n = 63850702771419606335924468754030219126608381612094808433287297744070399616013646245610552417474889698799209920331395191365041795616125368134230016395988706165914235167814682286750468195047462322317432625457289046268485871972041159171306041280621867724572895930105088006356272074527538441540328786595524776801
e = 55043709285706557186141783408646740626386535872495524511454567020750344496563488142767717601271456636895870620975340682211242927255280489770887945168955767319649744476226127711544911386689920713967734860745382889754159271220451920028933518335201011047121236533990496538749328848516607011933376215688398689269
c = 32959574516500955341758575252926933493600440411343359209211464767587204645268116962598114932344916140901169768951824689492596427532141968703809321372727871350633531248886256816867966397979768514099207909579270064966212493369351630871530554443251303816924229929477222108148100192695976020307356001147109536296

d = wiener_attack(e, n)
if d is not None:
    m = pow(c, d, n)
    flag = long_to_bytes(m)
    print(f"Recovered flag: {flag.decode()}")
else:
    print("Failed to recover private exponent d.")
```

---

## Outcome

When you run the above script, it will successfully recover the private key `d` and decrypt the ciphertext `c` to reveal the flag in the format:

```
flag{rsa_small_d_recovery}
```

---

## Conclusion

This challenge demonstrated the danger of choosing a small private exponent `d` in RSA. Wiener's attack exploits this to recover the private key without factoring the modulus.

Always ensure `d` is large enough to avoid such vulnerabilities.

---
