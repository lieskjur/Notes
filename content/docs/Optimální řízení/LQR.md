---
title: Linear Quadratic Regulator
draft: false
---

Linear Quadratic Regulator (LQR)
================================

LQR je určen pro regulaci lineárního systému se stavovou zpětnou vazbou ve tvaru
{{< katex display >}}
\bm{\dot{x}} = \bm{A} \, \bm{x} + \bm{B} \, \bm{u}
{{< /katex >}}
kde {{< katex >}} \bm{x} = \bm{x}(τ) \,,\; \bm{u} = \bm{u}(\bm{x}(τ)) {{< /katex >}} s kvadratickým kritériem optimality
{{< katex display >}}
J = \int_{-∞}^{∞}
\underbrace{
\bm{x}^T \bm{Q} \, \bm{x} + \bm{u}^T \bm{R} \, \bm{u}
}_{L(\bm{x},\bm{u},τ)} \, dτ
{{< /katex >}}
přičemž
{{< katex display >}}
\bm{Q} = \bm{Q}^T ⪰ 0
\;,\quad 
\bm{R} = \bm{R}^T ⪰ 0
{{< /katex >}}

---

Jeho syntéza je založena na nalezní řešení *Bellmanovy diferenciální rovnice* [^1]
{{< katex display >}}
\left. -\frac{∂J^*(\bm{x}_t,t)}{∂τ} \right|_{τ=t}
=
\left.
\min_{\bm{u}} \left(
	L(\bm{x},\bm{u},τ)
	+
	\frac{∂J^*(\bm{x}_t,t)}{∂\bm{x}}	
	\bm{f}(\bm{x},\bm{u},τ)
\right)
\right|_{τ=t}
{{< /katex >}}
s *Bellmanovou funkcí* [^1] ve tvaru
{{< katex display >}}
J^*(\bm{x}_t,t) = \bm{x}(t)^T \bm{S} \, \bm{x}(t) \;,\quad \bm{S} = \bm{S}^T
{{< /katex >}}

---

Po dosazení výše uvedených tvarů Bellmanovy funkce, stavového popisu systému a Lagrangiánu, získáváme rovnici
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
\bm{x}^T \bm{Q} \, \bm{x} + \bm{u}^T \bm{R} \, \bm{u} + 2 \bm{x}^T \bm{S} ( \bm{A} \bm{x} + \bm{B} \bm{u} )
\right)
{{< /katex >}}
přičemž z podmínky lokálního extrému
{{< katex display >}}
\frac{∂}{∂\bm{u}} \left(
\bm{x}^T \bm{Q} \, \bm{x} + \bm{u}^T \bm{R} \, \bm{u} + 2 \bm{x}^T \bm{S} ( \bm{A} \bm{x} + \bm{B} \bm{u} )
\right) 
=
0
{{< /katex >}}
lze vyjádřit optimální řízení {{< katex >}} \bm{u}^*(\bm{x}_t,τ) {{< /katex >}}
{{< katex display >}}
\bm{u}^* = - \bm{R}^{-1} \bm{B}^T \bm{S} \, \bm{x} 
{{< /katex >}}
které když dosadíme, získáme rovnici
{{< katex display >}}
0
=
\bm{x}^T \bm{Q} \, \bm{x} + \bm{x}^T \bm{S} \bm{B} \bm{R}^{-1} \bm{R} \bm{R}^{-1} \bm{B}^T \bm{S} \, \bm{x} + 2 \bm{x}^T \bm{S} ( \bm{A} \bm{x} - \bm{B} \bm{R}^{-1} \bm{B}^T \bm{S} \, \bm{x} )
{{< /katex >}}

---

Tu lze dále upravit na
{{< katex display >}}
0
=
\bm{x}_t^T \left(
	\bm{Q} - \bm{S}\bm{B}\bm{R}^{-1} \bm{B}^T \bm{S} + \bm{S}\bm{A} + \bm{A}^T \bm{S}
\right) \bm{x}_t
{{< /katex >}}
která platí pro libovolné {{< katex >}} \bm{x}_t {{< /katex >}} pokud je {{< katex >}} \bm{S} {{< /katex >}} řešením tzv. *Continuous Algebraic Riccati Equation (C.A.R.E.)*
{{< katex display >}}
\bm{Q} - \bm{S}\bm{B}\bm{R}^{-1} \bm{B}^T \bm{S} + \bm{S}\bm{A} + \bm{A}^T \bm{S}
= 0
{{< /katex >}}
[^1]: [Belmannův princip optimality]({{< ref "Bellman.md" >}})