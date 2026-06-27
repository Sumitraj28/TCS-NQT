# Number System — Formulas and Rules

## 1. HCF and LCM Relation
For any two positive integers $a$ and $b$:
$$\text{HCF}(a, b) \times \text{LCM}(a, b) = a \times b$$

---

## 2. HCF and LCM of Fractions
$$\text{HCF of Fractions} = \frac{\text{HCF of Numerators}}{\text{LCM of Denominators}}$$

$$\text{LCM of Fractions} = \frac{\text{LCM of Numerators}}{\text{HCF of Denominators}}$$

---

## 3. Factors Formulas
If prime factorization is $N = p_1^{a_1} \times p_2^{a_2} \times \dots$:
- **Total Factors Count:** $F(N) = (a_1 + 1)(a_2 + 1)\dots$
- **Sum of Factors:** $S(N) = \frac{p_1^{a_1+1}-1}{p_1-1} \times \frac{p_2^{a_2+1}-1}{p_2-1} \dots$
- **Product of Factors:** $P(N) = N^{F(N)/2}$
- **Number of ways to write N as product of two coprime numbers:** $2^{k-1}$ where $k$ is count of distinct prime factors.

---

## 4. Trailing Zeros in $N!$ (Legendre's Formula)
$$\text{Trailing Zeros} = \sum_{k=1}^{\infty} \lfloor \frac{N}{5^k} \rfloor = \lfloor \frac{N}{5} \rfloor + \lfloor \frac{N}{25} \rfloor + \lfloor \frac{N}{125} \rfloor + \dots$$
