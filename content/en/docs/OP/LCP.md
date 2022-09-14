---
title: Linear Complementarity Problem (LCP)
draft: false
weight: 1
---

Linear Complementarity problems can be defined as
{{< katex display >}}
\operatornamewithlimits{find}_{\bm{w},\bm{z}} \ \text{subject to}: \quad
\begin{aligned}
\bm{w} &= \bm{q} + \bm{M} \bm{z} \\
\bm{w},\bm{z} &\geq 0 \\
\bm{w}^T\bm{z} &= 0
\end{aligned}
{{< /katex >}}
which we may write in the short-hand
{{< katex display >}}
\operatornamewithlimits{find}_{\bm{z}} \ \text{s.t.}: \quad 0 \leq (\bm{q} + \bm{M}\bm{z}) \perp \bm{z} ≥ 0
{{< /katex >}}