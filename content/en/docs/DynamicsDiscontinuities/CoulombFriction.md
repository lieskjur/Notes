---
title: Coulomb friction
draft: false
weight: 12
---

In the case of Coulomb friction there are two general cases for the friction force {{< katex >}} f {{< /katex >}}
{{< katex display >}}
f =
\begin{cases}
	\dot{q} = 0 : |f| < μmg \\
	\dot{q} \neq 0 : |f| = μmg
\end{cases}
{{< /katex >}}
where {{< katex >}} mg {{< /katex >}} is always the magnitude of the normal force and {{< katex >}} μ {{< /katex >}} the coefficient of friction. This can be written in the very compact condition
{{< katex display >}}
0 ≤ μ mg - |f| ⟂ \dot{q}
{{< /katex >}}
By introducing slack variables {{< katex >}} f^+ {{< /katex >}}, {{< katex >}} f^- {{< /katex >}} where {{< katex >}} f = f^+ - f^- {{< /katex >}} and {{< katex >}} v_\text{abs} = |\dot{q}| {{< /katex >}} we may convert the condition into an LCP
{{< katex display >}}
\operatornamewithlimits{find}_{v_\text{abs},f^+,f^-} \ \text{s.t.}:
\begin{aligned}
\quad 0 &\leq v_\text{abs} + v &\perp&  & f^+ &≥ 0 \\
\quad 0 &\leq v_\text{abs} - v &\perp&  & f^- &≥ 0 \\
\quad 0 &\leq μmg - f^+ -f^- &\perp&  & v_\text{abs} &≥ 0
\end{aligned}
{{< /katex >}}

---

source: [Example B.5 of Russ Tedrake's 'Underactuated' notes](https://underactuated.mit.edu/multibody.html#example5)