# The Magic of Exponentials: Growth, Decay, and Compounding
**The Meenakshi School — Applied Mathematics & Science Series**

---

## Executive Overview
This lesson explores how the exponential function $y = a \cdot b^x$ governs fundamental phenomena across the Universe—from ancient algorithmic puzzles and subatomic physics to modern finance and cosmology.

---

## 1. Classical Growth: The Wheat and Chessboard Problem (Chaturanga)
* **The Premise:** The inventor of chess requested a seemingly modest reward from the King: $1$ grain of rice on the first square, $2$ on the second, $4$ on the third, doubling on each subsequent square across the $64$-square board.
* **The Mathematics:**
  $$\text{Total Grains} = \sum_{k=0}^{63} 2^k = 2^{64} - 1 = 18,446,744,073,709,551,615$$
* **The Reality Check:** Over $18.4$ quintillion grains of rice—equivalent to nearly **3,000 years of global agricultural production**.

---

## 2. Exponential Decay: Medical Physics & Nuclear Tracers
* **The Concept:** While growth multiplies by $b > 1$, decay scales down by $0 < b < 1$. Nuclear medicine uses short-lived radioactive isotopes like **Technetium-99m ($^{99\text{m}}\text{Tc}$)** for SPECT imaging because they clear quickly from the human body.
* **The Decay Equation:**
  $$N(t) = N_0 \left(\frac{1}{2}\right)^{\frac{t}{t_{1/2}}}$$
  * $N_0$: Initial administered dose
  * $t_{1/2}$: Half-life ($6\text{ hours}$ for $^{99\text{m}}\text{Tc}$)
  * $t$: Elapsed time in hours

* **Class Exercise:**
  * *Question:* If a patient receives a dose at 8:00 AM, how much remains in the body at 8:00 AM the following day ($24\text{ hours}$ later)?
  * *Calculation:* $t / t_{1/2} = 24 / 6 = 4 \text{ half-lives}$.
  * *Result:* $\left(\frac{1}{2}\right)^4 = \frac{1}{16} = 6.25\%$ remaining.

---

## 3. Financial Compounding: The 10 Paise Doubling Effect
* **The Scenario:** Compare making a single large deposit versus doubling a tiny initial amount of $10\text{ paise}$ ($0.10\text{ ₹}$) every day for $30\text{ days}$.
* **Day 30 Single-Day Value:**
  $$\text{Value}_{\text{Day } 30} = 0.10 \times 2^{29} = 0.10 \times 536,870,912 = 53,687,091.20\text{ ₹}$$
* **Cumulative 30-Day Account Balance:**
  $$\text{Total Balance} = \sum_{k=0}^{29} (0.10 \times 2^k) = 0.10 \times (2^{30} - 1) = 107,374,182.30\text{ ₹}$$
* **Takeaway:** Over $107\text{ Million ₹}$ (or **$10.74\text{ Crores}$**) accumulated from a starting balance of just 10 paise and doubling it for 30 days!

---

## 4. Universal Comparative Summary

| Application Domain | Mathematical Model | Base Behavior ($b$) | Real-World Impact |
| :--- | :--- | :--- | :--- |
| **Ancient Algorithmic Growth** | $y = 2^x$ | $b = 2 > 1$ | Outstrips global planetary supply ($18.4\text{ quintillion}$) |
| **Nuclear Medicine (Decay)** | $y = \left(\frac{1}{2}\right)^{x/6}$ | $b = 0.5 < 1$ | Clears $93.75\%$ of tracer radiation within $24\text{ hours}$ |
| **Financial Compounding** | $y = 0.10 \cdot (2)^x$ | $b = 2 > 1$ | Converts $10\text{ paise}$ into $>10.7\text{ Crores}$ in $30\text{ days}$ |
