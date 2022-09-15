---
title: QPP to LCP conversion
draft: false
weight: 10
---

Quadratic programming (QP) problems with non-strict inequality constraints
{{< k display >}}
\begin{aligned}
	\text{minimize:}& \quad \frac{1}{2}\bm{x}^T\bm{Q}\bm{x} + \bm{c}^T\bm{x}\\
	\text{subject to:}& \quad \bm{A}\bm{x} \geq \bm{b}
\end{aligned}
{{< /k >}}
where {{<k>}} \bm{Q} = \bm{Q}^T {{</k>}} can be converted to Linear complementarity problems (LCPs) [^1]
{{< k display >}}
\operatornamewithlimits{find}_{\bm{z}} \ \text{s.t.}: \quad 0 \leq (\bm{q} + \bm{M}\bm{z}) \perp \bm{z} ≥ 0
{{< /k >}}

## Pre-requisit
The pre-requisit for this convertion are the Karuch-Kuhn-Tucker (KKT) conditions [^2]
{{< k display >}}
\begin{aligned}
	\bm{g}(\bm{x}) ≤ 0 \\
	\bm{λ} ≤ 0 \\
	\bm{λ}^T \bm{g}(\bm{x}) = 0 \\
	∇f(\bm{x}) + \bm{λ}^T ∇\bm{g}(\bm{x}) = 0
\end{aligned}
{{< /k >}}
for finding the solution to a constrained optimization problem in the form
{{< k display >}}
\begin{aligned}
	\text{minimize:}& \quad f(\bm{x}) \\
	\text{subject to:}& \quad \bm{g}(\bm{x}) ≤ 0
\end{aligned}
{{< /k >}}
where {{<k>}} f(\bm{x}) {{</k>}} must be convex.

## Conversion

Karuch-Kuhn-Tucker conditions of a QP can be written as
{{< k display >}}
\begin{aligned}
	\bm{b} - \bm{A}\bm{x} ≤ 0 \\
	\bm{λ} ≤ 0 \\
	\bm{λ}^T (\bm{b} - \bm{A}\bm{x}) = 0 \\
	\bm{x}^T \bm{Q} + \bm{c}^T - \bm{λ}^T \bm{A} = 0
\end{aligned}
{{< /k >}}
From the last KKT condition we may express {{<k>}} \bm{x} {{</k>}} as
{{< k display >}}
\bm{x} = \bm{Q}^{-1} ( \bm{A}^T \bm{\lambda} - \bm{c})
{{< /k >}}
and substitute it into the first (also the third) condition, resulting in
{{< k display >}}
\begin{aligned}
\bm{b} - \bm{A} \bm{Q}^{-1} ( \bm{A}^T \bm{\lambda} - \bm{c}) ≤ 0
\end{aligned}
{{< /k >}}
Individual terms of the LCP can then be assigned as 
{{< k display >}}
\begin{aligned}
	\bm{q} &\coloneqq - \bm{A} \bm{Q}^{-1} \bm{c} - \bm{b} \\
	\bm{M} &\coloneqq \bm{A} \bm{Q}^{-1} \bm{A}^T \\
	\bm{z} &\coloneqq \bm{λ}
\end{aligned}
{{< /k >}}

[^1]

[^1]: source: [LCP](https://en.wikipedia.org/wiki/Linear_complementarity_problem)
[^2]: source: [KKT conditions](https://mdav.ece.gatech.edu/ece-6270-spring2021/notes/14-kkt-conditions.pdf)