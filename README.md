# <font size=6>Open Quantum-State Control with Control-Dependent Decoherence</font>

**Contributing Authors:** Cyril Morluyan Cordor<sup>1</sup>, Anthony Bloch<sup>1</sup>, Eitan Geva<sup>2</sup>

<sup>1</sup>Department of Mathematics, <sup>2</sup>Department of Chemistry, University of Michigan

Current deliverables:

- [Poster presentation](oqs-sec-redfield-lindblad-control-poster.pdf)
- *upcoming arxiv preprint*

## Contents

1. [Project Statement and Purpose of Repository](#project-statement-and-purpose-of-repository)
2. [Motivation and Abstract](#motivation-and-abstract)
3. [Open Quantum System and Bloch Ball Dynamics Refresher](#open-quantum-system-and-bloch-ball-dynamics-refresher)
4. [Animations](#animations)
5. [MATLAB Code](#matlab-code)

## Project Statement and Purpose of Repository

This project investigates the controllability of open quantum dynamics as modeled by the **secular approximation to the Redfield quantum master equation (QME)** with control-dependent decoherence and compare dynamics modeled by the **Lindblad quantum master equation** with constant, control-independent dissipation. Both equations are of the Lindblad framework, so we call the former the Control-Dependent Dissipation (CDD) master equation and the latter the Time-and-Control-Independent Dissipation (TCID) master equation.

The main purpose of this github repository is to display the animations for the dynamics of the TCID and CDD equations. We also give a brief introduction to the parameters of the project.

## Motivation and Abstract

**Motivation.** Myriad new quantum technologies&mdash;including, among many, *nuclear magnetic resonance and medical spectroscopy*, *quantum sensing*, and *quantum computing*&mdash;drive the need to construct the proper framework modeling dynamics of open quantum systems (OQS). In real-world applications, quantum systems are never closed from the environment, and hence OQS dynamics are not unitary.

**Abstract.** The challenge in controlling open quantum systems is that the environment causes *quantum decoherence* which arises from the entanglement of the system with the typically large number of environmental degrees of freedom. The true dynamics of an open quantum system are non-Markovian, but Markovian approximations such as the **Lindblad and Redfield quantum master equations** can be employed if the system is weakly coupled to the environment. Due to ease of use, the Lindblad master equation is a popular choice to model decoherence with the dissipation terms taken to be constant and/or independent of coherent, Hamiltonian controls. However, we argue that dissipation must be *control-dependent*. In particular, for a thermal bath environment, the system Hamiltonian continuously "informs" the bath-induced, irreversible processes, because the system wants to reach its thermal equilibrated state, *i.e.* the Boltzmann density operator $e^{-\beta {\hat{H}}_S}/\text{Tr}[e^{-\beta{\hat{H}_S}}]$, which is dependent on the system Hamiltonian and consequently the coherent controls. In this project, we investigate the differences in how the secular Redfield QME&mdash;an equivalent formulation to Lindblad-&mdash;with control-dependent dissipation (CDD) and the Lindblad QME with time-and-control-independent dissipation (TCID) model open system dynamics for the two-level system case. We show that the CDD dynamics are not just thermodynamically more consistent, but reveal that Hamiltonian controls may wield a greater degree of influence on the dynamics than predicted by the TCID control system.

## Lindblad and Secular Redfield QMEs on the Bloch Ball

For a more detailed introduction to the project see the poster presentation (and eventually an upcoming arxiv preprint) or for OQS dynamics in general see [^1].

For a two-level system (TLS) (or qubit), there's a bijective correspondence between the set of density operators $\mathcal{D}(\textbf{H}_S)$ and the closed unit ball $\text{𝔹} \subset \text{ℝ}^3$, called the **Bloch ball**. A system density operator $\hat{\rho}_S \in \mathcal{L}(\textbf{H}_S) \cong \text{ℂ}^{2\times 2}$ and system Hamiltonian $\hat{H}_S$ can be written as

$$
\begin{equation}
    \hat{\rho}_S(t) = \frac{1}{2} I_2 + \frac{1}{2} \sum_{j=1}^3 n_j(t) \hat{\sigma}_j, \qquad \hat{H}_S(t) = \frac{\hslash}{2} \sum_{j=1}^3 u_j(t) \hat{\sigma}_j, \qquad n_j(t), u_j(t) \in \text{ℝ},
\end{equation}
$$

where $\\{\hat{\sigma_j}\\}$ denote the Pauli state operators  and $\\{u_j\\}$ are coherent controls. The two Hamiltonian energy levels are time-dependent,

$$E_{\pm}(t) = \pm \frac{\hslash}{2} \sqrt{u_1(t)^2 + u_2(t)^2 + u_3(t)^2}.$$

For simplicity, we choose the dissipation to be **pure dephasing** relative the eigenbasis of the system Hamiltonian $\hat{H}_S$, and this leads to the Markovian QMEs for the Bloch ball:

**Lindblad QME on $\text{𝔹}$:**

$$
\begin{equation}
    \frac{d}{dt} \textbf{n}(t) = 2\textbf{h}(t) \times \textbf{n}(t) + (A - \text{Tr}[A]I_3) \textbf{n}(t) + \textbf{b}, \quad A \in \text{ℝ}^{3\times 3}, \textbf{b} \in \text{ℝ}^3
\end{equation}
$$

**Secular Redfield QME on $\text{𝔹}$:**

$$
\begin{align}
	\frac{d}{dt} \textbf{n}(t) &= \Omega(t) \begin{pmatrix} n_2 \\\\ -n_1 \\\\ 0 \end{pmatrix} - \frac{1}{2} K_a(t) \begin{pmatrix} n_1 \\\\ n_2 \\\\ 2n_3 \end{pmatrix} - D(t) \begin{pmatrix} n_1 \\\\ n_2 \\\\ 0 \end{pmatrix} + K_m(t) \begin{pmatrix} 0 \\\\ 0 \\\\ 1 \end{pmatrix} \\
	&\hspace{5cm} \Omega(t) := \sqrt{u_1(t)^2 + u_2(t)^2 + u_3(t)^2} \\
	&\hspace{5cm} K_{a,m}(t) := (1 \pm e^{-\beta\Omega(t)}) {\check{\kappa}}_{+-,-+}(t,\Omega(t)) \\
	&\hspace{5cm} D(t) := {\check{\kappa}}_{--,--}(t,0),
\end{align}
$$

where $-,+$ indicate ground and excited state indices, respectively, and $\beta$ the inverse thermodynamic temperature. Note that secular Redfield on the Bloch ball can be written in the form of Lindblad on the Bloch ball by defining

$$
\begin{equation}
\textbf{h}(t) = -\frac{\hslash}{2} \begin{pmatrix} 0 \\ 0 \\ \Omega(t) \end{pmatrix}\!\!, \,\,
	A^H(t) = \frac{1}{2\hslash^2} \begin{pmatrix} K_a(t) & 0 & 0 \\ 0 & K_a(t) & 0 \\ 0 & 0 & 2 D(t) \end{pmatrix}\!\!, \,\,
	\textbf{b}(t) = \frac{1}{\hslash^2} \begin{pmatrix} 0 \\ 0 \\ K_m(t) \end{pmatrix}\!\!.
\end{equation}
$$

The information of the bath's influence on the system is encoded by the Fourier transforms (with respect to the $\tau$ relaxation timescale) of the free-bath correlation functions $\kappa_{jk,\ell m}(t,\tau)$,

$$
\begin{align}
	{\check{\kappa}}_{+-,-+}(t,\Omega(t)) &= \frac{u_1(t)^2 + u_2(t)^2}{\Omega(t)^2} \int_\text{ℝ} C(\tau) e^{i\Omega(t)\tau} d\tau \\
	{\check{\kappa}}_{--,--}(t,0) &= \frac{u_3(t)^2}{\Omega(t)^2} \int_\text{ℝ} C(\tau) d\tau,
\end{align}
$$

where $C(\tau)$ represents the bath correlation function. We should note that the Redfield QME is valid in the instantaneous eigenbasis of the Hamiltonian $\hat{H}_S$. When diagonalized, the Hamiltonian in this case has the form $\hat{H}_S(t) = -\frac{\hslash}{2} \Omega(t) \hat{\sigma}_3$, and so dynamics are centered about the $z$-axis since the Hamiltonian diagonalized is stationary at the $z$-axis (see change-of-basis transformation in upcoming preprint). Below, however, the trajectories are converted back to the standard basis, so that the changes in the Hamiltonian control vector is explicitly seen.

## Animations

**Parameters for Numerical Simulations:**

1. **Hamiltonian.** The red vector in each of the Bloch animations is the Hamiltonian control vector $\textbf{h}(t) = (u_1(t),u_2(t),u_3(t))$. For the simulations with piecewise-constant Hamiltonian, the control functions are:

$$
\begin{equation}
	u_1(t) = \begin{cases} 0, & 0 \leq t \leq 10 \\\\ 18, & 10 < t \leq 20 \\\\ 6, & 20 < t \leq 30 \\\\ 0.8, & t > 30 \end{cases}, \quad u_2(t) = \begin{cases} 5, & 0 \leq t \leq 10 \\\\ 0, & 10 < t \leq 20 \\\\ 5, & 20 < t \leq 30 \\\\ 1.6, & t > 30 \end{cases}, \quad u_3(t) = \begin{cases} 0, & 0 \leq t \leq 20 \\\\ 14, & 20 < t \leq 30 \\\\ 1, & t > 30. \end{cases}
\end{equation}
$$

For the continuous, piecewise-linear functions, the control functions are:

$$
\begin{gather}
	u_1(t) = \begin{cases} 5, & 0 \leq t \leq 10 \\\\ 5 - 0.95(t - 10), & 10 < t \leq 15 \\\\ 0.25, & t > 15 \end{cases} \quad
%
	u_2(t) = \begin{cases} 0, & 0 \leq t \leq 5 \\\\ -0.8(t - 5), & 5 < t \leq 10 \\\\ -4 + 0.75(t - 10), & 10 < t \leq 15 \\\\ -0.25, & t > 15 \end{cases} \nonumber \\[0.5em]
%
	u_3(t) = \begin{cases} 0, & 0 \leq t \leq 5 \\\\ t - 5, & 5 < t \leq 10 \\\\ 5 - 0.9(t - 10), & 10 < t \leq 15 \\\\ 0.5 - 0.15(t - 15), & 15 < t \leq 20 \\\\ -0.25, & t > 20. \end{cases}
\end{gather}
$$

For the trajectories with evolving chimneys, the Hamiltonian controls are

$$
\begin{equation}
	u_1(t) = \begin{cases} 0, & 0 \leq t \leq 10 \\\\ 8, & 10 < t \leq 20 \\\\  -2, & 20 < t \leq 30 \\\\ 0.75, & t > 30 \end{cases} \quad
%
	u_2(t) = \begin{cases} 5, & 0 \leq t \leq 10 \\\\ 0, & 10 < t \leq 20 \\\\ 5, & 20 < t \leq 30 \\\\ 0.75, & t > 30 \end{cases} \quad
%
	u_3(t) = \begin{cases} 0, & 0 \leq t \leq 20 \\\\ 10, & t > 20 \end{cases}
\end{equation}
$$


2. **Static Parameters.** We set the temperature, Boltzmann's constant, and Planck's constant to $T = k_B = \hslash = 1$. The correlation time is $\tau_C = 0.2$.

3. **Initial Condition.** Except for the chimney animations, initial ground and excited population levels are $\rho_{--}(0) = 0.3$ and $\rho_{++}(0) = 0.7$, respectively, with initial coherence $\rho_{+-}(0) = 0.2 - 0.2i$. This corresponds to the Bloch vector **n**$(0) = (0.4, -0.4, -0.4)$. For the chimney animations, the initial Bloch vector is **n**$(0) = (0,0.4,-0.4)$.

4. **Correlation function.** The correlation function $C(\tau)$ is represented by a simple exponential decay function $C(\tau) = e^{-|\tau|/\tau_C}$.

### Steering trajectory in the Bloch ball

**Lindblad**

*Components (in energy eigenbasis) vs. Time*
<video src="https://github.com/user-attachments/assets/b2799eb6-373c-44b4-8e3f-8c0e200a0ed4"></video>

*Bloch ball trajectory*
<video src="https://github.com/user-attachments/assets/8798ce8c-ba9e-458d-b36c-66e439b97f7e"></video>


### Redfield-Bloch with Purity Chimneys
https://github.com/user-attachments/assets/f937ce60-6533-4cc9-ba22-489a8e58dde9



## MATLAB Code

**Coming soon!**


[^1]: H.P. Breuer and F. Petruccione. The Theory of Open Quantum Systems. Oxford University Press, New York, NY, 2002.

