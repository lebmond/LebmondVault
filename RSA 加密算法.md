- Key Generation:
    - Randomly select two **large**, distinct primes p and q of the same length
    - Compute $n=pq$, and $\phi(n)=(p-1)(q-1)$ is the Euler’s Function about $n$ (i.e. the number of numbers that is co-prime with $m$).
    - Select an arbitrary $e$ such that $1<e<\phi(n)$ and $gcd(e,\phi(n))=1$
    - Compute $d=e^{-1} \text{ mod }\phi(n)$ by using Extended Euclidean Algorithm to solve:
      $$ ed\equiv1\text{ mod }\phi(n) $$
      - A’s public key: $n=pq$ (called as **RSA modulus**), and $e$, a randomly picked number (called as ********encryption exponent********).
      - A’s private key: $d$, is also called as ******************decryption exponent******************). $d$ 也被称为 n 的模反元素.
    
- Encryption To encryption a plaintext, $M$, for Alice, Bob does:
    - obtain an authentic copy of A’s public key (n, e)
    - Compute the cipher text, $C=M^e\text{ mod }n$
    - Send $C$ to Alice.
- Decryption: to decrypt Bob’s cipher text, $C$, Alice does:
    - Compute $M=C^d\text{ mod } n$
    - $M$ is the plaintext sent by Bob.
- **RSA 原理/定理:**
$$ C^d\equiv M^{ed}\equiv M\text{ mod } n $$

 Proof: Since $ed\equiv 1 \text{ mod }\phi(n)$ by deliberately choosing such a $d$, we can write $ed=1+k\phi(n)=1 + k(p-1)(q-1)\ \exists k\in\mathbb{Z}$. We now want to show that:
    
    $$ M^{k\phi(n)+1}\equiv M\text{ mod }n,\text{where }n=pq $$
    
    - Case 1: $M$ divides $p$:
        
        $p|M\text{, then }M\equiv0\text{ mod }p,\\\text{take the exponent of }ed\text{ on both sides: }M^{ed}\equiv0^{ed}\equiv0\equiv M\text{ mod }p)$
        
    - Case 2: $M$ does not divide $p$:
        
        $p\nmid M$, besides we know $p$ is a prime, thus we must have $gcd(p,M)=1$. By Euler’s Theorem, we have:
        
        $$ \begin{aligned} M ^{\phi(p)}&\equiv1\text{ mod } p\\ M ^{p-1}&\equiv1\text{ mod }p \text{ (since p is a prime, thus } \phi(p)=p-1)\\ M ^{k(p-1)(q-1)}&\equiv1^{k(q-1)}\text{ mod }p \\ M ^{k(p-1)(q-1)}&\equiv1\text{ mod }p \\ M ^{k(p-1)(q-1)+1}&\equiv1\times M\text{ mod }p \\ M ^{ed}&\equiv M\text{ mod }p\ \text{(as desired)} \end{aligned} $$
        
        The same is true for $M ^{ed}\equiv M\text{ mod }q$. Thus:
        
        $\begin{aligned} p|(M^{ed}-M),\text{ and } q|(M^{ed}-M)\\ p\ne q\text{ are relatie primes}\\ \text{thus, }pq|(M^{ed}-M) \end{aligned}$
        
        Hence, we have $M^{ed}\equiv M\text{ mod }n$ as desired.