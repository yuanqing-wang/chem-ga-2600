[Yuanqing Wang](wangyq.net/contact), Simons Center Fellow; [wangyq@wangyq.net](mailto:wangyq@wangyq.net)

---
"All the possible solutions occur, each one being the point of departure for other bifurcations. Sometimes the pathways of this labyrinth converge. For example, you come to this house; but in other possible pasts you are my enemy; in others my friend."

---Jorge Luis Borges ["Garden of the Forking Path"](https://mycours.es/gamedesign2012/files/2012/08/The-Garden-of-Forking-Paths-Jorge-Luis-Borges-1941.pdf)

---
#### Recap: Path integral quantum propagator and canonical partition function: 
Path integral expression for the quantum propagator for the canonical density mix
$$
\begin{split}
U(x, x'; t) = \lim\limits_{P \rightarrow \infty}
(\frac{mP}{2\pi i t \hbar})^{P/2}
\int\limits_{x_1=x}^{x_{P+1=x'}}dx_2 \dots dx_P \\
\times\exp
\big(
\frac{i}{\hbar}
\sum\limits_{k=1}^P
[
\frac{mp}{2t}
(x_{k+1} - x_k)^2
- \frac{t}{2P}
(U(x_{k+1}) + U(x_k))
]
\big)
\end{split}
$$
canonical partition function:
$$
\begin{split}
Q(\beta)
=\int dx \braket{x | \exp(-\beta H) | x}
= \lim\limits_{P \rightarrow \infty}
(\frac{mp}{2\pi\beta\hbar})^{P/2}
\int dx_1 \dots dx_p\\
\times
\exp(
-\frac{1}{\hbar}\sum\limits_{k=1}^{P}\frac{mP}{2\beta\hbar}
(x_{k+1} - x_k)^2 + \frac{\beta \hbar}{2P}U(x_k) 
)|_{x_{P+1} = x_1}
\end{split}
$$
#### Recap: Path integral observables
For any Hermitian operator:
$$
\braket{\hat{A}} = \frac{1}{Q}\operatorname{Tr}[\hat{A}\exp(-\beta\hat{H})]
$$
in coordinate basis:
$$
\braket{\hat{A}} = \frac{1}{Q} \int dx \braket{x | \hat{A} \exp(-\beta\hat{H})|x}
$$
For position-dependent observables, we only need diagonal density matrix elements:
$$
\braket{\hat{A}}
=\frac{1}{Q}\int dx a(x) \braket{x |\exp{-\beta \hat{H}} | x}
$$
so we have:
$$
\begin{split}
\braket{\hat{A}} = \frac{1}{Q}
\lim\limits_{P \rightarrow \infty}
(\frac{mP}{2\pi \beta \hbar^2}) \int dx_1\dots dx_p
a(x_1)
\\
\times\exp(
-\frac{1}{\hbar}\sum\limits_{k=1}^{P}\frac{mP}{2\pi\beta\hbar^2}
(x_{k+1} - x_k)^2 + \frac{\beta \hbar}{P}(U(x_k))
)|_{x_{P+1} = x_1}
\end{split}
$$
with other indexing also standing.
Averaging the expressions with different indices we can replace $a(x_1)$ with
$$
a_P(x_1,\dots,x_P) = \frac{1}{P} \sum\limits_{k=1}^P a(x_k)
$$
We can also write this as:
$$
\braket{\hat{A}}_P = \lim\limits_{P\rightarrow \infty}\braket{a_P(x_1,\dots,x_P)}_f
$$
#### Recap: Path integral thermodynamic estimators
$$
E = \braket{\hat{H}} = \braket{\frac{\hat{p}}{2m} + U(\hat{x})}
$$
since
$$
E = -\frac{\partial}{\partial \beta} \ln Q = \frac{1}{Q} \frac{\partial q}{\partial \beta}
$$
it can be expressible using only cyclic paths
$$
\begin{split}
E = \frac{1}{Q}
\lim\limits_{P\rightarrow\infty}
(\frac{mP}{2\pi\beta\hbar^2})^{P/2}\int dx_1 \dots dx_p
\\
\times\exp(
-\frac{1}{\hbar}\sum\limits_{k=1}^{P}\frac{mP}{2\pi\beta\hbar^2}
(x_{k+1} - x_k)^2 + \frac{\beta \hbar}{P}(U(x_k))
)|_{x_{P+1} = x_1}\\
=\lim\limits_{P\rightarrow\infty}\braket{\epsilon_P(x_1,\dots,x_P)}_f
\end{split}
$$
where
$$
\epsilon_P(x_1,\dots,x_P) = 
\frac{P}{2\beta} - \sum\limits_{k=1}^{P}\frac{mP}{2\beta^2\hbar^2}(x_{k+1} - x_k)^2 + \frac{1}{P}U(x_k)
$$
is an estimator for the energy.

#### Classical isomorphism
What does the partition function $Q_P(L, T)$ resemble?

We can recast it as:
$$
\begin{split}
Q_P(L, T) = \int dp_1 \dots dp_p \int_{D(L)}d_x1\dots dx_p\\
\times \exp
\big(
-\beta \sum\limits_{k=1}^P
[
\frac{p_i^2}{2m'}
+ \frac{1}{2}m\omega_P^2(x_{k+1} - x_k)^2
+ \frac{1}{P}U(x_k)
]
\big)
\end{split}
$$
where $\omega_P = \sqrt{P} / (\beta\hbar)$ is the chain frequency.
This is the partition function of a classical polymer chain of $P$ points! 
The most efficient way to sample this system would be to project it onto *normal modes* that dates back to Chapter 1.7.
The Fourier expansion of the periodic path:
$$
x_k = \sum\limits_{l=1}^P a_l \exp(2\pi i (k-1)(l-1) / P)
$$
we can specify normal modes recursively:
$$
u_1 = a_1, u_p = a_{(P+2)/2}, u_{2k-2} = \operatorname{Re}(a_k), u_{2k-1} = \operatorname{Im}(a_k)
$$
Equivalently, write down the directed adjacency matrix $A$ with
$$
A_{ij} = 2\delta_{ij} - \delta_{i, j-1} - \delta_{i, j+1}, A_{i0}=A_{iP}, A_{i,P+1} = A_{i1}
$$
diagonalize it, yielding orthogonal matrix $O$; 
we have the forward and backward transformations (with unit Jacobian!):
$$
\begin{split}
u_k = \frac{1}{\sqrt{P}}\sum\limits O_{kl}x_l\\
x_k = \sqrt{P} \sum\limits_{l=1}^P O_{kl}^T u_l
\end{split}
$$
At the same time, we have the eigenvalues:
$$
\lambda_{2k-1} = \lambda_{2k-2} = 2[1 - \cos(\frac{2\pi(k-1)}{P})]
$$
We can now write the harmonic coupling term as:
$$
\sum\limits_{k=1}^{P}(x_k - x_{k+1}) ^2 = \sum\limits_{k=2}^{P}\lambda_k u_k^2
$$
#### Many-body path-integral molecular dynamics
For $N$ Boltzmann particles:
$$
\begin{split}
Q = 
\prod\limits_{i=1}^{N}(\frac{m_i P}{2 \pi \beta \hbar^2})^{dP/2}
\int \limits_{i=1}^{N} dr_i^{(1)}\dots dr_i^{(P)} dp_i^{1}\dots dp_i^{(P)}
\\
\times \exp
\big(
-\beta \sum\limits_{k=1}^{P}
(
\sum\limits_{i=1}^{N}\frac{p_i^{(s)^2}}{2m_i'}
+ \sum\limits_{i=1}^{N}\frac{1}{2}m_i\omega_P^2 (r_i^{k+1} - r_i^{k})^2
\\
+ \frac{1}{P} (r_1^{k},\dots,r_N^{(k)})
)
\big) |_{r_i^{(P+1)} = r_i^{(1)}}
\end{split}
$$
With staging or normal-mode variables, we can construct classical Hamiltonian as usual:
$$
\mathcal{H} = \sum_{k=1}^{P}
[
\sum\limits_{i=1}^{N}\frac{p_i^{(s)^2}}{2m_i^{(s)'}}
+ \sum\limits_{i=1}^{N}\frac{1}{2}m_i^{(k)}\omega_p^2 u_i^{(s)^2}
+ \frac{1}{P} U(r_1^{(k)}(u_1),\dots,r_N^{(k)}(u_n))
]
$$
Note that only beads with the same imaginary-time index on different chains interact with each other!