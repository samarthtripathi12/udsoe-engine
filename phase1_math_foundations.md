# Phase 1 — Mathematical Foundations (Complete Working Notes)

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

$$
x(t) = [x_1, x_2, \dots, x_n] \in \mathbb{R}^n
$$

- **Continuous variables:** \(x_1, x_2, \dots\)  
- **Discrete variables:** \(x_3, x_4, \dots\)  
- **State representation:**  
  - Vectorized form \(x(t)\) for all system components  
  - Can include agent states, environmental variables, and resource levels

**Example:**  

$$
x(t) = 
\begin{bmatrix}
x_1(t) \\ x_2(t) \\ x_3(t)
\end{bmatrix}
=
\begin{bmatrix}
\text{position} \\ \text{velocity} \\ \text{agent state}
\end{bmatrix}
$$

**Derivations / Notes:**  
- Define **initial conditions**  
- Identify **bounded/unbounded variables**  
- Determine which variables are **controllable vs exogenous**  

---

## 3. Agents & Utility Functions
Each agent \(i\) has a utility function:

$$
U_i(x_i, x_{-i}) = \text{agent's payoff based on its own state and other agents' states}
$$

- **Decision rule:**  

$$
x_i^* = \arg\max_{x_i} U_i(x_i, x_{-i})
$$

- **Interactions:**  
  - Agents can be **networked**  
  - Influence neighbors’ actions  
  - Can represent **market, strategic, or resource-based interactions**

**Example:** Two-agent system:

$$
U_1(x_1, x_2) = 2x_1 - x_1 x_2
$$

$$
U_2(x_2, x_1) = 3x_2 - x_1 x_2
$$

**Derivations / Notes:**  
- Gradient calculation:  

$$
\nabla_{x_1} U_1 = \frac{\partial U_1}{\partial x_1} = 2 - x_2
$$

$$
\nabla_{x_2} U_2 = \frac{\partial U_2}{\partial x_2} = 3 - x_1
$$

- Define agent types (rational, adaptive, stochastic)  
- Specify **interaction structure** (graph adjacency, market clearing, networked influence)

---

## 4. Constraints
- **Inequality constraints:**

$$
g_j(x) \le 0
$$

- **Equality constraints:**

$$
h_k(x) = 0
$$

**Example:**  
- Physical: \(x_1^2 + x_2^2 \le 10\)  
- Economic: budget \(x_1 + x_2 \le 100\)  
- Strategic: resource allocation \(h_1(x) = x_1 + x_2 - R = 0\)

**Derivations / Notes:**  
- Lagrangian formulation for constrained optimization:

$$
\mathcal{L}(x, \lambda) = U_i(x_i) + \sum_j \lambda_j g_j(x) + \sum_k \mu_k h_k(x)
$$

- Identify hard vs soft constraints  
- Gradient with respect to \(x\) and multipliers \(\lambda, \mu\)

---

## 5. Dynamics
- **Continuous-time dynamics:**

$$
\frac{dx}{dt} = f(x, u)
$$

- **Discrete-time update (Euler approximation):**

$$
x_{t+1} = x_t + \Delta t \cdot f(x_t, u_t)
$$

**Example:** Particle dynamics:

$$
\frac{dx}{dt} = v, \quad \frac{dv}{dt} = F/m
$$

**Derivations / Notes:**  
- Control inputs \(u\) influence evolution  
- Stability condition: \(|\Delta t| \ll 1\)  
- Stochastic vs deterministic dynamics (placeholder for future expansion)

---

## 6. Optimization
- **Objective function:**

$$
\max U_i(x_i) \quad \text{s.t. } g_j(x) \le 0
$$

- **Gradient-based Lagrangian:**

$$
\mathcal{L}(x, \lambda) = U_i(x_i) + \sum_j \lambda_j g_j(x)
$$

- **Gradient update:**

$$
x_{t+1} = x_t + \eta \nabla_x \mathcal{L}(x_t, \lambda_t)
$$

**Example:** Two-agent constrained optimization:

$$
\max_{x_1, x_2} U_1(x_1, x_2) \quad \text{s.t. } x_1 + x_2 \le 10
$$

**Derivations / Notes:**  
- Gradient of Lagrangian:

$$
\nabla_x \mathcal{L} = 
\begin{bmatrix}
\frac{\partial U_i}{\partial x_1} + \lambda \frac{\partial g_1}{\partial x_1} \\
\frac{\partial U_i}{\partial x_2} + \lambda \frac{\partial g_1}{\partial x_2} 
\end{bmatrix}
$$

- Multi-agent equilibrium approximations (Nash equilibrium)  
- Convergence criteria placeholder  

---

## 7. Assumptions & Proofs
- **Assumptions:**  
  - Dynamics differentiable  
  - Utilities continuous and concave where applicable  
  - Constraints convex or linear  
  - Small discretization step \(\Delta t\) for stability

- **Proofs / Derivations Placeholders:**  
  - Gradient of utility derivations  
  - Feasibility of constraints  
  - Stability proofs for discrete updates  
  - Add small lemmas as needed  

---

## 8. Discussion & Limitations
- **Limitations:**  
  - Small-scale systems initially  
  - Not industrial-scale optimized  
  - Only differentiable functions in optimization

- **Future Work:**  
  - Stochastic dynamics  
  - Multi-agent learning  
  - Non-convex constraints  
  - Comparison to classical physics and DSGE models  

---

## 9. References
- Boyd, S. *Convex Optimization*, Cambridge University Press  
- Binmore, K. *Game Theory: A Very Short Introduction*  
- Courant, R. *Differential Equations*  
- MIT OpenCourseWare, *Multivariable Calculus*  
- Add relevant research papers you plan to cite
