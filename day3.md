# Day 3: Analysis, Interpretation, and Communication

**Theme:** *From Results to Insights*

---

## Overview

On the final day, students transition from individual parameter estimation to comparative analysis and scientific communication. They formulate research questions, analyze patterns across materials, connect with professionals who use modeling in their careers, and present their findings.

---

## Learning Outcomes

### Core Skills
- **Research questions:** Formulate focused, answerable questions
- **Data storytelling:** Create compelling narratives from data
- **Scientific presentation:** Communicate findings effectively
- **Code quality:** Produce well-documented, reusable code
- **Career awareness:** Identify STEM pathways using modeling

### Analysis Skills
- Compare parameters across experimental conditions
- Assess reproducibility and variability
- Conduct sensitivity analysis
- Create comparison visualizations

### Communication Skills
- Select appropriate visualizations
- Give and receive constructive feedback
- Present technical findings to peers

---

## Schedule

### Morning Session (9:00 AM - 12:00 PM)

| Time | Activity | Description |
|------|----------|-------------|
| 9:00-9:30 | Research Questions | Finalize question from three options |
| 9:30-10:45 | Comparative Analysis | Pair work implementing chosen analysis |
| 10:45-11:00 | *Break* | |
| 11:00-12:00 | Career Connections Panel | Guest speakers + Q&A |

**Three Research Question Options:**

1. **Material Comparison:** How does k differ across ceramic/metal/plastic?
2. **Reproducibility:** Do pairs with same material get consistent parameters?
3. **Sensitivity Analysis:** How do estimates change with small data perturbations?

### Afternoon Session (1:00 PM - 5:00 PM)

| Time | Activity | Description |
|------|----------|-------------|
| 1:00-2:00 | Creating Data Stories | Draft written narrative (1 page) |
| 2:00-2:15 | *Break* | |
| 2:15-3:30 | Presentation Prep | Create 5-minute presentation with slides |
| 3:30-4:30 | Peer Presentations | Small group presentations with feedback |
| 4:30-4:45 | *Break* | |
| 4:45-5:00 | Workshop Wrap-Up | Reflection, Phase Two preview |

**Key Activity:** Each pair presents findings twice to different small groups, receiving peer feedback each time.

---

## Analysis Options (Choose One)

### Option 1: Material Comparison

**Research Question:** How does container material affect cooling rate?

**Analysis Steps:**
1. Pool data from all pairs (10 ceramic, 10 metal, 10 plastic)
2. Compute mean k and standard deviation for each material
3. Create comparison visualization (bar chart with error bars or box plots)
4. Consider: Are differences statistically significant?

**Sample Code:**
```julia
# Compare k values across materials
ceramic_k = [0.082, 0.079, 0.085, ...]  # 10 values
metal_k = [0.135, 0.142, 0.138, ...]    # 10 values
plastic_k = [0.091, 0.088, 0.093, ...]  # 10 values

# Compute statistics
using Statistics
ceramic_mean = mean(ceramic_k)
ceramic_std = std(ceramic_k)
# ... repeat for metal and plastic

# Create bar chart with error bars
materials = ["Ceramic", "Metal", "Plastic"]
means = [ceramic_mean, metal_mean, plastic_mean]
stds = [ceramic_std, metal_std, plastic_std]

bar(materials, means, yerr=stds,
    ylabel="Rate constant k (min⁻¹)",
    title="Cooling Rates by Container Material",
    legend=false)
```

### Option 2: Reproducibility Study

**Research Question:** How reproducible are our parameter estimates?

**Analysis Steps:**
1. Compare parameters across pairs using same material
2. Compute coefficient of variation (CV = std/mean)
3. Identify outliers
4. Discuss sources of variation (technique, error, randomness)

**Sample Code:**
```julia
# Reproducibility within material group
ceramic_k = [0.082, 0.079, 0.085, 0.076, 0.088, ...]

cv = std(ceramic_k) / mean(ceramic_k)
println("Coefficient of variation: $(round(cv*100, digits=2))%")

# Box plot to visualize spread
boxplot(["Ceramic"], ceramic_k,
        ylabel="Rate constant k (min⁻¹)",
        title="Reproducibility of k Estimates",
        legend=false)
```

### Option 3: Sensitivity Analysis

**Research Question:** How sensitive are parameter estimates to measurement errors?

**Analysis Steps:**
1. Take your original data
2. Systematically perturb (±2°F, ±30 seconds)
3. Rerun profiling algorithm
4. Quantify how much A and k change

**Sample Code:**
```julia
# Original parameters
A_original, k_original = 72.5, 0.082

# Perturb data
temp_perturbed = temp .+ randn(length(temp)) .* 2  # ±2°F noise

# Refit
result_perturbed = profile_over_A(A_range, time, temp_perturbed, u0)

# Compare
println("Original: A=$A_original, k=$k_original")
println("Perturbed: A=$(result_perturbed.A), k=$(result_perturbed.k)")
println("Change in k: $(abs(k_original - result_perturbed.k))")
```

---

## Career Connections Panel

### Format
3-4 professionals (in-person or virtual) share how they use parameter estimation:

| Role | Example Application |
|------|-------------------|
| **Data Scientist** | Predictive modeling for customer behavior |
| **Research Scientist** | Climate modeling or biomedical research |
| **Operations Research Analyst** | Optimization in logistics/manufacturing |
| **Undergraduate Student** | STEM coursework and research projects |

### Each Speaker Covers (10 minutes)
- Brief career overview
- How they use mathematical modeling and parameter estimation
- Educational pathway (high school → college → career)
- One example project in detail

### Q&A (20 minutes)
Students ask questions about:
- Daily work activities
- Required math/programming skills
- Career preparation strategies
- Challenges and interesting problems

---

## Presentation Structure

Students create 5-minute presentations with these components:

### Required Slides
1. **Title slide:** Names, research question
2. **Experimental design:** Photo of setup, brief description
3. **Data visualization:** Your cooling curve
4. **Model fitting:** Plot showing data + fitted curve with parameters
5. **Analysis results:** Answers to your research question
6. **Conclusions and limitations:** Main takeaway + what could be improved

### Delivery Tips
- Each partner presents ~2.5 minutes
- Make eye contact with audience
- Explain plots clearly (axes, units, trends)
- End with one concrete conclusion

---

## Effective Data Stories

### Story Structure Template

**1. Hook** - Start with the question  
*"Does the material of a container affect how quickly hot water cools?"*

**2. Show** - Visual evidence  
*[Insert your key plot]*

**3. Tell** - Interpretation in plain language  
*"We found that metal containers cooled 60% faster than ceramic containers, with rate constants of 0.14 vs. 0.08 min⁻¹."*

**4. Qualify** - Acknowledge limitations  
*"However, our measurements had ±2°F uncertainty, and we didn't control for container wall thickness."*

**5. Future** - One next step  
*"To improve this study, we could use more precise thermometers and standardize container dimensions."*

---

## Materials Needed

### Data
- All pairs' fitted parameters (shared spreadsheet)
- Individual experimental data from Day 1

### Software
- All previous tools
- Statistics package for analysis
- Presentation software (PowerPoint/Google Slides)

### Resources
- Careers in Modeling worksheet
- Presentation rubric
- Peer feedback forms
- Data story template

---

## Final Deliverables

**Due:** 1 week after workshop

### 1. Written Report (3-4 pages)
- Introduction: What is Newton's Law? Why estimate parameters?
- Methods: Experimental design, profiling algorithm
- Results: Your data, fitted parameters, analysis findings
- Discussion: Interpretation, validation, limitations
- Conclusion: Main takeaway and future questions
- Appendix: Well-documented code

### 2. Presentation Slides (PDF)
Polished version of in-workshop presentation

### 3. Code Portfolio
- `day1_my_experiment.jl` (data visualization)
- `day2_profiling.jl` (parameter estimation)
- `day3_analysis.jl` (comparative analysis)

All with comprehensive documentation (docstrings, comments, organization)

---

## Key Takeaways

By the end of Day 3, students will:

✓ Formulate and answer a focused research question  
✓ Compare results across experimental conditions  
✓ Understand career pathways in mathematical modeling  
✓ Communicate technical findings to peers effectively  
✓ Produce professional-quality documented code  
✓ See themselves as capable of authentic mathematical research  

---

## Phase Two Preview

**For Continuing Students:**
- Application opens next week
- Up to 10 students (5 pairs) selected
- Fall semester research project
- Topics: Closed-form solutions, concavity conditions, sensitivity analysis
- Mentorship from university faculty and undergraduates
- Culminates in symposium presentation

---

[← Day 2](day2.md) | [Back to Main Page](README.md) | [Phase Two Info →](phase2-projects.md)
