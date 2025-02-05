# spatial-dynamics

Investigations based on https://doi.org/10.1371/journal.pcbi.1010684, a document which describes in more detail just the mathematical model is at https://www.overleaf.com/project/6358566dce22e16ea2b63260

## Basic RM Model

The most simple RM model, given in https://link.springer.com/article/10.1186/1475-2875-3-13 is a pair of coupled ODEs.

$$
\dot{Z} = acX(e^{-gn}-Z) - gZ
$$

$$
\dot{X} = mabZ(1-X) - rX
$$
