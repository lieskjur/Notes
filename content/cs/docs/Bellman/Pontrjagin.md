---
title: Pontjaginův princip minima
draft: false
---

Přestože Pontrjaginův princip minima byl odvozen nezávisle v sovětském svazu, je možné jej odvodit z *Bellmanovy diferenciální rovnice* [^1]
{{< katex display >}}
%\left.
-\frac{∂J^*}{∂τ}
%\right|_{τ=t}
=
%\left.
\min_{\bm{u}} \left(
	L
	+
	\frac{∂J}{∂\bm{x}}	
	\bm{f}
\right)
%\right|_{τ=t}
{{< /katex >}}
Základem je zavedení Hamiltoniánu
{{< katex display >}}
H = -\frac{∂J}{∂τ}
{{< /katex >}}
a konjugovaného stavového vektoru
{{< katex display >}}
\bm{p} = \frac{∂J}{∂\bm{x}^T}
{{< /katex >}}

---

Bellmanovu diferenciální rovnici pak můžeme psát jako
{{< katex display >}}
%\left.
H^*
%\right|_{τ=t}
=
%\left.
\min_{\bm{u}} \left(
	L
	+
	\bm{p}^T	
	\bm{f}
\right)
%\right|_{τ=t}
{{< /katex >}}
kde {{< katex >}} H^* {{< /katex >}} je Hamiltonián při dosazení optimálního řízení {{< katex >}} \bm{u}^* {{< /katex >}} které jej minimalizuje
{{< katex display >}}
\bm{u}^* = \argmin_{\bm{u}} H
{{< /katex >}}

---

Samotný Hamiltonián lze vyjádřit jako obsah závroky
{{< katex display >}}
H = L + \bm{p}^T	\bm{f}
{{< /katex >}}
a z něj odvodit stavové rovnice
{{< katex display >}}
\dot{\bm{x}} = \frac{∂H}{∂\bm{p}^T}
\qquad 
\dot{\bm{p}} = -\frac{∂H}{∂\bm{x}^T}
{{< /katex >}}
kde je využito že vektor {{< katex >}} \bm{p} {{< /katex >}} je stavový vektor (závislý pouze na {{< katex >}} τ {{< /katex >}}) a tedy platí
{{< katex display >}}
\frac{d\bm{p}}{dτ} = \frac{∂\bm{p}}{∂τ} = \frac{∂^2J}{∂τ ∂\bm{x}^T} = -\frac{∂H}{∂\bm{x}^T}
{{< /katex >}}

[^1]: [Belmannův princip optimality]({{< ref "Bellman.md" >}})