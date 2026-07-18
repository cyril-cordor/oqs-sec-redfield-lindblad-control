# <font size=6>Open Quantum-State Control with Control-Dependent Decoherence</font>

**Contributing Authors:** Cyril Morluyan Cordor<sup>1</sup>, Anthony Bloch<sup>1</sup>, Eitan Geva<sup>2</sup>

<sup>1</sup>Department of Mathematics, <sup>2</sup>Department of Chemistry, University of Michigan

Poster presentation?

## Contents

1. [Purpose of Repository](#purpose-of-repository)
2. [Project Statement, Motivation, and Abstract](#project-statement-motivation-and-abstract)
3. [OQS Dynamics and Quantum Master Equations (QME)](#oqs-dynamics-and-quantum-master-equations-(qme))
4. [Bloch Vector Representation for a 2-Level System (2LS)](bloch-vector-representation-for-a-2-Level-System-(2ls))
5. [Animations](#animations)
6. [MATLAB Code](#matlab-code)

## Purpose of Repository

The main purpose of this github repository is to display animations to accompany the work/poster/blah. For more information, view the poster presentation.

## Motivation and Abstract

**Motivation.** Myriad new quantum technologies&mdash;including, among many, *nuclear magnetic resonance and medical spectroscopy*, *quantum sensing*, and *quantum computing*&mdash;drive the need to construct the proper framework modeling dynamics of open quantum systems (OQS). In real scenarios, quantum systems are never closed from the environment, and hence OQS dynamics are not unitary.

**Abstract.** The challenge in controlling open quantum systems is that the environment causes *quantum decoherence* which arises from the entanglement of the system with the typically large number of environmental degrees of freedom. The true dynamics of an open quantum system are non-Markovian, but Markovian approximations such as the **Lindblad and Redfield quantum master equations** can be employed if the system is weakly coupled to the environment. Due to ease of use, the Lindblad master equation is a popular choice to model decoherence with the dissipation terms taken to be constant and/or independent of coherent, Hamiltonian controls. However, we argue that dissipation must be *control-dependent*. In particular, for a thermal bath environment, the system Hamiltonian continuously "informs" the bath-induced, irreversible processes, because the system wants to reach its thermal equilibrated state, *i.e.* its Gibbs state $e^{-\beta {\hat{H}}_S}/\text{Tr}[e^{-\beta{\hat{H}_S}}]$, which is dependent on the system Hamiltonian and consequently the coherent controls. In this project, we investigate mathematically the differences in how the secular Redfield QME&mdash;an equivalent formulation to Lindblad-&mdash;with control-dependent dissipation and the Lindblad QME with constant, control-independent dissipation model open system dynamics. We show that Redfield dynamics are not just thermodynamically more consistent, but reveal that Hamiltonian controls may wield a greater degree of influence on the dynamics than predicted by Lindblad with constant, control-independent dissipation.

## OQS Dynamics and Quantum Master Equations (QME)

An open quantum system $S$ coupled with its environment/bath $B$ is represented by a *Hermitian*, *positive-semidefinite* density operator $\hat{\rho} \in \mathcal{L}(\mathbf{H})$ with *unity trace* over a Hilbert space $\textbf{H} = \mathbf{H}_S \otimes \mathbf{H}_B$. For a 2-level system (2LS) (or a qubit), a system density operator $\hat{\rho}_S \in \mathcal{L}(\mathbf{H}_S) \cong \mathbb{C}^{2\times 2}$ and system Hamiltonian $\hat{H}_S$ can be written as

$$
\begin{equation}
    \hat{\rho}_S(t) = \frac{1}{2} I_2 + \frac{1}{2} \sum_{j=1}^3 n_j(t) \hat{\sigma}_j, \quad \hat{H}_S(t) = \frac{\hslash}{2} \sum_{j=1}^3 u_j(t) \hat{\sigma}_j, \qquad n_j(t), u_j(t) \in \R,
\end{equation}
$$

where $\\{\hat{\sigma_j}j\\}$ denote the Pauli matrices and $\\{u_j\\}j$ are coherent controls. The 2 Hamiltonian energy levels are time-dependent, $E_{\pm}(t) = \pm \frac{\hslash}{2} \sqrt{u_1(t)^2 + u_2(t)^2 + u_3(t)^2}$.

The true dynamics of an open quantum system are non-Markovian. (See the *Nakajima-Zwanzig generalized quantum master equation*.) However, one can use Markovian approximations when the quantum system is weakly coupled to the environment/bath. More precisely, the Markovian approximation is valid when the timescale of the environmental fluctuations, the *correlation time*, is significantly shorter than the system relaxation timescale, $\tau_C \ll \tau_R$. The two Markovian approximations we focus on are the Lindblad QME,

$$
\begin{equation}
    \frac{d}{dt} \hat{\rho}(t) = -\frac{i}{\hslash} [\hat{H}(t),\hat{\rho}(t)] + \sum_{j=1}^N \gamma_j \left(\hat{L}_j \hat{\rho}(t) \hat{L}_j^\dagger - \frac{1}{2}
	\{\hat{L}_j^\dagger \hat{L}_j, \hat{\rho}(t)\}\right), \quad N \leq d = \dim(\mathbf{H}_S),
\end{equation}
$$

and the secular approximation to the Redfield QME,

$$\begin{align}
	\frac{d}{dt} \rho_{jk}(t) = -i \omega_{jk} \rho_{jk}(t) &- \frac{1}{2\hslash^2} \sum_{\ell=1}^d \rho_{jk}(t) \big(\check{\kappa}_{j\ell,\ell j}(\omega_{j\ell}) + \check{\kappa}_{k\ell,\ell k}(-\omega_{\ell k})\big) \\
	&+ \frac{\delta_{jk}}{\hslash^2} \sum_{\ell=1}^d \rho_{\ell\ell}(t) \check{\kappa}_{\ell j,j\ell}(\omega_{\ell j}), \quad j,k \in \{1,\ldots,d\} \notag
\end{align}$$

## Bloch Vector Representation for a 2-Level System (2LS)

For a 2LS, there's a bijective correspondence between the set of density operators $\mathcal{D}(\mathbf{H}_S)$ and the closed unit ball $\mathbb{B} \subset \mathbb{R}^3$ by taking the "traceless components" of (ABOVE). For simplicity, we choose the dissipation to be **pure dephasing**.

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
	D(t) &:= \frac{u_3(t)^2}{\Omega(t)^2} {\check{\kappa}}_{--,--}(0)
\end{align}
$$

## Animations

### Piecewise constant control steering trajectory in the Bloch ball

Lindblad				Redfield



### Chimney/Ellipsoids

Lindblad				Redfield

### Blah 3


## MATLAB Code


