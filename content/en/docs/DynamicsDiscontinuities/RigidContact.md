---
title: Rigid contact
draft: false
weight: 11
---

rigid contact in equations of motion can be inforced by a single quadratic equality constraint and two linear inequality constraint
{{< k display >}}
\begin{aligned}
	\bm{ϕ}(\bm{q})⋅\bm{f} &= 0
	\\
	\bm{\phi}(\bm{q}) &≥ 0
	\\
	\bm{f} &≥ 0
\end{aligned}
{{< /k >}}
which can be written in the compact form of an LSP as
{{< k display >}}
\operatornamewithlimits{find}_{\bm{f}} \ \text{s.t.}: 0 ≤ \bm{ϕ}(\bm{q}) ⟂ \bm{f} ≥ 0
{{< /k >}}

### Example
Take a simple cart
![](cart.jpg)
Its equations of motion can be written as
{{< k display >}}
m\ddot{q} = u + f
{{< /k >}}
suplemented by contact constraints
{{< k display >}}
	fq = 0
	\;,\quad 
	q ≥ 0
	\;,\quad 
	f ≥ 0
{{< /k >}}
written in the compact form of an LSP as
{{< k display >}}
\operatornamewithlimits{find}_{f} \ \text{s.t.}: 0 ≤ q ⟂ f ≥ 0
{{< /k >}}

---

By discretizing the EoM we can approximate {{<k>}} q_{n+1} {{</k>}} using the semi-implicit Euler scheme
{{< k display >}}
\begin{aligned}
q_{n+1} &≈ q_n + h \dot{q}_{n+1} \\
\dot{q}_{n+1} &≈ \dot{q}_n + h \ddot{q}_n
\end{aligned}
{{< /k >}}
where
{{< k display >}}
\ddot{q}_{n} = \frac{u_n+f_n}{m}
{{< /k >}}
After consecutive substitutions we attain the approximation
{{< k display >}}
q_{n+1}
=
q_n + h \dot{q}_n + \frac{h^2}{m} u_n + \frac{h^2}{m} f_n
{{< /k >}}
for which we may formulate the LCP
{{< k display >}}
\operatornamewithlimits{find}_{f} \ \text{s.t.}: 0 ≤ q_{n+1} ⟂ f_n ≥ 0
{{< /k >}}

---

In line with the original definiton of the LCP we have
{{< k display >}}
\bm{w} \coloneqq q_{n+1}
\;,\quad 
\bm{z} \coloneqq f	
{{< /k >}}
and terms
{{< k display >}}
\begin{aligned}
	\bm{q} &\coloneqq q_n + h \dot{q}_n + \frac{h^2}{m} u_n \\
	\bm{M} &\coloneqq \frac{h^2}{m}
\end{aligned}
{{< /k >}}

---

More on the topic can be read in [B3.3](https://underactuated.mit.edu/multibody.html#section3) of Russ Tedrake's underactuated notes.