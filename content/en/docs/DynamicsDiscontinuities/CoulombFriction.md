---
title: Coulomb friction
draft: false
weight: 12
---

In the case of Coulomb friction there are two general cases for the friction force {{<k>}} f {{</k>}}
{{< k display >}}
f =
\begin{cases}
	\dot{q} = 0 : |f| < μmg \\
	\dot{q} \neq 0 : |f| = μmg
\end{cases}
{{< /k >}}
where {{<k>}} mg {{</k>}} is always the magnitude of the normal force and {{<k>}} μ {{</k>}} the coefficient of friction. This can be written in the very compact condition
{{< k display >}}
0 ≤ μ mg - |f| ⟂ \dot{q}
{{< /k >}}
By introducing slack variables {{<k>}} f^+ {{</k>}}, {{<k>}} f^- {{</k>}} where {{<k>}} f = f^+ - f^- {{</k>}} and {{<k>}} v_\text{abs} = |\dot{q}| {{</k>}} we may convert the condition into an LCP
{{< k display >}}
\operatornamewithlimits{find}_{v_\text{abs},f^+,f^-} \ \text{s.t.}:
\begin{aligned}
\quad 0 &\leq v_\text{abs} + v &\perp&  & f^+ &≥ 0 \\
\quad 0 &\leq v_\text{abs} - v &\perp&  & f^- &≥ 0 \\
\quad 0 &\leq μmg - f^+ -f^- &\perp&  & v_\text{abs} &≥ 0
\end{aligned}
{{< /k >}}

---

source: [Example B.5 of Russ Tedrake's 'Underactuated' notes](https://underactuated.mit.edu/multibody.html#example5)