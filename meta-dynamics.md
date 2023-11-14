MetaDynamics
---
[Yuanqing Wang](wangyq.net/contact), Simons Center Fellow; [wangyq@wangyq.net](mailto:wangyq@wangyq.net)
Would appreciate your feedback at: https://forms.gle/Gx3TpNd8bYPzyKkPA

"Filling the free energy wells with computational sand" (Darve and Pohorille 2001) 🏖️

"Iteratively ‘filling’ the potential energy of the system by a sum of Gaussians centred along the trajectory followed by a suitably chosen set of collective variables (CVs), thereby forcing the system to migrate from one minimum to the next." (Bussi and Laio 2020)
### Review: rare events
Metastability: A probability function has peaks separated by a region magnitudes lower 🏔️

### Review: collective variables (CV)
Collective variable: a (usually low-dimensional) function of the coordinates that takes different values in relevant metastable states.

$$
P(s) = \int d x P(x) \delta (s - S(x)) 
$$
This can be further expanded as
$$
P(s) \propto \int dp dx \exp(-\beta \mathcal{H}) \prod \delta (s - S(x))
$$
We can also replace the phase space average with a time average:
$$
P(s) = \lim\limits_{\mathcal{T}\rightarrow \infty} \frac{1}{\mathcal{T}} \int\limits_0^{\mathcal{T}} dt \prod \delta (s - S(x(t)))
$$

We can write the free energy as a function of these $\{s\}$
$$
A(s) = -kT \ln P(s)
$$

### Biasing potential
We can add a bias to the potential energy function,
$$
\tilde{u}(x) = u(x) + B(S(x))
$$
the corresponding probability distribution:
$$
\tilde{P}(s) \propto \int dx \exp(-\beta (u(x) + B(S(x)))) \delta (s - S(x)) \propto \exp(-\beta (A(s) + B(s)))
$$
If $B$ is large enough, $\tilde{P}$ will be flat enough!

Unbiasing:
$$
A(s) = -B(s) - T\ln(\hat{P}) + C
$$

### Adaptive umbrella sampling
$$
B_{r+1}(s) = B_r(s) + T \ln (H_r(s))
$$
### The concept of metadynamics
- accelerates conformational transitions between metastable states
- collective variable choice is key
	- low dimension: the cost of filling a multidimensional space scales with the number of dimensions
	- only works if CV varies among different metastable states and in the transition state

### Biasing potential of metadynamics
$$
B_{t+1}(s) = B_t(s) + w \exp (-\frac{(s_t - s) ^ 2}{2\sigma^2})
$$
It becomes non-Markovian!

The resulting free energy happens to converge to the negative average biasing potential:
$$
A = \lim\limits_{t \rightarrow +\infty} -\frac{1}{t - t_\operatorname{fill}}\sum\limits_{t'=t_\operatorname{fill}}^t B_{t'}(s)
$$

Well-tempered meta-dynamics:
$$
w = \exp(-\frac{B_t(s)}{\Delta T})
$$
### Automatic learning of CVs
**Path CV**: Interpolated closest structure index: 🛣️
$$
s = \frac{\sum_i i \exp{-\lambda d_i}}{\sum_i \exp{-\lambda d_i}}
$$
where $d_i$ is the squared distance between the current position and the $i$-th reference structure

**Spectral gap optimization**: Trial-and-error: pick the best CV depending on the height of the free energy barrier

**TICA**: Choose the CV making the autocorrelation time as large as possible



