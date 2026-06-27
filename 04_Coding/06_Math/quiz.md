# Math — Quiz

## Rapid-Fire Q&A
1. **What is the time complexity of the standard Euclidean algorithm for GCD?**
   - **Answer:** $O(\log(\min(a, b)))$.
2. **How to calculate LCM from GCD?**
   - **Answer:** $\text{LCM}(a, b) = \frac{a \times b}{\text{GCD}(a, b)}$.
3. **What is the digital root of 987?**
   - **Answer:** $9 + 8 + 7 = 24 \rightarrow 2 + 4 = 6$.
4. **Is 1 considered a prime number?**
   - **Answer:** No, prime numbers must be strictly greater than 1.
5. **How many prime factors can a composite number $N$ have at most that are greater than $\sqrt{N}$?**
   - **Answer:** At most 1.
6. **What is the number of trailing zeros in $100!$?**
   - **Answer:** $\lfloor 100/5 \rfloor + \lfloor 100/25 \rfloor = 20 + 4 = 24$.
7. **Is 28 a perfect number?**
   - **Answer:** Yes ($1 + 2 + 4 + 7 + 14 = 28$).
8. **What bitwise check checks if $N$ is odd?**
   - **Answer:** `(n & 1) != 0`.
9. **How many digits does $N$ have?**
   - **Answer:** $\lfloor \log_{10} N \rfloor + 1$.
10. **What is the complexity of binary exponentiation?**
    - **Answer:** $O(\log N)$.

## True or False
1. **The Sieve of Eratosthenes algorithm has a time complexity of $O(N \log N)$.**
   - **Answer:** False (It is $O(N \log \log N)$).
2. **Every Armstrong number must be a 3-digit number.**
   - **Answer:** False (e.g. 1634 is a 4-digit Armstrong number).
3. **The modulo operator `%` in C++ returns positive values even for negative numerators.**
   - **Answer:** False (e.g. `-5 % 3` returns `-2`).
4. **If $(n \& (n - 1)) == 0$ is true for $n > 0$, then $n$ is a power of 2.**
   - **Answer:** True.
5. **The sum of the first $n$ odd natural numbers is $n^2$.**
   - **Answer:** True.
