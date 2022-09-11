---
title: Bellmanův princip optimality
draft: false
---

# Bellmanův princip optimality

Pro dynamický systém se stavovou zpětnou vazbou ve tvaru
{{< katex display >}}
\dot{\bm{x}} = \bm{f}(\bm{x},\bm{u},τ) \;,\quad \bm{u} = \bm{u}(\bm{x})
{{< /katex >}}
kde {{< katex >}} \bm{x} = \bm{x}(τ) {{< /katex >}}, můžeme definovat pro trajektorii ze stavu {{< katex >}} \bm{x}(t) {{< /katex >}} do stavu {{< katex >}} \bm{x}(T) {{< /katex >}} kritérium optimality
{{< katex display >}}
J(t) = ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}
Pro libovolný stav {{< katex >}} \bm{x}(\tau) {{< /katex >}} pak existuje optimální řízení {{< katex >}} \bm{u}^*(τ) {{< /katex >}} pro dosažení žádaného stavu v čase {{< katex >}} T {{< /katex >}}
{{< katex display >}}
\bm{u}^* = \argmin_{\bm{u}} ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}
kde *Bellmanovou funkcí* budeme nazýváme kritérium optimality při optimálním řízení
{{< katex display >}}
J^*(t) = \min_{\bm{u}} ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}

## Bellmanova rovnice

Pokud hledáme optimální řízení ve stavu {{< katex >}} \bm{x}(t) {{< /katex >}}, můžeme rozdělit celou trajektorii na dva úseky:

1. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{< /katex >}} s kritériem optimality {{< katex >}} \int_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ {{< /katex >}}
2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,T⟩ {{< /katex >}} s kritérium optimality {{< katex >}} J(t+Δt) {{< /katex >}}

![trajektorie](/Trajektorie.png)

S definovanými úseky můžeme Bellmanovu funkci rozepsat do tvaru tzv. *Bellmanovy rovnice*
{{< katex display >}}
J^*(t) = \min_{\bm{u}} \left( \int_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ + J(t+Δt) \right)
{{< /katex >}}

## Bellmanova diferenciání rovnice

člen {{< katex >}} J(t+Δt) {{< /katex >}} můžeme rozepsat jako
{{< katex display >}}
J(t+Δt)
=
J(t)
+
∫_{t}^{t+Δt} \frac{dJ(t)}{dτ} dτ
{{< /katex >}}
kdy osazením získáme
{{< katex display >}}
J^*(t)
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ
	+
	J(t)
	+
	∫_{t}^{t+Δt} \frac{dJ(t)}{dτ} dτ
\right)
{{< /katex >}}
Jelikož platí
{{< katex display >}}
J^*(t) = \min_{\bm{u}} \left( J(t) \right)
{{< /katex >}}
člen {{< katex >}} J(t) {{< /katex >}} můžeme vykrátit s levou stranou
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt}
	L(\bm{x},\bm{u},τ) +
    \frac{dJ(t)}{dτ}
    \ dτ
\right)
{{< /katex >}}
a provést úpravu
{{< katex display >}}
\frac{dJ(t)}{dτ}
=
\frac{∂J(t)}{∂\bm{x}(τ)} \bm{f}(\bm{x},\bm{u},τ)
+
\frac{∂J(t)}{∂τ}
{{< /katex >}}
Výsledkem jejího dosazení je rovnice
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
∫_t^{t+Δt}
L(\bm{x},\bm{u},τ) + \frac{∂J(t)}{∂\bm{x}}\bm{f}(\bm{x},\bm{u},τ) + \frac{∂J(t)}{∂τ}
\ dτ
\right)
{{< /katex >}}

---

Pokud {{< katex >}} Δt→0 {{< /katex >}}, můžeme aproximovat integrál pomocí Reimannova součtu a výslednou rovnici upravit do tvaru tzv. *Bellmanovy diferenciální rovnice*
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
vyjádřené v čase {{< katex >}} τ = t {{< /katex >}}
, ze které lze přímo odvodit [LQR]({{< ref "LQR.md" >}}) a s úpravou, Pontrjaginův princip minima.