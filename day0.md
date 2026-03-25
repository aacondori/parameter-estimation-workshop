# Day 0: Preliminaries

**Theme:** *Getting Ready for the Workshop*

---

## Overview

Before the workshop begins, please complete the setup steps below. This ensures we can dive straight into experiments and coding on Day 1 without technical delays.

**Time Estimate:** 90 minutes  
**Deadline:** Complete before Day 1

---

## Learning Outcomes

By completing these preliminaries, you will:

### Technical Skills
- **Julia basics:** Launch Julia, run simple expressions, install packages
- **VS Code proficiency:** Create and run `.jl` files, use the integrated terminal
- **Pluto notebooks:** Create reactive notebooks, understand how cells auto-update
- **AI assistance:** Use GitHub Copilot to ask questions and explore code

### Mathematical Foundations
- **Exponential functions:** Recognize $e^{-kt}$ as exponential decay
- **Logarithmic properties:** Apply rules like $\ln(e^x) = x$ and $\ln(ab) = \ln a + \ln b$
- **Differentiation:** Compute derivatives of exponential functions

### Collaboration Setup
- **Microsoft Teams:** Ready to access shared workspace and spreadsheets

---

## Step 1: Install Julia

[Julia](https://julialang.org/learning/) is the programming language we'll use throughout the workshop. It's designed for scientific computing and is both fast and easy to learn.

### Installation

1. Go to [julialang.org/downloads](https://julialang.org/downloads/)
2. Download **Julia 1.11** (or newer) for your operating system
3. Run the installer with default settings
4. Verify installation: Open a terminal and type `julia --version`

**Expected output:** `julia version 1.11.x` (or newer)

### Quick Test

Open Julia (search for "Julia" in your applications) and try:

```julia
println("Hello, workshop!")
1 + 1
```

You should see `Hello, workshop!` and `2`. Type `exit()` to close Julia.

---

## Step 2: Install VS Code

[VS Code](https://code.visualstudio.com/) is a professional code editor that we'll use for writing and running Julia scripts.

### Installation

1. Go to [code.visualstudio.com](https://code.visualstudio.com/)
2. Download and install for your operating system
3. Launch VS Code

### Install the Julia Extension

1. In VS Code, click the Extensions icon (left sidebar, looks like four squares)
2. Search for "Julia"
3. Install **Julia** by julialang (the official extension)
4. Restart VS Code

### Verify Setup

1. Create a new file: `File → New File`
2. Save it as `test.jl` (the `.jl` extension tells VS Code it's Julia)
3. Type: `println("VS Code + Julia works!")`
4. Press `Ctrl+Enter` (or `Cmd+Enter` on Mac) to run the line
5. You should see the output in a Julia terminal that opens at the bottom

---

## Step 3: Install Julia Packages

Julia packages extend what Julia can do. We need a few for the workshop.

### Open Julia's Package Manager

1. Open Julia (from your applications or by typing `julia` in a terminal)
2. Press `]` to enter package mode (the prompt changes from `julia>` to `pkg>`)

### Install Required Packages

Type these commands one at a time (each may take a minute or two):

```julia
add Pluto
add Plots
```

Press `Backspace` to exit package mode and return to `julia>`.

### Verify Packages Work

```julia
using Plots

# Quick test: create a simple plot
plot(x->x^2, title="Test Plot", label="y = x²")
```

A plot window should appear. Close it when done.

**Note:** `LinearAlgebra` and `Statistics` are built into Julia (no installation needed).

---

## Step 4: Try Pluto Notebooks

Pluto is an interactive notebook environment where changes update all connected code automatically. We'll use it for exploration and demos.

### Launch Pluto

In Julia, run:

```julia
using Pluto
Pluto.run()
```

Your web browser will open with Pluto's welcome page.

### Create a Test Notebook

1. Click "New notebook"
2. In the first cell, type: `x = 5`
3. Press `Shift+Enter` to run
4. In the next cell, type: `x + 10`
5. Press `Shift+Enter`—you should see `15`
6. Now go back and change `x = 5` to `x = 7` and run it (by pressing `Shift+Enter`)
7. Notice that the second cell automatically updates to `17`!

This "reactivity" is what makes Pluto special for exploring mathematical models.

### Close Pluto

Close the browser tab, then press `Ctrl+C` in the Julia terminal to stop the server.

---

## Step 5: Accounts and Access

### Microsoft Teams

All workshop participants will be invited to join a dedicated Microsoft Teams workspace. During the workshop, we'll use it to:

- Share experimental data in a class-wide spreadsheet
- Post announcements and schedule updates
- Collaborate with your partner between sessions

If you don't have a Microsoft Teams account or can't access it through your school, please contact us before Phase One begins.

### GitHub Copilot (AI Coding Assistant)

GitHub Copilot is an AI assistant that helps you write code. It can:

- **Explain code:** Highlight unfamiliar code and ask "What does this do?"
- **Answer questions:** Ask how to create a plot, fix an error, or understand a concept
- **Suggest completions:** As you type, Copilot suggests the next lines of code
- **Debug:** Paste an error message and ask for help fixing it

During the workshop, Copilot can help you understand Julia syntax, troubleshoot errors, and explore ideas—while you stay in control of what you write.

#### Step 1: Create a GitHub Account

1. Go to [github.com](https://github.com/) and click "Sign up"
2. Use your personal email (you'll verify your student status separately)
3. Complete the account setup

#### Step 2: Get Free Access (GitHub Education)

As a student, you qualify for free GitHub Copilot through the GitHub Student Developer Pack:

1. Go to [education.github.com/pack](https://education.github.com/pack)
2. Click "Sign up for Student Developer Pack"
3. Verify your student status using:
   - Your school email address, OR
   - A photo of your student ID
4. Approval typically takes a few minutes to a few days

Once approved, GitHub Copilot is free for as long as you're a student!

**Don't want to apply for the Student Developer Pack?** No problem! With a free GitHub account, you still get GitHub Copilot Free:
- 2,000 code completions per month
- 50 chat messages per month

This is plenty for the workshop. You can always apply for the Student Developer Pack later if you want unlimited access.

#### Step 3: Install in VS Code

1. In VS Code, click the Extensions icon (left sidebar)
2. Search for "GitHub Copilot" and install both:
   - **GitHub Copilot** (autocomplete suggestions)
   - **GitHub Copilot Chat** (chat interface)
3. Click "Sign in to GitHub" when prompted
4. Authorize VS Code to access your GitHub account

#### Step 4: Verify It Works

1. Open a `.jl` file in VS Code
2. Click the Copilot Chat icon in the sidebar (speech bubble)
3. Type: "What is Julia?" and press Enter
4. You should see Copilot respond with an explanation

**Note:** If your Student Developer Pack hasn't been approved yet, you can still use GitHub Copilot's free tier (limited to 2,000 completions and 50 chat messages per month).

#### Using Copilot Responsibly

Copilot is a tool, not a replacement for learning. During the workshop:

- ✓ Use it to understand error messages
- ✓ Ask it to explain code you don't understand
- ✓ Use it to explore "what if" questions
- ✗ Don't copy code without understanding it
- ✗ Don't let it write your entire solution—you learn by doing!

---

## Step 6: Math Prerequisites Review

The workshop builds on precalculus and introductory calculus. If any of these feel rusty, a quick review will help.

### Functions and Exponentials

You should be comfortable with:

- Function notation: $f(x)$, $u(t)$
- Exponential functions: $e^x$, $e^{-kt}$
- What "exponential decay" or "exponential growth" looks like on a graph

**Quick check:** Can you sketch $y = 3^{2x}$ for $x \geq 0$?  What about $y = e^{-3x}$?

### Logarithms

You should know:

- $\ln(e^x) = x$
- $\ln(ab) = \ln(a) + \ln(b)$
- How to solve $e^{-kt} = 0.5$ for $t$

**Quick check:** If $e^{-2t} = 0.25$, what is $t$? Can you find an *exact* solution (no decimals)?  What about an approximation (with decimals)?

### Derivatives (Light Introduction)

On Day 2, we'll verify that our model satisfies a differential equation. You should know:

- The derivative of $e^{kt}$ is $ke^{kt}$
- The chain rule: derivative of $f(g(t))$ involves $f'(g(t)) \cdot g'(t)$

Don't worry if differential equations are new—we'll introduce everything you need.

---

## Troubleshooting

### Julia won't install

- Make sure you have administrator privileges
- Try downloading a different version (e.g., 1.10 if 1.11 fails)
- Check the [Julia installation guide](https://julialang.org/downloads/platform/)

### VS Code doesn't recognize Julia

- Restart VS Code after installing the Julia extension
- Make sure Julia is in your system PATH (the installer usually does this automatically)
- In VS Code settings, search for "Julia: Executable Path" and set it manually if needed

### Packages fail to install

- Check your internet connection
- Try again—sometimes package servers are temporarily slow
- If `Plots` takes too long, try: `add Plots; precompile` (precompilation can take 5-10 minutes the first time)

### Pluto won't open in browser

- Try a different browser (Chrome, Firefox, Edge)
- Check if something is already using port 1234
- Try `Pluto.run(port=1235)` to use a different port

---

## Checklist

Before Day 1, confirm you can:

- [ ] Run Julia from the command line (`julia --version` works)
- [ ] Open VS Code and run a `.jl` file
- [ ] Import Pluto and Plots without errors (`using Pluto; using Plots`)
- [ ] Launch a Pluto notebook and run a cell
- [ ] Access Microsoft Teams
- [ ] (Optional) GitHub Copilot responds to a test question in VS Code

If you encounter problems you can't solve, email us before the workshop. We're happy to help!

---

## What's Next?

On **Day 1**, you'll:

- Meet your partner
- Design a cooling experiment
- Collect real temperature data
- Create your first scientific visualization in Julia

Come ready to experiment, code, and collaborate!

---

[Back to Main Page](README.md) | [Next: Day 1 →](day1.md)
