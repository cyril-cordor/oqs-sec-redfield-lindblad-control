# Open Quantum-State Control with Control-Dependent Decoherence

## Project Statement and Motivation

We investigate the controllability of open quantum dynamics as modeled by the **secular approximation to the Redfield quantum master equation (QME)** with control-dependent decoherence and compare dynamics modeled by the **Lindblad QME** with constant, control-independent dissipation.

**Motivation.** Myriad new quantum technologies&mdash;including, among many, *nuclear magnetic resonance and medical spectroscopy*, *quantum sensing*, and *quantum computing*&mdash;drive the need to construct the proper framework modeling dynamics of open quantum systems (OQS). In real scenarios, quantum systems are never closed from the environment, and hence OQS dynamics are not unitary.

**Abstract.** The challenge in controlling open quantum systems is that the environment causes *quantum decoherence* which arises from the entanglement of the system with the typically large number of environmental degrees of freedom. The true dynamics of an open quantum system are non-Markovian, but Markovian approximations such as the Lindblad and Redfield quantum master equations can be employed if the system is weakly coupled to the environment. Due to ease of use, the Lindblad master equation is a popular choice to model decoherence with the dissipation terms taken to be constant and/or independent of coherent, Hamiltonian controls. However, we argue that dissipation must be *control-dependent*. In particular, for a thermal bath environment, the system Hamiltonian continuously "informs" the bath-induced, irreversible processes, because the system wants to reach its thermal equilibrated state, *i.e.* its Gibbs state, which is dependent on the system Hamiltonian and consequently the coherent controls. In this project, we mathematically investigate the differences in how the 	secular Redfield equation&mdash;an equivalent formulation to Lindblad-&mdash;with control-dependent dissipation and the Lindblad equation with constant, control-independent dissipation model open system dynamics. We show that Redfield dynamics are not just thermodynamically more consistent, but reveal that Hamiltonian controls may wield a greater degree of influence on the dynamics than predicted by Lindblad with constant, control-independent dissipation.

## OQS Dynamics and Quantum Master Equations (QME)

The true dynamics of an open quantum system are non-Markovian and can be modeled by the *Nakajima-Zwanzig generalized quantum master equation* (NZ-GQME), a first-order, integro-differential equation \cite{nakajima,zwanzig}. In general, obtaining exact solutions to the NZ-GQME is not tractable, even numerically. However, in many practical applications, the quantum system is weakly coupled to the environment/bath, and so one can approximate the system's dynamics as Markovian. More precisely, the Markovian approximation is valid when the timescale of the environmental fluctuations, the *correlation time*, is significantly shorter than the system relaxation timescale, $\tau_{_C} \ll \tau_{_R}$. The two Markovian approximations we focus on are the Lindblad QME,

$$\begin{equation}
    \frac{d}{dt} \hat{\rho}(t) = -\frac{i}{\hslash} [\hat{H}(t),\hat{\rho}(t)] + \sum_{j=1}^N \gamma_j \left(\hat{L}_j \hat{\rho}(t) \hat{L}_j^\dagger - \frac{1}{2} \left\{\hat{L}_j^\dagger \hat{L}_j, \hat{\rho}(t)\right\}\right), \quad N \leq d = \dim(\mathbf{Hbold}_S),
\end{equation}$$

and the secular approximation to the Redfield QME,

$$\begin{align}
	\frac{d}{dt} \rho_{jk}(t) = -i \omega_{jk} \rho_{jk}(t) &- \frac{1}{2\hslash^2} \sum_{\ell=1}^d \rho_{jk}(t) \big(\check{\kappa}_{j\ell,\ell j}(\omega_{j\ell}) + \check{\kappa}_{k\ell,\ell k}(-\omega_{\ell k})\big) \\
	&+ \frac{\delta_{jk}}{\hslash^2} \sum_{\ell=1}^d \rho_{\ell\ell}(t) \check{\kappa}_{\ell j,j\ell}(\omega_{\ell j}), \quad j,k \in \{1,\ldots,d\} \notag
\end{align}$$
