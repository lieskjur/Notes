---
title: Rigid contact
draft: false
weight: 11
---

rigid contact in equations of motion can be inforced by a single quadratic equality constraint and two linear inequality constraint
{{< katex display >}}
\begin{aligned}
	\bm{ϕ}(\bm{q})⋅\bm{f} &= 0
	\\
	\bm{\phi}(\bm{q}) &≥ 0
	\\
	\bm{f} &≥ 0
\end{aligned}
{{< /katex >}}
which can be written in the compact form of an LSP as
{{< katex display >}}
\operatornamewithlimits{find}_{\bm{f}} \ \text{s.t.}: 0 ≤ \bm{ϕ}(\bm{q}) ⟂ \bm{f} ≥ 0
{{< /katex >}}

### Example
Take a simple cart
![](cart.jpg)
Its equations of motion can be written as
{{< katex display >}}
m\ddot{q} = u + f
{{< /katex >}}
suplemented by contact constraints
{{< katex display >}}
	fq = 0
	\;,\quad 
	q ≥ 0
	\;,\quad 
	f ≥ 0
{{< /katex >}}
written in the compact form of an LSP as
{{< katex display >}}
\operatornamewithlimits{find}_{f} \ \text{s.t.}: 0 ≤ q ⟂ f ≥ 0
{{< /katex >}}

---

By discretizing the EoM we can approximate {{< katex >}} q_{n+1} {{< /katex >}} using the semi-implicit Euler scheme
{{< katex display >}}
\begin{aligned}
q_{n+1} &≈ q_n + h \dot{q}_{n+1} \\
\dot{q}_{n+1} &≈ \dot{q}_n + h \ddot{q}_n
\end{aligned}
{{< /katex >}}
where
{{< katex display >}}
\ddot{q}_{n} = \frac{u_n+f_n}{m}
{{< /katex >}}
After consecutive substitutions we attain the approximation
{{< katex display >}}
q_{n+1}
=
q_n + h \dot{q}_n + \frac{h^2}{m} u_n + \frac{h^2}{m} f_n
{{< /katex >}}
for which we may formulate the LCP
{{< katex display >}}
\operatornamewithlimits{find}_{f} \ \text{s.t.}: 0 ≤ q_{n+1} ⟂ f_n ≥ 0
{{< /katex >}}

---

In line with the original definiton of the LCP we have
{{< katex display >}}
\bm{w} \coloneqq q_{n+1}
\;,\quad 
\bm{z} \coloneqq f	
{{< /katex >}}
and terms
{{< katex display >}}
\begin{aligned}
	\bm{q} &\coloneqq q_n + h \dot{q}_n + \frac{h^2}{m} u_n \\
	\bm{M} &\coloneqq \frac{h^2}{m}
\end{aligned}
{{< /katex >}}

---

More on the topic can be read in [B3.3](https://underactuated.mit.edu/multibody.html#section3) of Russ Tedrake's underactuated notes.