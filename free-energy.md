Introduction to free energy calculations
---

[Yuanqing Wang](wangyq.net/contact),
Simons Center Fellow;
[wangyq@wangyq.net](mailto:wangyq@wangyq.net)


Would appreciate your feedback at: <https://forms.gle/rkGLPHtJ9ncHHuqBA>

### Why are we doing free energy calculations? 🤔
The protein-ligand binding free energy gives us
qauntitative insights into the behavior or small molecules,
which is our best bet, at the protein level,
to provide some educated guess about the potency of the compound. 💊

Consider a system
with protein $P$, ligand $L$, and protein-ligand complex $PL$,
with reversible binding behavior:

$$
P + L \rightleftharpoons PL
$$

we are interested in the association coëfficient: 🤝

$$
K_a = \frac{[PL]}{[P][L]}.
$$

This can be associated with the Gibbs free energy by

$$
\Delta G_{P + L \rightleftharpoons PL} = -kT \ln K_a
$$


### Definition of free energy 

The difference between free energies are simply defined as:
$$
\Delta A_{AB} = A_B - A_A
$$

where $A$ is the Helmholtz free energy:

$$
A = E - TS
= H - PV - TS 
= G - PV.
$$

BTW, checkout the relationship between Helmholtz free energy and autoencoder discussed by Hinton [here](https://proceedings.neurips.cc/paper/1993/hash/9e3cfc48eccf81a0d57663e129aef3cb-Abstract.html).


### Free energy perturbation
Recall that Helmholtz free energy is related to the canonical partition functions by

$$
A = -kT \ln Q
$$

where

$$
Q(N, V, T)
= C_N \int d^N \mathbf{p} d^N \mathbf{r}
\exp(-\beta \mathcal{H}),
$$

where the Hamiltonian

$$
\mathcal{H} = \sum\frac{\mathbf{p}^2}{2m} + U.
$$

When integrating over the phase space,
the momentum factor cancels out of the ratio, allowing us to _just_ use the ratio of
_configurataional partition function_:

$$
Z = \int d^N \mathbf{r} \exp(-\beta U)
$$

to evaluate the free energy:

$$
\Delta A_{AB} 
= A_B - A_A
= -kT \ln \frac{Z_B}{Z_A}.
$$

Pluggin in the previous equation,
we trivially arrive at (verify this!):

$$
\Delta A_{AB} = -kT \ln \langle \exp(-\beta (U_B - U_A)) \rangle _A
$$

where the notation $\langle\rangle_A$ signifies that the average is taken w.r.t. the canonical distribution of the state $A$.

Voilà! Now we have the expression of the free energy difference _exactly_!

**Discussion**: 
why haven't we designed cures for all cancers yet using this _exact_ equation? 
What's wrong?

**Remedy**: 
Generate a bunch of intermediate state and rewrite:

$$
\Delta A_{AB}
= -kT 
\sum\limits_{\alpha=1}^{M-1}
\ln
\langle
\exp\big(
-\beta
\small(
U_{\alpha+1}
- U_\alpha
\small)
\big)
\rangle_\alpha.
$$

And why is this still legal? 🤨

### Adiabatic switching 📈

One way to select infinite many such states  $\{\alpha \}$ is by defining

$$
U(\mathbf{r}, \lambda)
= f(\lambda)U_A(\mathbf{r})
+ g(\lambda)U_B(\mathbf{r})
$$

with switching functions satisfying

$$
f(0) = g(1) = 1;
f(1) = g(0) = 0.
$$

Now the discrete sum becomes an intergral (verify this):

$$
\Delta A_{AB} 
= \int\limits_0^1
\frac{\partial A}{ \partial \lambda} d\lambda
= \int\limits_0^1 \langle\frac{\partial U}{\partial \lambda}\rangle_\lambda d\lambda.
$$
This is called thermodynamic integration.

Now let's look at the dummest choice of the $\lambda$-schedule:

$$
f(\lambda) = 1 - \lambda; g(\lambda) = \lambda.
$$

Plugging in, we have:

$$
\Delta A_{AB} = 
\int\limits_0^1 \langle U_B - U_A \rangle_\lambda d\lambda
$$

How does this relate to our old friend, the second law of thermodynamics?

### Jarzynski's equality
We have now been restricting ourselves to the realm of equilibrium free energy methods.
How can we jump out of that?🏃‍♀️

The work–free–energy inequality

$$
\langle W_{AB}(x) \rangle _A \geq \Delta A_{AB}
$$

dictates that we can get the upper bound of free energy difference from worked performed on the system would only lead to an upper bound.

Jarzynski's equality, nevertheless, states that if we don't average the work itself, but the term $\exp(-\beta W_{AB}(x))$, we can establish an equal relationship:

$$
\Delta A_{AB} = -kT \langle \exp(-\beta W_{AB}(x))\rangle
$$

which is the foundation for nonequilibrium free energy methods.






