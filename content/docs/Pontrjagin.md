---
title: Pontjaginův princip minima
draft: false
---

Přestože Pontrjaginův princip minima byl odvozen nezávisle v sovětském svazu, je možné jej odvodit z *Bellmanovy diferenciální rovnice* [^1]
{{< katex display >}}
%\left.
-\frac{∂J^*(t)}{∂τ}
%\right|_{τ=t}
=
%\left.
\min_{\bm{u}} \left(
	L(\bm{x},\bm{u},τ)
	+
	\frac{∂J(t)}{∂\bm{x}}	
	\bm{f}(\bm{x},\bm{u},τ)
\right)
%\right|_{τ=t}
{{< /katex >}}
Základem je zavedení Hamiltoniánu
{{< katex display >}}
H(t) = -\frac{∂J(t)}{∂τ}
{{< /katex >}}
a konjugovaného stavového vektoru
{{< katex display >}}
\bm{p}(τ) = \frac{∂J(t)}{∂\bm{x}^T}
{{< /katex >}}

---

Bellmanovu diferenciální rovnici pak můžeme psát jako
{{< katex display >}}
%\left.
H^*(t)
%\right|_{τ=t}
=
%\left.
\min_{\bm{u}} \left(
	L(\bm{x},\bm{u},τ)
	+
	\bm{p}^T	
	\bm{f}(\bm{x},\bm{u},τ)
\right)
%\right|_{τ=t}
{{< /katex >}}
kde {{< katex >}} H^*(t) {{< /katex >}} je Hamiltonián při dosazení optimálního řízení {{< katex >}} \bm{u}^* {{< /katex >}} které jej minimalizuje
{{< katex display >}}
\bm{u}^* = \argmin_{\bm{u}} H(t)
{{< /katex >}}

---

Samotný Hamiltonián lze vyjádřit jako obsah závroky
{{< katex display >}}
H(t) = L(\bm{x},\bm{u},τ) + \bm{p}(τ)^T	\bm{f}(\bm{x},\bm{u},τ)
{{< /katex >}}
a z něj odvodit stavové rovnice
{{< katex display >}}
\dot{\bm{x}} = \frac{∂H(t)}{∂\bm{p}^T}
\qquad 
\dot{\bm{p}} = \frac{∂H(t)}{∂\bm{x}^T}
{{< /katex >}}
kde je využito že vektor {{< katex >}} \bm{p}(τ) {{< /katex >}} je stavový vektor (závislý pouze na {{< katex >}} τ {{< /katex >}}) a tedy platí
{{< katex display >}}
\frac{d\bm{p}}{dτ} = \frac{∂\bm{p}}{∂τ} = \frac{∂^2J(t)}{∂τ ∂\bm{x}^T} = \frac{∂H(t)}{∂\bm{x}^T}
{{< /katex >}}

[^1]: [Belmannův princip optimality]({{< ref "Bellman.md" >}})