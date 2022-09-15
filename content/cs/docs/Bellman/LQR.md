---
title: Linear Quadratic Regulator
draft: false
---

Linear Quadratic Regulator (LQR)
================================

LQR je určen pro regulaci lineárního systému se stavovou zpětnou vazbou ve tvaru
{{< k display >}}
\bm{\dot{x}} = \bm{A} \, \bm{x} + \bm{B} \, \bm{u} \;,\quad \bm{u} = -\bm{K}\bm{x}
{{< /k >}}
s kvadratickým kritériem optimality trajektorie
{{< k display >}}
J = \int_{-∞}^{∞}
\underbrace{
\bm{x}^T \bm{Q} \, \bm{x} + \bm{u}^T \bm{R} \, \bm{u}
}_{L(\bm{x},\bm{u},τ)} \, dτ
{{< /k >}}
přičemž
{{< k display >}}
\bm{Q} = \bm{Q}^T ⪰ 0
\;,\quad 
\bm{R} = \bm{R}^T ⪰ 0
{{< /k >}}

---

Jeho syntéza je založena na nalezní řešení *Bellmanovy diferenciální rovnice* [^1]
{{< k display >}}
%\left.
-\frac{∂J^*}{∂τ}
%\right|_{τ=t}
=
%\left.
\min_{\bm{u}} \left(
	L
	+
	\frac{∂J^*}{∂\bm{x}}	
	\bm{f}
\right)
%\right|_{τ=t}
{{< /k >}}
vyjádřené v čase {{<k>}} τ = t {{</k>}} s cenou do cíle
{{< k display >}}
J^* = \bm{x}^T \bm{S} \, \bm{x} \;,\quad \bm{S} = \bm{S}^T
{{< /k >}}

---

Po dosazení výše uvedených tvarů Bellmanovy funkce, stavového popisu systému a Lagrangiánu, získáváme rovnici
{{< k display >}}
0
=
\min_{\bm{u}} \left(
\bm{x}^T \bm{Q} \, \bm{x} + \bm{u}^T \bm{R} \, \bm{u} + 2 \bm{x}^T \bm{S} ( \bm{A} \bm{x} + \bm{B} \bm{u} )
\right)
{{< /k >}}
přičemž z podmínky lokálního extrému
{{< k display >}}
\frac{∂}{∂\bm{u}} \left(
\bm{x}^T \bm{Q} \, \bm{x} + \bm{u}^T \bm{R} \, \bm{u} + 2 \bm{x}^T \bm{S} ( \bm{A} \bm{x} + \bm{B} \bm{u} )
\right) 
=
0
{{< /k >}}
lze vyjádřit optimální řízení {{<k>}} \bm{u}_\text{opt}(τ) {{</k>}}
{{< k display >}}
\bm{u}_\text{opt} = - \bm{R}^{-1} \bm{B}^T \bm{S} \, \bm{x} 
{{< /k >}}
které když dosadíme, získáme rovnici
{{< k display >}}
0
=
\bm{x}^T \bm{Q} \, \bm{x} + \bm{x}^T \bm{S} \bm{B} \bm{R}^{-1} \bm{R} \bm{R}^{-1} \bm{B}^T \bm{S} \, \bm{x} + 2 \bm{x}^T \bm{S} ( \bm{A} \bm{x} - \bm{B} \bm{R}^{-1} \bm{B}^T \bm{S} \, \bm{x} )
{{< /k >}}

Tu lze dále upravit na
{{< k display >}}
0
=
\bm{x}^T \left(
	\bm{Q} - \bm{S}\bm{B}\bm{R}^{-1} \bm{B}^T \bm{S} + \bm{S}\bm{A} + \bm{A}^T \bm{S}
\right) \bm{x}
{{< /k >}}
která platí pro libovolné {{<k>}} \bm{x}(t) {{</k>}} pokud je {{<k>}} \bm{S} {{</k>}} řešením tzv. *Continuous Algebraic Riccati Equation (C.A.R.E.)*
{{< k display >}}
\bm{Q} - \bm{S}\bm{B}\bm{R}^{-1} \bm{B}^T \bm{S} + \bm{S}\bm{A} + \bm{A}^T \bm{S}
= 0
{{< /k >}}

[^1]: [Belmannův princip optimality]({{< ref "Bellman.md" >}})