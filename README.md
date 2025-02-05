# spatial-dynamics

Investigations based on https://doi.org/10.1371/journal.pcbi.1010684, a document which describes in more detail just the mathematical model is at https://www.overleaf.com/project/6358566dce22e16ea2b63260

## Basic RM Model

The most simple RM model, given in https://link.springer.com/article/10.1186/1475-2875-3-13 is a pair of coupled ODEs.

$$
\dot{Z} = acX(e^{-g\tau}-Z) - gZ
$$
$$
\dot{X} = mabZ(1-X) - rX
$$

Note in the original equation, $n$ is used in place of $\tau$ for the EIP, and $a=fq$. In spatial dynamics we seperated $a$ that way because some vector control may affect their components differently.
If we want to make this most basic model spatial, we need to use the mosquito demography matrix $\Omega$. First, let's recall its definition.

$$
\Omega =  \mbox{diag(g)} + \left(I- K \right) \cdot \mbox{diag}(\sigma)
$$

Note, in papers $K$ is given as `\mathcal{K}` but that command doesn't work on Github Markdown it seems. Oh well. $K$ is a matrix
whose columns sum to 1 giving the probability of arriving at each destination patch (with the diagonal being 0s, as it is conditional on leaving).
The vector $\sigma$ are the rates of leaving each patch. Therefore $\left(I-K\right) \cdot \mbox{diag}(\sigma)$ is the matrix describing net change
in population due to movement. We then add $\mbox{\diag(g)}$, a matrix of mortality rates on the diagonal, to account for death.
We we multiply on the right by the vector of populations at each patch, we get the rates of change in each population due to movement and mortality.

A spatial version of the mosquito equation is:

$$
\dot{Z}=\text{diag}(fq\kappa) \cdot (e^{-\Omega\tau}I-Z) - \Omega \cdot Z
$$

Here, $\kappa$ is the net infectiousness of humans to mosquitoes in each patch. It is given by $\Psi \cdot c X$.
This is much simpler than the formulation in the spatial dynamics paper because $X$ and $Z$ are just proportions of
infected and infectious humans and mosquitoes, respectively, so there is no need to normalize by population sizes in the biting distribution matrix.
We also assume for here that all human strata have equal propensity to be bitten.
