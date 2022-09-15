---
title: Prediktivní řízení
draft: false
---

Pro diskrétní systémy ve tvaru
{{< k display >}}
\begin{aligned}
	\bm{x}_{k+1} &= \bm{A}\bm{x}_k + \bm{B}\bm{u}_k \\
	\bm{y}_k &= \bm{C}\bm{x}_k
\end{aligned}
{{< /k >}}
existuje forma optimálního řízení, které využívá kvadratického kritéria
{{< k display >}}
J_{i+1}
=
(\bm{y}_{i+1}-\bm{w}_{i+1})^T \bm{Q}_{i+1} (\bm{y}_{i+1}-\bm{w}_{i+1})
+
\bm{u}_i^T\bm{R}_i\bm{u}_i
{{< /k >}}
kde {{<k>}} \bm{w}_{i+1} {{</k>}} jsou žádané hodnoty výstupů na horizontu
{{< k display >}}
i+1 = k+1,\dots,k+N
{{< /k >}}
pro určení optimálního řízení {{<k>}} \bm{u}^*_i {{</k>}}.

---

Jednotlivé stavy systému {{<k>}} \bm{x}_i {{</k>}} můžeme vyjádřit jako
{{< k display >}}
\begin{aligned}
	\bm{x}_{k+1} &= \bm{A}\bm{x}_k + \bm{B}\bm{u}_k \\
	\bm{x}_{k+2} &= \bm{A}^2\bm{x}_k + \bm{A}\bm{B}\bm{u}_k + \bm{B}\bm{u}_{k+1}\\
	\bm{x}_{k+n} &= \bm{A}^n\bm{x}_k + \sum_{j=1}^n \bm{A}^{n-j}\bm{B}\bm{u}_{k+j-1}
\end{aligned}
{{< /k >}}
přičemž jeho výstupy nabývají hodnot
{{< k display >}}
\bm{y}_{k+n} = \bm{C}\bm{A}^n\bm{x}_k + \sum_{j=1}^n \bm{C}\bm{A}^{n-j}\bm{B}\bm{u}_{k+j}
{{< /k >}}

---

Výstupy {{<k>}} \bm{y}_i \,,\; i = k+1,\ldots,k+N {{</k>}} můžeme seřadit do vektoru
{{< k display >}}
\bm{Y} = \bm{f} + \bm{G}\bm{U}
{{< /k >}}
kde
{{< k display >}}
\bm{Y}
=
\begin{bmatrix}
	\bm{y}_{k+1} \\
	\vdots \\
	\bm{y}_{k+N}
\end{bmatrix}
\;,\quad 
\bm{f}
=
\begin{bmatrix}
	\bm{C}\bm{A} \\
	\vdots \\
	\bm{C}\bm{A}^N
\end{bmatrix}
\bm{x}_k
\;,\quad 
\bm{G}
=
\begin{bmatrix}
	\bm{C}\bm{B} &  & \bm{0} \\
	\vdots & \ddots & \\
	\bm{C}\bm{A}^{N-1}\bm{B} & \dots & \bm{C}\bm{B}
\end{bmatrix}
\;,\quad 
\bm{U}
=
\begin{bmatrix}
	\bm{u}_{k} \\
	\vdots \\
	\bm{u}_{k+N-1}
\end{bmatrix}
{{< /k >}}

---

Pro celý horizont můžeme utvořit kvadratické kritérium optimality
{{< k display >}}
J = (\bm{W}-\bm{Y})^T \bm{Q} (\bm{W}-\bm{Y}) + \bm{U}^T\bm{R}\bm{U}
{{< /k >}}
kde {{<k>}} \bm{Q} {{</k>}} a {{<k>}} \bm{R} {{</k>}} jsou váhové matice a {{<k>}} \bm{W} {{</k>}} vektor žádaných výstupů
{{< k display >}}
\bm{W}
=
\begin{bmatrix}
	\bm{w}_{k+1} \\
	\vdots \\
	\bm{w}_{k+N}
\end{bmatrix}
\;,\quad 
\bm{Q}
=
\begin{bmatrix}
	\bm{Q}_{k+1} &  & \bm{0} \\
	\vdots & \ddots & \\
	\bm{0} & \dots & \bm{Q}_{k+N}
\end{bmatrix}
\;,\quad 
\bm{R}
=
\begin{bmatrix}
	\bm{R}_{k} &  & \bm{0} \\
	\vdots & \ddots & \\
	\bm{0} & \dots & \bm{R}_{k+N-1}
\end{bmatrix}
{{< /k >}}
Po dozazení {{<k>}} \bm{Y} = \bm{f} + \bm{G}\bm{U} {{</k>}} můžeme najít jeho minimum pomocí podmínky
{{< k display >}}
\frac{∂J}{∂\bm{U}} = \bm{0}
{{< /k >}}