# Phase 1 — Mathematical Foundations (Working Notes)

---

## 1. Introduction / Motivation
Real-world systems often involve a combination of **physical dynamics, multi-agent interactions, and optimization under constraints**. Existing tools are fragmented: physics engines handle motion, economic/game-theory models handle agent behavior, and optimization solvers handle mathematical objectives.

This project addresses this gap by creating a **Unified Dynamic Systems Optimization Engine (UDSOE)** that:

- Integrates **physical and economic dynamics**
- Provides **transparent, from-scratch numerical solvers**
- Serves as a **modular research environment** for experiments

**Goal:** Model, simulate, and optimize complex systems with **mathematical rigor and computational clarity**.

---

## 2. State Space
Define the system variables and dimensions.

\[
x(t) = [x_1, x_2, ..., x_n] \in \mathbb{R}^n
\]

- **Continuous variables:** \(x_1, x_2, ...\)  
- **Discrete variables:** \(x_3, x_4, ...\)  
- **State representation:**  
  - Vectorized form \(x(t)\) for all system components  
  - Can include agent states, environmental variables, and resource levels

**Example:**  

\[
x(t) = 
\begin{bmatrix}
x_1(t) \\ x_2(t) \\ x_3(t)
\end{bmatrix}
=
\begin{bmatrix}
\text{position} \\ \text{velocity} \\ \text{agent state}
\end{bmatrix}
\]

**Notes / To-do:**  
- Define **initial conditions**  
- Identify **bounded/unbounded variables**  
- Determine which variables are **controllable vs exogenous**

---

## 3. Agents & Utility Functions
Each agent \(i\) has a utility function:

\[
U_i(x_i, x_{-i}) = \text{agent's payoff based on its own state and other agents' states}
\]

- **Decision rule:**

\[
x_i^* = \arg\max_{x_i} U_i(x_i, x_{-i})
\]

- **Interactions:**  
  - Agents can be **networked**  
  - Influence neighbors’ actions  
  - Can represent **market, strategic, or resource-based interactions**

**Example:** Two-agent system:

\[
U_1(x_1, x_2) = 2x_1 - x_1 x_2
\]
\[
U_2(x_2, x_1) = 3x_2 - x_1 x_2
\]

**Notes / To-do:**  
- Define agent types (rational, adaptive, stochastic)  
- Specify **interaction structure** (graph adjacency or market clearing)

---

## 4. Constraints
Mathematical representation of system limitations:

- **Inequality constraints:**

\[
g_j(x) \le 0
\]

- **Equality constraints:**

\[
h_k(x) = 0
\]

**Example:**  
- Physical: \(x_1^2 + x_2^2 \le 10\)  
- Economic: budget \(x_1 + x_2 \le 100\)  
- Strategic: resource allocation \(h_1(x) = x_1 + x_2 - R = 0\)

**Notes / To-do:**  
- Clearly classify **hard vs soft constraints**  
- Prepare for **Lagrangian formulation** in optimization

---

## 5. Dynamics
- **Continuous-time dynamics:**

\[
\frac{dx}{dt} = f(x, u)
\]

- **Discrete-time update (Euler approximation):**

\[
x_{t+1} = x_t + \Delta t \cdot f(x_t, u_t)
\]

**Example:** Particle dynamics:

\[
\frac{dx}{dt} = v, \quad \frac{dv}{dt} = F/m
\]

**Notes / To-do:**  
- Define **control inputs** \(u\)  
- Specify **stability conditions**  
- Consider **stochastic vs deterministic models**

---

## 6. Optimization
- **Objective function:**

\[
\max U_i(x_i) \quad \text{s.t. } g_j(x) \le 0
\]

- **Lagrangian formulation:**

\[
\mathcal{L}(x, \lambda) = U_i(x_i) + \sum_j \lambda_j g_j(x)
\]

- **Gradient-based update:**

\[
x_{t+1} = x_t + \eta \nabla_x \mathcal{L}(x_t, \lambda_t)
\]

**Example:** Two-agent constrained optimization:

\[
\max_{x_1, x_2} U_1(x_1, x_2) \quad \text{s.t. } x_1 + x_2 \le 10
\]

**Notes / To-do:**  
- Specify **gradient descent / iterative solvers**  
- Include **multi-agent equilibrium approximations** (e.g., Nash equilibrium)  
- Discuss **convergence criteria**

---

## 7. Assumptions & Proofs
- **Assumptions:**  
  - Dynamics are differentiable  
  - Utilities are continuous and concave where applicable  
  - Constraints are convex or linear for tractable optimization  
  - Time discretization is small enough for stability

- **Proofs / Mini-derivations:**  
  - Derivation of **gradient of utility**  
  - Proof of **feasibility of constraints**  
  - Stability proofs for **discrete-time updates**

**Notes / To-do:**  
- Add small lemmas and derivations for each major equation

---

## 8. Discussion & Limitations
- **Limitations:**  
  - Small system scale initially  
  - Not optimized for industrial-scale speed  
  - Only differentiable functions handled in optimization

- **Discussion:**  
  - Can extend to **larger multi-agent systems**  
  - Future work: stochastic dynamics, agent learning, non-convex constraints  
  - Comparison to **classical physics and DSGE models**

---

## 9. References
- Boyd, S. *Convex Optimization*, Cambridge University Press  
- Binmore, K. *Game Theory: A Very Short Introduction*  
- Courant, R. *Differential Equations*  
- MIT OpenCourseWare, *Multivariable Calculus*  
- Any relevant research papers you plan to cite
