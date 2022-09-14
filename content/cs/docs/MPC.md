---
title: Prediktivní řízení
draft: false
---

Pro diskrétní systémy ve tvaru
{{< katex display >}}
\begin{aligned}
	\bm{x}_{k+1} &= \bm{A}\bm{x}_k + \bm{B}\bm{u}_k \\
	\bm{y}_k &= \bm{C}\bm{x}_k
\end{aligned}
{{< /katex >}}
existuje forma optimálního řízení, které využívá kvadratického kritéria
{{< katex display >}}
J_{i+1}
=
(\bm{y}_{i+1}-\bm{w}_{i+1})^T \bm{Q}_{i+1} (\bm{y}_{i+1}-\bm{w}_{i+1})
+
\bm{u}_i^T\bm{R}_i\bm{u}_i
{{< /katex >}}
kde {{< katex >}} \bm{w}_{i+1} {{< /katex >}} jsou žádané hodnoty výstupů na horizontu
{{< katex display >}}
i+1 = k+1,\dots,k+N
{{< /katex >}}
pro určení optimálního řízení {{< katex >}} \bm{u}^*_i {{< /katex >}}.

---

Jednotlivé stavy systému {{< katex >}} \bm{x}_i {{< /katex >}} můžeme vyjádřit jako
{{< katex display >}}
\begin{aligned}
	\bm{x}_{k+1} &= \bm{A}\bm{x}_k + \bm{B}\bm{u}_k \\
	\bm{x}_{k+2} &= \bm{A}^2\bm{x}_k + \bm{A}\bm{B}\bm{u}_k + \bm{B}\bm{u}_{k+1}\\
	\bm{x}_{k+n} &= \bm{A}^n\bm{x}_k + \sum_{j=1}^n \bm{A}^{n-j}\bm{B}\bm{u}_{k+j-1}
\end{aligned}
{{< /katex >}}
přičemž jeho výstupy nabývají hodnot
{{< katex display >}}
\bm{y}_{k+n} = \bm{C}\bm{A}^n\bm{x}_k + \sum_{j=1}^n \bm{C}\bm{A}^{n-j}\bm{B}\bm{u}_{k+j}
{{< /katex >}}

---

Výstupy {{< katex >}} \bm{y}_i \,,\; i = k+1,\ldots,k+N {{< /katex >}} můžeme seřadit do vektoru
{{< katex display >}}
\bm{Y} = \bm{f} + \bm{G}\bm{U}
{{< /katex >}}
kde
{{< katex display >}}
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
{{< /katex >}}

---

Pro celý horizont můžeme utvořit kvadratické kritérium optimality
{{< katex display >}}
J = (\bm{W}-\bm{Y})^T \bm{Q} (\bm{W}-\bm{Y}) + \bm{U}^T\bm{R}\bm{U}
{{< /katex >}}
kde {{< katex >}} \bm{Q} {{< /katex >}} a {{< katex >}} \bm{R} {{< /katex >}} jsou váhové matice a {{< katex >}} \bm{W} {{< /katex >}} vektor žádaných výstupů
{{< katex display >}}
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
{{< /katex >}}
Po dozazení {{< katex >}} \bm{Y} = \bm{f} + \bm{G}\bm{U} {{< /katex >}} můžeme najít jeho minimum pomocí podmínky
{{< katex display >}}
\frac{∂J}{∂\bm{U}} = \bm{0}
{{< /katex >}}