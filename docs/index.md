# Complementarity by Construction
<span class="subtitle">A Novel Approach to Solving Quadratic Programs with Linear Complementarity Constraints</span>

![Three example problems for our solver, showing a hopper hopping over stairs (left), a rocket catch (middle), and a quadrotor flying through gates (right)](images/topfigure.png)

RCQP is an open-source solver for quickly finding local solutions to quadratic programs with linear complementarity constraints (LCQPs). LCQPs are incredibly expressive, as shown by the examples above, but this comes at the price of non-convexity and disjoint feasible sets, making them challenging to solve. Given our view that LCQPs are as critical to reasoning about non-smooth or switching systems as QPs are critical to smooth optimization, we hope that this solver provides a useful tool to practically tackle them.

## What is complementarity?
Complementarity constraints introduce a switching relationship between two variables so that one or the other can be positive, but not both at the same time. For example, given scalars $s$ and $t$, complementarity consists of three constraints

$$\begin{align}s \geq 0, t \geq 0, st = 0\end{align}$$

The last constraint encodes an exclusive or (XOR) between the two variables and gives the switching behavior. When $s$ and $t$ are vectors, the complementarity constraint uses element-wise multiplication $s \circ t = 0$. Often we use the shorthand $0 \leq s \perp t \geq 0$ to donate this set of constraints. 

### Common Examples

<div style="display: flex; gap: 2em;">

<div style="flex: 1;">
<strong>Contact</strong>
<br>
TODO
</div>

<div style="flex: 1;">
<strong>State-Triggered Constraints</strong>
<br>
TODO
</div>

<div style="flex: 1;">
<strong>?</strong>
<br>
TODO
</div>

</div>

### Challenges with Complementarity
-----8<----- "docs/plots/complementarity.html"

## Defining an LCQP
RCQP solve LCQPs specified using the following general form

$$\begin{align}
    \min_{z, s, t} \quad &\frac{1}{2} z^TQz+g^Tz \\
    \text{subject to} \quad &Az + b = 0 \\
    &Cx + d \geq 0 \\
    &0 \leq Lz + l \perp Rz + r \geq 0 
\end{align}$$
