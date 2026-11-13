# Designing-Simulation-of-2-Bit-Multiplier-Circuit

### Why did I start with a 2-bit multiplier?

I actually designed this circuit as a stepping stone towards a 4-bit binary multiplier. Designing a 4-bit multiplier is one of my current assignments, but before jumping directly into it, I decided to start with a 2-bit multiplier.

The reason was simple: I wanted to understand how partial products are generated, how they are added, and how the complete multiplication process can be implemented using basic logic gates. I thought understanding a smaller multiplier first would make the 4-bit design easier to approach, and eventually help me move towards larger multipliers such as 8-bit ones.

So, this became my starting point.

## About the Circuit

The circuit takes two 2-bit binary inputs -

- A = A1 A0
- B = B1 B0

And produces a 4-bit product -

- P = P3 P2 P1 P0

Instead of using a predefined multiplier component, I designed it using individual logic gates and half adders in Logisim Evolution.

## Working Principle

The multiplication starts by generating four partial products using AND gates.

| Partial Product | Expression |
|:---:|:---:|
| PP0 | A0B0 |
| PP1 | A1B0 |
| PP2 | A0B1 |
| PP3 | A1B1 |

These partial products are arranged according to their binary weights.

The two middle partial products have the same weight, so they need to be added. This is where the first half adder comes in.

### First Half Adder

Inputs:
- A1B0
- A0B1

Outputs:
- Sum = P1
- Carry = C1

### Second Half Adder

Inputs:
- A1B1
- C1

Outputs:
- Sum = P2
- Carry = P3

The least significant bit P0 is directly obtained from PP0.

## Boolean Expressions

The final expressions obtained from the circuit are -

**P0 = A0B0**

**P1 = A1B0 ⊕ A0B1**

**C1 = (A1B0)(A0B1)**

**P2 = A1B1 ⊕ C1**

**P3 = (A1B1)C1**

After simplification:

**C1 = A1A0B1B0**

**P3 = A1A0B1B0**

## Boolean Expression Derivation

I explored two approaches to understand and derive the output expressions:

**1. Binary Addition / Half-Adder Approach**

Started with ordinary binary multiplication, generated the partial products and arranged them according to their weights. The addition stages helped identify where half adders were required and how their sum and carry outputs were generated.

**2. Truth Table and Karnaugh Map (K-Map) Approach**

Prepared the truth table for all 16 input combinations and used separate 4-variable K-maps for P0, P1, P2 and P3.

This helped me simplify the output functions independently and compare them with the expressions obtained through the half-adder approach.

Both approaches led to the same final output functions.

## Truth Table and Verification

Since there are four input variables, the circuit has:

2⁴ = 16 possible input combinations.

I used the Test Vector feature in Logisim Evolution to verify the circuit against all 16 combinations.

**Simulation Result:**
- Total test cases: 16
- Passed: 16
- Failed: 0

## Tools Used

- Logisim Evolution – Circuit design and simulation
- Boolean Algebra – Expression derivation
- Karnaugh Maps – Boolean simplification
- Test Vectors – Functional verification

## What Comes Next?

This 2-bit multiplier is not the final destination. It is my starting point for the original 4-bit multiplier assignment.

Before increasing the number of input bits, I wanted to become comfortable with the complete process: partial products, addition stages, Boolean expressions, K-maps, circuit implementation and verification.

The next step is to apply this understanding to a 4-bit multiplier.

---
