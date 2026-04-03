# Error Analysis: Expected Value Problems (Mathematics / Probability)

**Date:** 2026-04-02
**Source:** Discord chat history
**Tags:** #Mathematics #Probability #ExpectedValue #Symmetry #LinearityOfExpectation

---

## Overview

This entry consolidates two probability mistakes from the same study session and records the underlying pattern rather than treating them as isolated slips.

### Core Pattern
The student understands the broad idea of expectation, but the errors show an unstable grasp of **structure recognition**:
- sometimes the student misses the hidden symmetry in a combinatorial setup;
- sometimes the student mis-weights place value or grouping structure.

In both cases, the fix is not “calculate harder,” but **model the random structure correctly before computing**.

---

## ❌ Problem 1: Expected Value of a 6-Digit Palindrome

**Question:** A palindrome is chosen uniformly at random from all 6-digit palindromes. What is its expected value?

**Student's Responses:**
- 550049.5
- 550055

**✅ Correct Answer:** **550000**

### 💡 In-Depth Analysis

- A 6-digit palindrome has the form \(abc|cba\).
- The first digit \(a\) is uniformly chosen from \(1,2,\dots,9\), so \(E[a]=5\).
- The middle free digits \(b,c\) are each uniformly chosen from \(0,1,\dots,9\), so \(E[b]=E[c]=4.5\).

Using place values:
\[
E = E[a](10^5+1)+E[b](10^4+10)+E[c](10^3+10^2)
\]
\[
=5(100001)+4.5(10010)+4.5(1100)
\]
\[
=500005+45045+4950=550000.
\]

### Root Cause
The student likely made a **place-value weighting slip**.
They saw the expectation idea correctly, but did not keep the mirrored digit structure aligned with the correct decimal weights.

### Key Takeaway
When a number has mirrored structure, do **not** expand digit by digit mechanically. First compress the number into independent random digits and their combined place-value weights.

### One-Line Memory Hook
**For a palindrome, pair mirrored places first, then take expectation.**

---

## ❌ Problem 2: Expected Position of the First Spade in a Shuffled Deck

**Question Context:** In a standard 52-card deck, what is the expected position of the first spade?

**Student's Wrong Answer:** **53/13**

**✅ Correct Answer:** **53/14**

### 💡 In-Depth Analysis

There are 13 spades and 39 non-spades.
A clean way to think about the problem is:
- the 13 spades divide the 39 non-spades into **14 gaps**;
- by symmetry, the expected number of non-spades before the first spade is
\[
\frac{39}{14}.
\]
So the expected position of the first spade is
\[
1 + \frac{39}{14} = \frac{53}{14}.
\]

### Root Cause
The student treated **13 spades as creating 13 intervals**, but actually **13 successes create 14 segments**.
This is a classic grouping error in symmetry-based expectation problems.

### Key Takeaway
If \(s\) success items are scattered among failures, they split the failures into **\(s+1\)** parts, not \(s\) parts.

### One-Line Memory Hook
**\(s\) successes create \(s+1\) gaps.**

---

## 📚 Consolidated Learning Points

1. **Linearity of expectation is powerful, but only after the model is correct.**
2. **Symmetry usually simplifies expected value problems more than brute-force calculation.**
3. **Watch for hidden grouping structures**:
   - mirrored digits;
   - intervals/gaps;
   - repeated weights;
   - success/failure partitions.

---

## ✅ Error Pattern Label

**Pattern:** Structural Modeling Error in Expected Value Problems

**Typical symptoms:**
- arithmetic is mostly reasonable;
- final answer is close to correct or “looks plausible”;
- the real mistake happened one step earlier, when translating the setup into a model.

---

## 🔁 Future Check Routine

Before solving the next expected value problem, ask:
1. What are the truly independent random pieces?
2. Is there symmetry I can exploit?
3. Am I counting groups / gaps / mirrored places correctly?
4. Am I weighting each piece by the correct positional or probabilistic factor?
