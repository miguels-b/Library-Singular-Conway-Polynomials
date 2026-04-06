# Conway Polynomials: High-Performance Implementation in Singular

This repository contains `conway.lib`, a specialized library for the **Singular** computer algebra system. Developed as part of my Bachelor's Thesis in Mathematics at the **University of Valladolid**, this project provides a robust framework for calculating Conway polynomials across various finite field characteristics.

## Project Overview
Conway polynomials $C_{p,n}$ provide a canonical choice of irreducible polynomials to represent each finite field $\mathbb{F}_{p^{n}}$, guaranteeing seamless compatibility between field extensions. This standardization is critical for interoperability between major computer algebra systems such as GAP, Magma, and Singular.

Computing these polynomials is a high-cost computational problem. This implementation leverages the **Heath-Loehr algorithm (2004)** and introduces original optimizations to extend calculations to degrees previously considered unreachable on standard hardware.

## Key Technical Achievements
* **Discovery of New Polynomials**: Successfully calculated **eight previously unrecorded Conway polynomials** for Mersenne exponents: 521, 607, 1279, 2203, 2281, 3217, 4253, and 4423. Also we calculated **one hundred and four more previously unrecorded Conway polynomials** with p>200 and n=11,13,17,19,23.
* **Advanced Algorithmic Implementation**:
    * **Ben-Or Irreducibility Test**: Integrated a highly efficient test that avoids full factorization, enabling the verification of high-degree candidates in $O(n^3)$ time.
    * **Lexicographical Pruning**: Implemented "Parker order" pruning to abort sub-optimal candidate calculations immediately, significantly reducing total execution time.
    * **Mersenne Prime Optimization**: Developed a specialized path for Mersenne exponents that bypasses expensive primitivity tests, allowing calculations up to degree 4423.
    * **Hybrid Computation Model**: The library automatically switches between the Heath-Loehr algorithm for composite degrees and optimized exhaustive searches for prime degrees based on the compatibility parameter $g$.
* **System Integration**: Utilizes Singular’s efficient binary representation and modular arithmetic, coupled with external Linux-based factorization tools for maximum performance.

## Research & Impact
By reducing the search space by factors exceeding **$10^{13}$** for certain composite degrees (e.g., $n=60$), this library demonstrates how mathematical theory can be applied to solve "NP-hard" style bottlenecks in computational algebra.

---

# Conway Polynomials Database

This repository contains a collection of 112 unregistered **Conway Polynomials** $C_{p,n}$, which are used to define standard extensions of finite fields $GF(p^n)$. These polynomials are essential for ensuring compatibility between different computer algebra systems.

---

## 1. Characteristic 2 ($p=2$)
Standard Conway polynomials for binary fields, often used in cryptography (e.g., AES, ECC).

| Degree ($n$) | Approx. Primitive Elements | Conway Polynomial $C_{2,n}(x)$ |
| :--- | :--- | :--- |
| **521** | $\sim 6.9 \times 10^{156}$ | $x^{521} + x^9 + x^6 + x^5 + x^3 + x + 1$ |
| **607** | $\sim 5.3 \times 10^{182}$ | $x^{607} + x^9 + x^7 + x^6 + x^4 + x + 1$ |
| **1279** | $\sim 1.0 \times 10^{385}$ | $x^{1279} + x^{11} + x^9 + x^8 + x^5 + x^3 + x^2 + x + 1$ |
| **2203** | $\sim 1.5 \times 10^{663}$ | $x^{2203} + x^{11} + x^{10} + x^6 + x^4 + x + 1$ |
| **2281** | $\sim 4.5 \times 10^{686}$ | $x^{2281} + x^9 + x^8 + x^7 + x^6 + x^2 + 1$ |
| **3217** | $\sim 2.6 \times 10^{969}$ | $x^{3217} + x^{11} + x^{10} + x^9 + x^8 + x^6 + x^5 + x^4 + x^3 + x^2 + 1$ |
| **4253** | $\sim 4.5 \times 10^{1281}$ | $x^{4253} + x^{12} + x^{10} + x^7 + x^5 + x^4 + 1$ |
| **4423** | $\sim 2.8 \times 10^{1332}$ | $x^{4423} + x^{14} + x^{12} + x^{10} + x^9 + x^5 + x + 1$ |

---

## 2. Higher Characteristics ($p > 2$)
Conway polynomials for various prime characteristics $p$ and degrees $n$.

| $p$ | $n=11$ | $n=13$ | $n=17$ | $n=19$ | $n=23$ |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **263** | - | $x^{13} + 6x - 5$ | $x^{17} + x - 5$ | $x^{19} + 10x - 5$ | $x^{23} + 8x - 5$ |
| **269** | - | $x^{13} + 31x - 2$ | $x^{17} + 12x - 2$ | $x^{19} + 30x - 2$ | $x^{23} + 45x - 2$ |
| **271** | - | $x^{13} + 4x - 6$ | $x^{17} + 14x - 6$ | $x^{19} + 19x - 6$ | $x^{23} + 7x - 6$ |
| **277** | - | $x^{13} + 20x - 5$ | $x^{17} + 31x - 5$ | $x^{19} + 26x - 5$ | $x^{23} - x^2 + x - 5$ |
| **281** | - | $x^{13} + x - 3$ | $x^{17} + 11x - 3$ | $x^{19} + 14x - 3$ | $x^{23} + 94x - 3$ |
| **283** | - | $x^{13} + 4x - 3$ | $x^{17} + 29x - 3$ | $x^{19} + 4x - 3$ | $x^{23} + 25x - 3$ |
| **293** | - | $x^{13} + 2x - 2$ | $x^{17} + 43x - 2$ | $x^{19} + 2x - 2$ | $x^{23} + 60x - 2$ |
| **307** | $x^{11} + 5x - 5$ | $x^{13} + 3x - 5$ | $x^{17} - x^2 + x - 5$ | $x^{19} + 19x - 5$ | $x^{23} + 42x - 5$ |
| **311** | $x^{11} + 8x - 17$ | $x^{13} + 14x - 17$ | $x^{17} + 14x - 17$ | $x^{19} + 4x - 17$ | $x^{23} + 29x - 17$ |
| **313** | $x^{11} + 5x - 10$ | $x^{13} + 7x - 10$ | $x^{17} + 34x - 10$ | $x^{19} + 17x - 10$ | $x^{23} + 38x - 10$ |
| **317** | $x^{11} + 8x - 2$ | $x^{13} + 4x - 2$ | $x^{17} + 11x - 2$ | $x^{19} + 8x - 2$ | - |
| **331** | $x^{11} + 73x - 3$ | $x^{13} + 3x - 3$ | $x^{17} + 33x - 3$ | $x^{19} + 10x - 3$ | $x^{23} + 13x - 3$ |
| **337** | $x^{11} + 8x - 10$ | $x^{13} + 5x - 10$ | $x^{17} + 13x - 10$ | $x^{19} + 17x - 10$ | $x^{23} + 46x - 10$ |
| **347** | $x^{11} + 25x - 2$ | $x^{13} + 11x - 2$ | $x^{17} + 20x - 2$ | $x^{19} + 7x - 2$ | $x^{23} + 36x - 2$ |
| **349** | $x^{11} + 42x - 2$ | $x^{13} + 13x - 2$ | $x^{17} + 8x - 2$ | $x^{19} + 7x - 2$ | $x^{23} + 16x - 2$ |
| **353** | $x^{11} + 13x - 3$ | $x^{13} + 22x - 3$ | $x^{17} + 16x - 3$ | $x^{19} + 5x - 3$ | - |
| **359** | $x^{11} + 27x - 7$ | $x^{13} + 4x - 7$ | $x^{17} + 22x - 7$ | - | $x^{23} + 35x - 7$ |
| **367** | $x^{11} + 27x - 6$ | $x^{13} + 6x - 6$ | $x^{17} + 11x - 6$ | $x^{19} + 43x - 6$ | $x^{23} + 26x - 6$ |
| **373** | $x^{11} + 4x - 2$ | $x^{13} + 15x - 2$ | $x^{17} + 17x - 2$ | $x^{19} + 18x - 2$ | $x^{23} + 13x - 2$ |
| **379** | $x^{11} + 6x - 2$ | $x^{13} + 8x - 2$ | $x^{17} + 8x - 2$ | $x^{19} + 26x - 2$ | $x^{23} + 7x - 2$ |
| **383** | $x^{11} + 17x - 5$ | $x^{13} + x - 5$ | $x^{17} + 13x - 5$ | $x^{19} + 25x - 5$ | $x^{23} + 7x - 5$ |
| **389** | $x^{11} + 4x - 2$ | $x^{13} + 13x - 2$ | $x^{17} + 44x - 2$ | $x^{19} + 14x - 2$ | - |
| **397** | $x^{11} + 12x - 5$ | $x^{13} + x - 5$ | $x^{17} + 19x - 5$ | $x^{19} + 33x - 5$ | $x^{23} + 7x - 5$ |
