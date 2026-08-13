---
layout: post
title: "Magic of Exponentials"
author: "Chandru Narayan"
categories: lessons
tags: [lessons]
image: ci.png
---
Albert Einstein most certainly did NOT say "Compound Interest is the most powerful force in the Universe". Still, it may be true ...

# Magic of Exponentials  
  
## 🌾 Module 1: The ancient Indian story of the Chaturanga  
## 1.1 The Legend of Chaturanga  
### In ancient India, the inventor of chess (Chaturanga) presented his game to the ruling king. As a reward, the inventor requested a seemingly trivial prize:  
* **1 grain of rice** on the first square of the board.  
* **2 grains** on the second square, **4 grains** on the third, **8 grains** on the fourth, and so on.  
* The payout must double continuously for each of the **64 squares** on the board.  
* The king immediately accepted, how much rice did the king owe to the inventer?  Can you guess at the answer? This picture should give you a clue!
![](../assets/img/chaturanga.png)

### In this session we will calculate this from first principles which will show the real nature of Exponential functions following the 10 steps below:
1. First let us draw a 4x4 chess board with 16 squares
    | | | | |
    | :---: | :---: | :---: | :---: |
    | **1** | **2** | **3** | **8** |
    | **5** | **6** | **7** | **8** |
    | **??** | **??** | **??** | **??** |
    | **??** | **??** | **??** | **??** |
    ...
1. Now, let us put the number of rice in each square

    | | | | |
    | :---: | :---: | :---: | :---: |
    | **1** | **2** | **4** | **8** |
    | **??** | **??** | **??** | **??** |
    | **??** | **??** | **??** | **??** |
    | **??** | **??** | **??** | **??** |
    ...

1. This can be modeled as a series exponential numbers as follows: 

    *[note that ${2}^0 = 1 $ or $ {(any\ number)}^0 = 1 $]*

    | | | | |
    | :---: | :---: | :---: | :---: |
    | $ 2^0 $ | $ 2^1 $ | $ 2^2 $ | $ 2^3 $ |
    | **??** | **??** | **??** | **??** |
    | **??** | **??** | **??** | **??** |
    | **??** | **??** | **??** | $ 2^{15} $ | 
    
    why are we missing $2^{16}$ above ?

1. Now, let us create a Series with 16 terms for 16 squares and sum all of the terms:
    
    $ S_{16} = 1\ +\ 2\ +\ 4\ +\ 8\ +\ 16\ +\ 32\ +\ 64\ +\ ...\ \ +\ 32,768 $

1. You can also write the 16-term series using exponentials as (hints: $2^0 = 1$ and $2^1 = 2$):
    
    $ S_{16} =\ 2^0\ +\ 2^1\ +\ 2^2\ +\ 2^3\ +\ 2^4\ +\ ...\ \ +\ 2^{14}\ +\ 2^{15} $ why are we missing the $2^{16}$ term?

1. Can you write out the full Series for a 8x8 square chessboard in powers of 2? (you will need 64 terms):

    $\textcircled{1}\;S_{64} =\ 2^0\ +\ 2^1\ +\ 2^2\ +\ 2^3\ +\ 2^4\ +\ ...\ \ +\ 2^{62}\ +\ 2^{63}$

1. Multiply equation $ \textcircled{2}$ above by $2$ on both sides of the $=$ sign:

    $ \textcircled{2}\;2*S_{64} =\ 2*2^0\ +\ 2*2^1\ +\ 2*2^2\ +\ 2*2^3\ +\ 2*2^4\ +\ ...\ \ +\ 2*2^{62}\ +\ 2*2^{63}$
    
1. Simplify equation $ \textcircled{2}$ above to get (hints: $2*2^0 = 2^{1+0} = 2^1$ and $2*2^3 = 2^{1+3} = 2^4$):

    $ \textcircled{3}\;2*S_{64} =\ 2^1\ +\ 2^2\ +\ 2^3\ +\ 2^4\ +\ 2^5\ +\ ...\ \ +\ 2^{63}\ +\ 2^{64} $

1. Subract equation $ \textcircled{1}$ from equation $\textcircled{3}$ to get $\textcircled{3}-\textcircled{1}$ as follows (shifted terms in equation $\textcircled{3}$ for lining up): 

    | | | | | | | | | | |
    | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
    |  $\textcircled{3}\,2*S_{64} \,=$ | *(shift)*$+$ |  $2^1 \,+$ |  $2^2 +$ |  $2^3 +$ |  $2^4 +$ |  $2^5+ $ |  $... $ |  $2^{63}+ $ |  $2^{64} $ |
    |  $\textcircled{1}\,S_{64} \,=$ |  $2^0 \,+$ |  $2^1 \,+$ |  $2^2 +$ |  $2^3 +$ |  $2^4 +$ |  $... $ |  $2^{62}+ $ |  $2^{63} $ |



    | | | | | | | | | | | | ||
    | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |:---: |
    |$\textcircled{4}\,S_{64}=\;\;\;\;\;\;\;$ |  $-1 +$ |||||||||| |$2^{64} $|
 
 1. Simplify equation $ \textcircled{4}$ above to get $ \textcircled{5}$ which represents the number of rice kernels in square 64 of the chess board.

    $ \textcircled{5}\;S_{64} = 2^{64} - 1 $

1. Computing that that in your calculator will give you a **HUMUNGOUS** number - 18 followed by another 18 decimals or 18.5 quntillion rice kernels!!

    **$ Total\ Amount\ of\ Rice=(2^{64}-1)=\mathbf{18,446,744,073,709,551,615}\text{\ grains}$**


### How much rice is that when compared to the entire annual rice production of India? How many years will it take to produce that much rice?

**Here is some pertinent information for you to calculate this**

````        
1. Average Weight of a Single Rice Grain ≈ 0.025 grams
1. Indian Annual Rice Production = 150 million metric tonnes
1. There are 1000 grams in a kg
1. There are 1000 kg in a metric tonne

````
