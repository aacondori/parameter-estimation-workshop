# Day 1: Experimental Design, Data Collection, and Visualization

**Theme:** *From Real Phenomena to Data*

---

## Overview

On Day 1, students transition from abstract concepts to hands-on experimentation. Working in collaborative pairs, they design and conduct cooling experiments, collect temperature data, and create their first scientific visualizations.

---

## Learning Outcomes

### Core Skills
- **Data fundamentals:** Understand data, variables, and datasets
- **Experimental workflow:** Collect → explore → model → communicate
- **Measurement error:** Understand why repeated measurements give slightly different results
- **Controlled experiments:** Design rigorous experiments with proper controls

### Technical Skills
- **Pluto notebooks:** Interactive notebooks where changes update all dependencies instantly
- **VS Code:** Professional coding environment
- **Julia vectors:** Lists of numbers for storing measurements
- **Plotting:** Create scatterplots to visualize your data

### Collaboration and Communication
- **Pair work:** Collaborate effectively throughout the day
- **Peer explanation:** Communicate findings to other students

---

## Schedule

### Morning Session (9:00 AM - 12:00 PM)

| Time Slot | Activity | Description |
|-----------|----------|-------------|
| 9:00-9:30 | Welcome & Overview | Program goals, Newton's Law introduction, meet your partner |
| 9:30-10:15 | What is Data? | Define data, variables, and datasets. Discuss measurement error |
| 10:15-10:30 | *Break* | |
| 10:30-11:30 | Designing Our Experiment | Identify controlled variables, complete design worksheet |
| 11:30-12:00 | Preparation | Set up experimental stations, practice measurements |
| 12:00-1:00 | *Lunch* | Provided—refuel before the afternoon experiment! |

**Key Activity:** Students design a controlled experiment to investigate: *"How does container material affect cooling rate?"*

This means deciding:
- What to change (container material)
- What to measure (temperature over time)
- What to keep the same (water amount, starting temperature, room conditions, timing)

### Afternoon Session (1:00 PM - 5:00 PM)

| Time Slot | Activity | Description |
|-----------|----------|-------------|
| 1:00-2:00 | Conduct Experiment | Collect data, enter into class-wide shared spreadsheet (Teams) |
| 2:00-3:15 | Visualizing Data | Live coding in pairs: Create scatterplots in VS Code |
| 3:15-3:30 | Gallery Walk | Peer review of plots, observe patterns across materials |
| 3:30-4:15 | Describing Patterns | Pluto demo: Describing what your cooling curve shows |
| 4:15-4:30 | *Break* | |
| 4:30-5:00 | Wrap-Up | Share findings, preview Day 2 |

**Key Activities:** 
- Each pair creates their first Julia script (`day1_my_experiment.jl`) to visualize their cooling data
- Connect everyday descriptions to mathematical vocabulary:
  - "Temperature drops fast at first, then slows down" → *decreasing, concave up*
  - "Approaches room temperature but never quite reaches it" → *horizontal asymptote*

---

## Example Code

Students create a script like this to visualize their experimental data:

```julia
# Day 1: Cooling Experiment Visualization
# Pair: [Student Names]
# Container material: ceramic

using Plots

# Our experimental data
time = [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]  # minutes
temperature = [195, 178, 164, 153, 144, 137, 131, 126, 122, 118, 115]  # °F
room_temp = 72  # °F

# Create scatterplot
scatter(time, temperature, 
        xlabel="Time (minutes)", 
        ylabel="Temperature (°F)",
        title="Cooling Experiment - Ceramic Container",
        label="Measured data",
        legend=:right,
        markersize=6)

# Add horizontal line for room temperature
hline!([room_temp], label="Room temperature", linestyle=:dash)

savefig("day1_cooling_curve.png")
```

---

## Materials Needed

### Equipment (per pair)
- One container (ceramic, metal, or plastic)
- Digital thermometer
- Data recording sheet
- Access to hot water station

### Software We'll Use
- Julia 1.11+
- VS Code with Julia extension
- [Pluto.jl](https://plutojl.org/) package
- [Plots.jl](https://docs.juliaplots.org/stable/#Intro-to-Plots-in-Julia) package

### Resources
- Experimental Design Worksheet
- Pattern Description Template
- Example cooling data (Pluto notebooks)

---

## Homework Assignment

**Due:** Before Day 2 (evening of Day 1)  
**Time Estimate:** 90 minutes

### Task 1: Reading (20 minutes)
Read "Newton's Law of Cooling: History and Physics" (3-page article)

**Reflection questions:**
- Why does temperature approach room temperature asymptotically rather than linearly?
- What does "proportional to temperature difference" mean in your own words?

### Task 2: Pluto Exploration (40 minutes)
Complete interactive notebook: `Forward-Problems.jl`

In this notebook, you'll explore the "forward problem", that is, given values for the model, predict what the temperature will be.

- Use sliders to adjust $A$ (ambient temperature), $k$ (cooling rate), and $u_0$ (starting temperature)
- Answer embedded questions about parameter effects
- Try to match model to your experimental data

### Task 3: Check the Math (30 minutes)
Using pencil and paper, show that $u(t) = A + (u_0 - A)e^{-kt}$ is a solution to the differential equation $\frac{du}{dt} = k(A-u)$.

*Hint: Take the derivative of $u(t)$ and simplify. You should get the right-hand side of the equation.*

---

## Key Takeaways

By the end of Day 1, students should be able to:

✓ Understand that data comes from deliberate experimental design  
✓ Understand why real measurements are never perfectly precise  
✓ Be able to create scientific visualizations in Julia  
✓ Describe patterns in temperature-time data qualitatively  
✓ Work effectively with a partner on technical tasks  

**Tomorrow's Preview:** We'll build a mathematical model to *predict* these patterns and find the values that make the model match our data.

---

[← Back to Main Page](README.md) | [Next: Day 2 →](day2.md)
