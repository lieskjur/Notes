---
title: Bellmanův princip optimality
draft: false
---

# Bellmanův princip optimality

Pro dynamický systém se stavovou zpětnou vazbou ve tvaru
{{< katex display >}}
\dot{\bm{x}} = \bm{f}(\bm{x},\bm{u},τ) \;,\quad \bm{u} = \bm{u}(\bm{x})
{{< /katex >}}
kde {{< katex >}} \bm{x}(τ) {{< /katex >}} jsou stavy systému a {{< katex >}} \bm{u}(\bm{x}) {{< /katex >}}  funkce vstupů ze zpětnou vazbou, můžeme definovat pro trajektorii ze stavu {{< katex >}} \bm{x}(t) {{< /katex >}} do stavu {{< katex >}} \bm{x}(T) {{< /katex >}} kritérium optimality
{{< katex display >}}
J_{t→T} = ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}

---

Pro libovolný stav {{< katex >}} \bm{x}(\tau) {{< /katex >}} pak existuje optimální řízení {{< katex >}} \bm{u}^*(τ) {{< /katex >}} pro dosažení žádaného stavu v čase {{< katex >}} T {{< /katex >}}
{{< katex display >}}
\bm{u}^* = \argmin_{\bm{u}} J_{t→T}
{{< /katex >}}
kde *Bellmanovou funkcí* budeme nazýváme kritérium optimality při optimálním řízení
{{< katex display >}}
J_{t→T}^* = \min_{\bm{u}} J_{t→T}
{{< /katex >}}

## Bellmanova rovnice

Pokud hledáme optimální řízení ve stavu {{< katex >}} \bm{x}(t) {{< /katex >}}, můžeme rozdělit celou trajektorii na dva úseky:

1. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{< /katex >}} s kritériem optimality {{< katex >}} \int_t^{t+Δt} L\,dτ {{< /katex >}}
2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,T⟩ {{< /katex >}} s kritériem optimality {{< katex >}} J_{t+Δt→T} {{< /katex >}}

![trajektorie](/Trajektorie.png)

S definovanými úseky můžeme Bellmanovu funkci rozepsat do tvaru tzv. *Bellmanovy rovnice*
{{< katex display >}}
J_{t→T}^* = \min_{\bm{u}} \left( \int_t^{t+Δt} L\,dτ + J_{t+Δt→T} \right)
{{< /katex >}}

## Bellmanova diferenciání rovnice

Člen {{< katex >}} J_{t+Δt→T} {{< /katex >}} můžeme rozepsat jako
{{< katex display >}}
J_{t+Δt→T}
=
J_{t→T}
+
∫_{t}^{t+Δt} \frac{dJ_{t→T}}{dτ} dτ
{{< /katex >}}
kdy dosazením získáme
{{< katex display >}}
J_{t→T}^*
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L\,dτ
	+
	J_{t→T}
	+
	∫_{t}^{t+Δt} \frac{dJ_{t→T}}{dτ} dτ
\right)
{{< /katex >}}
Jelikož platí
{{< katex display >}}
J_{t→T}^* = \min_{\bm{u}} \left( J_{t→T} \right)
{{< /katex >}}
člen {{< katex >}} J_{t→T} {{< /katex >}} můžeme vykrátit s levou stranou
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt}
	L +
    \frac{dJ_{t→T}}{dτ}
    \ dτ
\right)
{{< /katex >}}
a provést úpravu
{{< katex display >}}
\frac{dJ_{t→T}}{dτ}
=
\frac{∂J_{t→T}}{∂\bm{x}} \bm{f}
+
\frac{∂J_{t→T}}{∂τ}
{{< /katex >}}
Výsledkem jejího dosazení je rovnice
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
∫_t^{t+Δt}
L + \frac{∂J_{t→T}}{∂\bm{x}}\bm{f} + \frac{∂J_{t→T}}{∂τ}
\ dτ
\right)
{{< /katex >}}

---

Pokud {{< katex >}} Δt→0 {{< /katex >}}, můžeme aproximovat integrál pomocí Reimannova součtu a výslednou rovnici upravit do obecného tvaru (nezávislého na mezích kritéria optimality) tzv. *Bellmanovy diferenciální rovnice*
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
vyjádřené v čase {{< katex >}} τ = t {{< /katex >}}
, ze které lze přímo odvodit [LQR]({{< ref "LQR.md" >}}) a s úpravou, [Pontrjaginův princip minima]({{< ref "Pontrjagin.md" >}}).