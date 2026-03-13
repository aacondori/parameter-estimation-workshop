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
- **Measurement error:** Recognize sources of noise and uncertainty
- **Controlled experiments:** Design rigorous experiments with proper controls

### Technical Skills
- **Pluto notebooks:** Interactive exploration and reactive computing
- **VS Code:** Production coding environment
- **Julia vectors:** Data structures for measurements
- **Plotting:** Create scatterplots with Plots.jl

### Collaboration
- **Pair work:** Collaborate effectively throughout the day
- **Peer explanation:** Communicate findings to other students

---

## Schedule

### Morning Session (9:00 AM - 12:00 PM)

| Time | Activity | Description |
|------|----------|-------------|
| 9:00-9:30 | Welcome & Overview | Program goals, Newton's Law introduction, form pairs |
| 9:30-10:15 | What is Data? | Define data/variables/datasets; discuss measurement error |
| 10:15-10:30 | *Break* | |
| 10:30-11:30 | Designing Our Experiment | Identify controlled variables, complete design worksheet |
| 11:30-12:00 | Preparation | Set up experimental stations, practice measurements |

**Key Activity:** Students design a controlled experiment to investigate: *"How does container material affect cooling rate?"*

### Afternoon Session (1:00 PM - 5:00 PM)

| Time | Activity | Description |
|------|----------|-------------|
| 1:00-2:00 | Conduct Experiment | Collect temperature measurements every 2 minutes for 20 minutes |
| 2:00-2:15 | *Break* | |
| 2:15-3:15 | Visualizing Data | Live coding: Create scatterplots in VS Code |
| 3:15-3:30 | Gallery Walk | Peer review of plots, observe patterns across materials |
| 3:30-4:15 | Describing Patterns | Pluto demo: Vocabulary for describing data trends |
| 4:15-4:30 | *Break* | |
| 4:30-5:00 | Wrap-Up | Share findings, preview Day 2 |

**Key Activity:** Each pair creates their first Julia script (`day1_my_experiment.jl`) to visualize their cooling data.

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

### Software
- Julia 1.11+ installed
- VS Code with Julia extension
- Pluto.jl package
- Plots.jl package

### Resources
- Experimental Design Worksheet
- Pattern Description Template
- Example cooling data (Pluto notebooks)

---

## Homework Assignment

**Due:** Before Day 2 (evening of Day 1)  
**Time Estimate:** 60-90 minutes

### Task 1: Reading (20 minutes)
Read "Newton's Law of Cooling: History and Physics" (3-page article)

**Reflection questions:**
- Why does temperature approach room temperature asymptotically rather than linearly?
- What does "proportional to temperature difference" mean in your own words?

### Task 2: Pluto Exploration (40 minutes)
Complete interactive notebook: `Forward-Problems.jl`

- Manipulate sliders for A (ambient), k (rate constant), u₀ (initial temp)
- Answer embedded questions about parameter effects
- Try to match model to your experimental data

### Task 3: Verify the Solution (30 minutes)
On paper, verify that u(t) = A + (u₀ - A)e^(-kt) satisfies the differential equation du/dt = -k(u - A)

---

## Key Takeaways

By the end of Day 1, students will:

✓ Understand that data comes from deliberate experimental design  
✓ Recognize that all measurements contain error and noise  
✓ Be able to create scientific visualizations in Julia  
✓ Describe patterns in temperature-time data qualitatively  
✓ Work effectively with a partner on technical tasks  

**Tomorrow's Preview:** We'll build a mathematical model to *predict* these patterns and estimate the parameters from our data.

---

[← Back to Main Page](README.md) | [Next: Day 2 →](day2.md)
