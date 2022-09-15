---
title: Pontjaginův princip minima
draft: false
---

Přestože Pontrjaginův princip minima byl odvozen nezávisle v sovětském svazu, je možné jej odvodit z *Bellmanovy diferenciální rovnice* [^1]
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
Základem je zavedení Hamiltoniánu
{{< k display >}}
H = -\frac{∂J^*}{∂τ}
{{< /k >}}
a konjugovaného stavového vektoru
{{< k display >}}
\bm{p} = \frac{∂J^*}{∂\bm{x}^T}
{{< /k >}}

---

Bellmanovu diferenciální rovnici pak můžeme psát jako
{{< k display >}}
%\left.
H
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
{{< /k >}}
kde {{<k>}} H {{</k>}} je Hamiltonián při dosazení optimálního řízení {{<k>}} \bm{u}_\text{opt} {{</k>}} které jej minimalizuje
{{< k display >}}
\bm{u}_\text{opt} = \argmin_{\bm{u}} H
{{< /k >}}

---

Samotný Hamiltonián lze vyjádřit jako obsah závroky
{{< k display >}}
H = L + \bm{p}^T	\bm{f}
{{< /k >}}
a z něj odvodit stavové rovnice
{{< k display >}}
\dot{\bm{x}} = \frac{∂H}{∂\bm{p}^T}
\qquad 
\dot{\bm{p}} = -\frac{∂H}{∂\bm{x}^T}
{{< /k >}}
kde je využito že vektor {{<k>}} \bm{p} {{</k>}} je stavový vektor (závislý pouze na {{<k>}} τ {{</k>}}) a tedy platí
{{< k display >}}
\frac{d\bm{p}}{dτ} = \frac{∂\bm{p}}{∂τ} = \frac{∂^2J^*}{∂τ ∂\bm{x}^T} = -\frac{∂H}{∂\bm{x}^T}
{{< /k >}}

[^1]: [Belmannův princip optimality]({{< ref "Bellman.md" >}})