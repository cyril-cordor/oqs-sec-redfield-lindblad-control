# <font size=6>Open Quantum-State Control with Control-Dependent Decoherence</font>

**Contributing Authors:** Cyril Morluyan Cordor<sup>1</sup>, Anthony Bloch<sup>1</sup>, Eitan Geva<sup>2</sup>

<sup>1</sup>Department of Mathematics, <sup>2</sup>Department of Chemistry, University of Michigan

Current deliverables:
Poster presentation
*upcoming arxiv preprint*

## Contents

1. [Project Statement and Purpose of Repository](#project-statement-and-purpose-of-repository)
2. [Motivation and Abstract](#motivation-and-abstract)
3. [OQS Dynamics and Quantum Master Equations (QME)](#oqs-dynamics-and-quantum-master-equations-qme)
4. [Bloch Vector Representation for a 2-Level System (2LS)](bloch-vector-representation-for-a-2-level-system-2ls)
5. [Animations](#animations)
6. [MATLAB Code](#matlab-code)

## Project Statement and Purpose of Repository

This project investigates mathematically the controllability of open quantum dynamics as modeled by the **secular approximation to the Redfield quantum master equation (QME)** with control-dependent decoherence and compare dynamics modeled by the **Lindblad quantum master equation** with constant, control-independent dissipation.

The purpose of this github repository is to display time-evolving animations of the Lindblad- and Redfield-Bloch dynamics that appear on the poster presentation (and in a future arxiv post). We give a quick introduction to the parameters of the project.

## Motivation and Abstract

**Motivation.** Myriad new quantum technologies&mdash;including, among many, *nuclear magnetic resonance and medical spectroscopy*, *quantum sensing*, and *quantum computing*&mdash;drive the need to construct the proper framework modeling dynamics of open quantum systems (OQS). In real scenarios, quantum systems are never closed from the environment, and hence OQS dynamics are not unitary.

**Abstract.** The challenge in controlling open quantum systems is that the environment causes *quantum decoherence* which arises from the entanglement of the system with the typically large number of environmental degrees of freedom. The true dynamics of an open quantum system are non-Markovian, but Markovian approximations such as the **Lindblad and Redfield quantum master equations** can be employed if the system is weakly coupled to the environment. Due to ease of use, the Lindblad master equation is a popular choice to model decoherence with the dissipation terms taken to be constant and/or independent of coherent, Hamiltonian controls. However, we argue that dissipation must be *control-dependent*. In particular, for a thermal bath environment, the system Hamiltonian continuously "informs" the bath-induced, irreversible processes, because the system wants to reach its thermal equilibrated state, *i.e.* its Gibbs state $e^{-\beta {\hat{H}}_S}/\text{Tr}[e^{-\beta{\hat{H}_S}}]$, which is dependent on the system Hamiltonian and consequently the coherent controls. In this project, we investigate mathematically the differences in how the secular Redfield QME&mdash;an equivalent formulation to Lindblad-&mdash;with control-dependent dissipation and the Lindblad QME with constant, control-independent dissipation model open system dynamics for the two-level system case. We show that Redfield dynamics are not just thermodynamically more consistent, but reveal that Hamiltonian controls may wield a greater degree of influence on the dynamics than predicted by Lindblad with constant, control-independent dissipation.

## Open Quantum System and Bloch Ball Dynamics Refresher

For a more detailed introduction to the project see the poster presentation (and eventually an upcoming arxiv preprint) or for OQS dynamics in general see [^1].

Recall that an open quantum system is represented by a Hermitian, positive-semidefinite, density operator $\hat{\rho} \in \mathcal{L}(\mathbf{H})$ with unital trace over a Hilbert space $\mathbf{H}$. Let $S$ stand for the *reduced system* or system of interest and $B$ for the environment or heat bath. The density operator of the composite system, system plus bath, lives in the Hilbert space product $\mathbf{H} = \mathbf{H}_S \otimes \mathbf{H}_B$ where $\mathbf{H}_S$ is the quantum state Hilbert space for the system of interest and $\mathbf{H}_B$ is for that of the bath. The dynamics of the composite system are assumed closed, but by taking a partial trace $\text{Tr}_B$ over the bath degrees of freedom, we can derive equations of motion for the reduced system density operator $\hat{\rho}$. The secular Redfield and Lindblad QMEs are Markovian approximations to the OQS dynamics. This approximation is valid for weak system-bath coupling and when the timescale of the bath fluctuations, the correlation time, is significantly shorter than the system relaxation time, *i.e.* $\tau_C \ll \tau_R$.

For a two-level system (2LS) (or qubit), there's a bijective correspondence between the set of density operators $\mathcal{D}(\mathbf{H}_S)$ and the closed unit ball $\mathbb{B} \subset \mathbb{R}^3$, called the **Bloch ball**. A system density operator $\hat{\rho}_S \in \mathcal{L}(\mathbf{H}_S) \cong \mathbb{C}^{2\times 2}$ and system Hamiltonian $\hat{H}_S$ can be written as

$$
\begin{equation}
    \hat{\rho}_S(t) = \frac{1}{2} I_2 + \frac{1}{2} \sum_{j=1}^3 n_j(t) \hat{\sigma}_j, \qquad \hat{H}_S(t) = \frac{\hslash}{2} \sum_{j=1}^3 u_j(t) \hat{\sigma}_j, \qquad n_j(t), u_j(t) \in \mathbb{R},
\end{equation}
$$

where $\\{\hat{\sigma_j}\\}j$ denote the Pauli matrices and $\\{u_j\\}j$ are coherent controls. The 2 Hamiltonian energy levels are time-dependent, $E_{\pm}(t) = \pm \frac{\hslash}{2} \sqrt{u_1(t)^2 + u_2(t)^2 + u_3(t)^2}$.


For simplicity, we choose the dissipation to be **pure dephasing**, and this leads to the Markovian QMEs for the Bloch ball:

**Lindblad-Bloch QME** with time- and control-independent dissipation

$$
\begin{equation}
    \frac{d}{dt} \mathbf{n}(t) = \mathbf{h}(t) \times \mathbf{n}(t) + (A - \text{Tr}[A]I_3)\mathbf{n}(t) + \mathbf{b}, \quad A \in \mathbb{R}^{3\times 3}, \, \mathbf{b} \in \mathbb{R}^3
\end{equation}
$$

**Redfield-Bloch QME** with control-dependent dissipation

$$
\begin{equation}
	\frac{d}{dt} \mathbf{n}(t) = \Omega(t) \begin{pmatrix} n_2 \\\\ -n_1 \\\\ 0 \end{pmatrix} - \frac{1}{2} K_a(t) \begin{pmatrix} n_1 \\\\ n_2 \\\\ 2n_3 \end{pmatrix} - D(t) \begin{pmatrix} n_1 \\\\ n_2 \\\\ 0 \end{pmatrix} + K_m(t) \begin{pmatrix} 0 \\\\ 0 \\\\ 1 \end{pmatrix},
\end{equation}
$$

where

$$
\begin{align}
	\Omega(t) &:= \sqrt{u_1(t)^2 + u_2(t)^2 + u_3(t)^2} \\
	K_{a,m} &:= (1 \pm e^{-\beta\Omega(t)}) \frac{u_1(t)^2 + u_2(t)^2}{\Omega(t)^2} {\check{\kappa}}_{+-,-+}(\Omega(t)) \\
	D(t) &:= \frac{u_3(t)^2}{\Omega(t)^2} {\check{\kappa}}_{--,--}(0).
\end{align}
$$

We should note that the Redfield QME is valid in the eigenbasis of the Hamiltonian $\hat{H}_S$. When diagonalized, the Hamiltonian in this case has the form $\hat{H}_S = -\frac{\hslash}{2} \hat{\sigma}_3$, and so dynamics are centered about the $z$-axis since the Hamiltonian diagonalized is stationary at the $z$-axis. Below, the trajectories are converted back to the standard basis, so that the changes in the Hamiltonian control vector is explicitly seen.

[^1]: H.P. Breuer and F. Petruccione. The Theory of Open Quantum Systems. Oxford University Press, New York, NY, 2002.


## Animations


### Piecewise constant control steering trajectory in the Bloch ball


**Redfield**

[Components (in energy eigenbasis) vs. Time](https://drive.google.com/file/d/1s7BZ-LhQthuiCBcCaCqzV7_pN2NcVqsi/view?usp=drive_link)



[Bloch Ball Dynamics](https://drive.google.com/file/d/1siKaFvoEJ3ZlyMDAQ48jkJPox5gG1-ml/view?usp=drive_link)




## MATLAB Code

**Coming soon!**


