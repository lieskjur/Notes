---
title: QPP to LCP conversion
draft: false
weight: 10
---


Quadratic programming (QP) problems with non-strict inequality constraints
{{< katex display >}}
\begin{aligned}
	\text{minimize:}& \quad \frac{1}{2}\bm{x}^T\bm{Q}\bm{x} + \bm{c}^T\bm{x}\\
	\text{subject to:}& \quad \bm{A}\bm{x} \geq \bm{b}
\end{aligned}
{{< /katex >}}
where {{< katex >}} \bm{Q} = \bm{Q}^T {{< /katex >}} can be converted to Linear complementarity problems (LCP) [^1]
{{< katex display >}}
\operatornamewithlimits{find}_{\bm{z}} \ \text{s.t.}: \quad 0 \leq (\bm{q} + \bm{M}\bm{z}) \perp \bm{z} ≥ 0
{{< /katex >}}

## Pre-requisit
The pre-requisit for this convertion are the Karuch-Kuhn-Tucker (KKT) conditions [^2]
{{< katex display >}}
\begin{aligned}
	\bm{g}(\bm{x}) ≤ 0 \\
	\bm{λ} ≤ 0 \\
	\bm{λ}^T \bm{g}(\bm{x}) = 0 \\
	∇f(\bm{x}) + \bm{λ}^T ∇\bm{g}(\bm{x}) = 0
\end{aligned}
{{< /katex >}}
for finding the solution to a constrained optimization problem in the form
{{< katex display >}}
\begin{aligned}
	\text{minimize:}& \quad f(\bm{x}) \\
	\text{subject to:}& \quad \bm{g}(\bm{x}) ≤ 0
\end{aligned}
{{< /katex >}}
where {{< katex >}} f(\bm{x}) {{< /katex >}} must be convex.

## Conversion

Karuch-Kuhn-Tucker conditions of a QP can be written as
{{< katex display >}}
\begin{aligned}
	\bm{b} - \bm{A}\bm{x} ≤ 0 \\
	\bm{λ} ≤ 0 \\
	\bm{λ}^T (\bm{b} - \bm{A}\bm{x}) = 0 \\
	\bm{x}^T \bm{Q} + \bm{c}^T - \bm{λ}^T \bm{A} = 0
\end{aligned}
{{< /katex >}}
From the last KKT condition we may express {{< katex >}} \bm{x} {{< /katex >}} as
{{< katex display >}}
\bm{x} = \bm{Q}^{-1} ( \bm{A}^T \bm{\lambda} - \bm{c})
{{< /katex >}}
and substitute it into the first (and third) condition, resulting in
{{< katex display >}}
\begin{aligned}
\bm{b} - \bm{A} \bm{Q}^{-1} ( \bm{A}^T \bm{\lambda} - \bm{c}) ≤ 0
\end{aligned}
{{< /katex >}}
Individual terms of the LCP can then be assigned as
{{< katex display >}}
\begin{aligned}
	\bm{q} &\coloneqq - \bm{A} \bm{Q}^{-1} \bm{c} - \bm{b} \\
	\bm{M} &\coloneqq \bm{A} \bm{Q}^{-1} \bm{A}^T \\
	\bm{z} &\coloneqq \bm{λ}
\end{aligned}
{{< /katex >}}
[^1]

[^1]: source: [LCP](https://en.wikipedia.org/wiki/Linear_complementarity_problem)
[^2]: source: [KKT conditions](https://mdav.ece.gatech.edu/ece-6270-spring2021/notes/14-kkt-conditions.pdf)