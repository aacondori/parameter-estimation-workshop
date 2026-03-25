# Day 2: Mathematical Modeling and Parameter Estimation

**Theme:** *From Data to Model Parameters*

---

## Overview

Day 2 transforms students from data collectors into model builders. They learn the mathematics behind Newton's Law of Cooling, implement an algorithm to find the values that make the model match their data, and check whether the results make physical sense.

---

## Learning Outcomes

### Core Skills
- **Model interpretation:** Understand what the exponential model means and what each value represents or controls
- **Forward vs. inverse problems:** Distinguish between using a fixed model to predict data and using data to determine the best model
- **Profiling technique:** Use a clever trick to simplify the search for best-fit values
- **Model validation:** Check if results make physical sense, not just statistical sense

### Mathematical Concepts
- Exponential solution: $u(t) = A + (u_0 - A)e^{-kt}$
- Differential equations: $\frac{du}{dt} = k(A - u)$
- Logarithmic transformation for linearization
- Parameter meanings: $A$ (ambient temperature), $k$ (rate), $u_0$ (initial temperature)

### Technical Skills
- Define and evaluate Julia functions
- Linear regression implementation
- Optimization landscape visualization
- Model-data overlay plots

---

## Schedule

### Morning Session (9:00 AM - 12:00 PM)

| Time Slot | Activity | Description |
|------|----------|-------------|
| 9:00-9:15 | Homework Debrief | Share insights from forward problems exploration |
| 9:15-10:30 | Exponential Model | Parameter meanings, verification, Pluto demo |
| 10:30-10:45 | *Break* | |
| 10:45-11:45 | Forward vs. Inverse | Define problem types, explore difficulty of inverse problems |
| 11:45-12:00 | Three-Point Problem | Formulate specific estimation problem |
| 12:00-1:00 | *Lunch* | Provided—refuel before coding! |

**Key Concepts:**
- **Forward problem:** Given $A$, $k$, $u_0$ → compute $u(t)$
- **Inverse problem:** Given measurements → estimate $A$, $k$
- **Why inverse is harder:** No simple formula, small errors in data cause big changes in answers, multiple "close enough" solutions

### Afternoon Session (1:00 PM - 5:00 PM)

| Time Slot | Activity | Description |
|------|----------|-------------|
| 1:00-2:15 | Profiling Technique | How the algorithm works, live demo |
| 2:15-2:30 | *Break* | |
| 2:30-3:30 | Implementation | Code the algorithm in pairs (VS Code) |
| 3:30-4:00 | Analyzing Results | Compare fits across materials, discuss what you found |
| 4:00-4:15 | *Break* | |
| 4:15-5:00 | Model Validation | Does it fit? Does it make sense? |

**Key Activity:** Students implement the profiling algorithm, a clever approach that:
- Tests many possible ambient temperature values ($A$)
- For each guess, uses linear regression to find the best cooling rate ($k$)
- Picks the combination that best matches your data

---

## The Profiling Algorithm

### The Challenge
We need to find three unknown values ($A$, $k$, and $u_0$) that make our model match the data—even $u_0$, because our first measurement has error too! Searching for multiple values at once is hard.

### The Key Insight
If we *guess* $A$, finding $k$ becomes easy:

1. Take logarithms: $\ln(u - A) = \ln(u_0 - A) - kt$
2. This looks like a line! $Y = b + mt$ where $Y = \ln(u-A)$ and $m = -k$
3. Use linear regression (you may have seen this in statistics) to find the slope, which gives us $k$

### The Algorithm

```
For each candidate value A in search range:
    1. Transform data: Y = ln(u - A)
    2. Perform linear regression: Y vs. t
    3. Extract k from slope: k = -slope
    4. Compute fit quality (SSE) in original domain
    
Select A* that minimizes SSE
Return (A*, k*)
```

### Why It Works
- Reduces 2D nonlinear search to 1D search + linear regression
- Guarantees finding global minimum (convex in many cases)
- Fast: ~4ms for 1000 candidates

---

## Example Code

Students implement core functions for profiling:

```julia
# Day 2: Parameter Estimation via Profiling
# Pair: [Student Names]

using Plots, LinearAlgebra

"""
    linear_regression(X, Y)

Perform simple linear regression: Y = b + m*X
Returns (slope=m, intercept=b)
"""
function linear_regression(X, Y)
    n = length(X)
    X_mean = sum(X) / n
    Y_mean = sum(Y) / n
    
    numerator = sum((X .- X_mean) .* (Y .- Y_mean))
    denominator = sum((X .- X_mean).^2)
    
    slope = numerator / denominator
    intercept = Y_mean - slope * X_mean
    
    return (slope=slope, intercept=intercept)
end

"""
    evaluate_fit(A, time, temp, u0)

For a given candidate A, compute k and SSE.
"""
function evaluate_fit(A, time, temp, u0)
    # Transform to linear domain
    Y = log.(abs.(temp .- A))
    
    # Linear regression
    result = linear_regression(time, Y)
    k = -result.slope
    
    # Compute SSE in original domain
    predicted = A .+ (u0 - A) .* exp.(-k .* time)
    residuals = temp .- predicted
    SSE = sum(residuals.^2)
    
    return (k=k, SSE=SSE)
end

"""
    profile_over_A(A_range, time, temp, u0)

Test all candidate A values and find optimal.
"""
function profile_over_A(A_range, time, temp, u0)
    SSE_values = Float64[]
    k_values = Float64[]
    
    for A in A_range
        result = evaluate_fit(A, time, temp, u0)
        push!(SSE_values, result.SSE)
        push!(k_values, result.k)
    end
    
    # Find minimum
    best_idx = argmin(SSE_values)
    A_optimal = A_range[best_idx]
    k_optimal = k_values[best_idx]
    
    return (A=A_optimal, k=k_optimal, SSE=SSE_values[best_idx])
end
```

---

## Validation Checks

Students learn that statistical fit ≠ physical correctness:

### Check 1: Does $A$ match room temperature?
- Should be close to what you measured
- Example: Room = 72°F, but fitted $A$ = 365°F → **Something went wrong!**

### Check 2: Is k positive?
- Required for cooling/heating to equilibrium
- Negative $k$ indicates model failure

### Check 3: Is k reasonable for the material?
- Metals typically cool faster (larger $k$) than ceramic
- Compare with literature values if available

### Check 4: Visual fit quality
- Residuals should be randomly scattered
- No systematic patterns in errors

---

## Materials Needed

### Data
- Day 1 experimental measurements
- Room temperature readings

### Software We'll Use
- All Day 1 tools plus [LinearAlgebra.jl](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/) package

### Resources
- Profiling algorithm explanatory slides
- Example optimization landscapes
- Validation checklist

---

## Homework Assignment

**Due:** Before Day 3 (evening of Day 2)  
**Time Estimate:** 60 minutes

### Task 1: Reading (15 minutes)
"Case Studies in Parameter Estimation Gone Wrong" - Examples where fitting led to nonsensical results

### Task 2: Refine Your Code (30 minutes)
Clean up `day2_profiling.jl`:
- Add comprehensive docstrings to all functions
- Add comments explaining major steps
- Organize into clear sections
- Test with different A_range values

### Task 3: Research Question (15 minutes)
With your partner, brainstorm questions you could answer with your data and models:
- Do metal containers cool faster than ceramic? By how much?
- What happens to your results if timing measurements are slightly off?
- Do containers of the same material give similar $k$ values across different pairs?

Write down 2-3 candidate questions.

---

## Key Takeaways

By the end of Day 2, students will:

✓ Understand the difference between forward and inverse problems  
✓ Implement an algorithm that finds best-fit values from data
✓ Recognize that good statistical fit doesn't guarantee physical validity  
✓ Be able to extract parameters from real experimental data  
✓ Write documented, reusable mathematical functions  

**Tomorrow's Preview:** We'll use our fitted models to answer scientific questions and communicate findings.

---

[← Day 1](day1.md) | [Back to Main Page](README.md) | [Next: Day 3 →](day3.md)
