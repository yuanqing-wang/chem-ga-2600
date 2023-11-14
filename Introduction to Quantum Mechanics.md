---

---
---
[Yuanqing Wang](wangyq.net/contact), Simons Center Fellow; [wangyq@wangyq.net](mailto:wangyq@wangyq.net)

### Recap: Fundamental Postulates of Quantum Mechanics
- How is the physical state of the system described? 🔎
- How are physical observables represented?
- What are the possible outcomes of a given experiment? 🔬
- What is the expected result when an average over a very large number of observations is performed? 
- How does the physical state of a system evolve in time?
- What types of measurements are compatible with each other?

### Recap: state vector
$$
\bra{\psi} =
\begin{bmatrix}
\alpha_1 \\
\alpha_2 \\
.\\
.\\
.
\end{bmatrix}
$$
This is a Dirac ket vector.

Correspondingly, the bra vector:
$$
\bra{\psi} = \big( \alpha_1^*, \alpha_2^*, ...\big)
$$
their product: 
$$
\braket{\psi | \psi} = \sum \alpha \alpha^* = \sum | \alpha |^2 = 1
$$
More generally,
$$
\braket{\psi | \phi} = \sum\limits_k \psi^*_k\phi_k = \braket{\phi | \psi}^*
$$
### Physical observables
Postulate: physical observables are represented by linear Hermitian operators
$$
\hat{A}\ket{\phi} = \ket{\phi'}
$$
The outcomes of a physical measurement must be one of the eigenvalues of the operator.
$$
\hat{A}\ket{a} = a\ket{a}
$$
**The eigenvalues of Hermitian operators are real.** (Verify)

Any operator can be expressed as the tensor (outer) product
$$
\hat{A} = \sum a \ket{a} \bra{a}
$$
**The eigenvectors of Hermitian operators form a complete orthonormal set of vectors spanning the Hilbert space.** (Verify)

The expectation of an operator can be written as 
$$
\braket{\hat{A}} = \braket{\Psi | \hat{A} | \Psi}
$$
**No experiment can measure two observables simultaneously unless they share eigenvectors.** (Verify)

### Time evolution & the Schrodinger equation
Postulate: state vector evolves with time as (the Schrodinger equation):
$$
i\hbar \frac{\partial}{\partial t}  = \hat{\mathcal{H}} \ket{\Psi(t)}
$$
Solved analytically:
$$
\ket{\Psi(t)} = \exp(-i\hat{H}\frac{t}{\hbar}) \ket{\Psi(0)}
$$
the exponential term is known as the time evolution operator or quantum propagator.

### Position and momentum operators
We use $\hat{x}$ and $\hat{p}$ to denote the quantum mechanical position and momentum operators.

Their eigenvalues:
$$
\hat{x} \ket{x} = x \ket{x}; \hat{p} \ket{p} = p \ket{p}
$$
**Heisenberg uncertainty principle**:
$$
\Delta x \Delta p \geq \frac{\hbar}{2}
$$
Verify that they do not commute and:
$$
[\hat{x}, \hat{p}] = \hat{x}\hat{p} - \hat{p}\hat{x} = i\hbar\hat{I}
$$
The quantum Hamiltonian operator can be obtained by promoting position and momentum to operators using the quantum-classical correspondence principle.
$$
\hat{\mathcal{H}}(\hat{x}, \hat{p}) = \frac{\hat{p}^2}{2m} + U(\hat{x})
$$
We can project the Schrodinger equation onto the basis of position eigenvectors:
$$
-\frac{\hbar^2}{2m}\frac{\partial^2}{\partial x^2} \Psi(x, t) + U(x)\Psi(x, t) = i\hbar\frac{\partial}{\partial t}\Psi(x, t)
$$
### Example: the free particle
Since there is no potential energy, the Hamiltonian is just
$$
\hat{\mathcal{H}} = \frac{\hat{p}^2}{2m}
$$
It's eigenvalues for $\hat{\mathcal{H}}$ can be expressed as
$$
-\frac{\hat{h}^2}{2m} \ket{E} = E \ket{E}
$$
The energy eigenfunction can be written as
$$
\psi_p(x) = \frac{1}{\sqrt{2\pi\hbar}} \exp(ipx/\hbar)
$$
If we restrict $x$ to an interval $[0, L]$, imposing the periodic boundary conditions $\psi_p(0) = \psi_p(L)$ we have
$$
C\exp(ip0/\hbar) = C^{ipL/\hbar}
$$
The only way to satisfy this would be to require $pL/\hbar$ is an integer multiple of $2\pi$:
$$
\frac{pL}{\hbar} = 2\pi n \Rightarrow p = \frac{2\pi \hbar}{L}n \equiv p_n
$$
The momentum eigenvalues are _quantized_! 🪜

The energy eigenvalues are also quantized as:
$$
E_n = \frac{p_n^2}{2m} = \frac{2\pi^2\hbar^2}{mL^2}n^2
$$
### Example: the harmonic oscillator
Hamiltonian:
$$
\hat{H} = \frac{\hat{p}^2}{2m} + \frac{1}{2}m\omega^2 \hat{x}^2
$$
Eigenvalue problem for $\hat{\mathcal{H}}$:
$$
[-\frac{\hbar^2}{2m} \frac{d^2}{dx^2} + \frac{1}{2} m\omega^2 x^2] \psi_n(x) = E_n \psi_n(x)
$$
The energy eigenvalues can be solved as
$$
E_n = (n + \frac{1}{2}) \hbar \omega
$$
