---
title: Bellmanův princip optimality
draft: false
---

# Bellmanův princip optimality

Pro systému se stavovou zpětnou vazbou ve tvaru
{{< katex display >}}
\frac{d\bm{x}}{dτ} = \bm{f}(\bm{x},\bm{u},τ)
{{< /katex >}}
kde {{< katex >}} \bm{x} = \bm{x}(τ) \,,\; \bm{u} = \bm{u}(\bm{x}(τ)) {{< /katex >}} <!-- dále jen {{< katex >}} \bm{\dot{x}} = \bm{f}(\bm{x},\bm{u},τ) {{< /katex >}} -->
můžeme definovat pro trajektorii ze stavu {{< katex >}} \bm{x}(t_0) = \bm{x}_0 {{< /katex >}} do stavu {{< katex >}} \bm{x}(t_1) {{< /katex >}} kritérium optimality
{{< katex display >}}
J(\bm{x}_0,t_0) = ∫_{t_0}^{t_1} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}
Pro libovolný stav {{< katex >}} \bm{x}(t)=\bm{x}_t {{< /katex >}} existuje optimální řízení {{< katex >}} \bm{u}^* = \bm{u}^*(\bm{x}_t,τ) {{< /katex >}} do koncového stavu {{< katex >}} \bm{x}(t_1) {{< /katex >}}
{{< katex display >}}
\bm{u}^* = \argmin_{\bm{u}} ∫_{t}^{t_1} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}
kde *Bellmanovou funkcí* budeme nazýváme kritérium optimality ze stavu {{< katex >}} \bm{x}(t)=\bm{x}_t {{< /katex >}} do koncového stavu {{< katex >}} \bm{x}(t_1) {{< /katex >}}, při optimálním řízení
{{< katex display >}}
J^*(\bm{x}_t,t) = \min_{\bm{u}} ∫_{t}^{t_1} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}

---

Pokud hledáme optimální řízení v bodě {{< katex >}} \bm{x}(t) = \bm{x}_t {{< /katex >}} můžeme rozdělit celou trajektorii na tři úseky:

1. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t_0,t) {{< /katex >}} který byl už absolvován
2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{< /katex >}} s kritériem optimality {{< katex >}} \int_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ {{< /katex >}}
3. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,t_1⟩ {{< /katex >}} s kritérium optimality {{< katex >}} J(\bm{x}_{t+Δt},t+Δt) {{< /katex >}}

![trajektorie](/Trajektorie.png)

S definovanými úseky můžeme Bellmanovu funkci rozepsat do tvaru tzv. *Bellmanovy rovnice*
{{< katex display >}}
J^*(\bm{x}_t,t) = \min_{\bm{u}} \left( \int_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ + J(\bm{x}_{t+Δt},t+Δt) \right)
{{< /katex >}}
kde <!-- {{< katex >}} \bm{x}_{t+Δt} = \bm{x}(t+Δt) {{< /katex >}} a -->
{{< katex display >}}
J(\bm{x}_{t+Δt},t+Δt)
=
J(\bm{x}_t,t)
+
∫_{t}^{t+Δt} \frac{dJ(\bm{x}_t,t)}{dτ} dτ
{{< /katex >}}
Dosazením pak získáme
{{< katex display >}}
J^*(\bm{x}_t,t)
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L(\bm{x},\bm{u},τ)\,dτ
	+
	J(\bm{x}_t,t)
	+
	∫_{t}^{t+Δt} \frac{dJ(\bm{x}_t,t)}{dτ} dτ
\right)
{{< /katex >}}

---
Jelikož platí
{{< katex display >}}
J^*(\bm{x}_t,t) = \min_{\bm{u}} \left( J(\bm{x}_t,t) \right)
{{< /katex >}}
člen {{< katex >}} J(\bm{x}_t,t) {{< /katex >}} můžeme vykrátit s levou stranou
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L(\bm{x},\bm{u},τ)
	+
    \frac{dJ(\bm{x}_t,t)}{dτ} \ dτ
\right)
{{< /katex >}}
a provést úpravu
{{< katex display >}}
\frac{dJ(\bm{x}_t,t)}{dτ}
=
\frac{∂J(\bm{x}_t,t)}{∂\bm{x}(τ)} \bm{f}(\bm{x},\bm{u},τ)
+
\frac{∂J(\bm{x}_t,t)}{∂τ}
{{< /katex >}}
Výsledkem jejího dosazení je rovnice
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
∫_t^{t+Δt}
L(\bm{x},\bm{u},τ) + \frac{∂J(\bm{x}_t,t)}{∂\bm{x}}\bm{f}(\bm{x},\bm{u},τ) + \frac{∂J(\bm{x}_t,t)}{∂τ}
\ dτ
\right)
{{< /katex >}}

---
Pokud pro {{< katex >}} Δt→0 {{< /katex >}} approximujeme integrál pomocí Reimannova součtu
{{< katex display >}}
0
=
\left.
\min_{\bm{u}} \left(
\left(
L(\bm{x},\bm{u},τ) + \frac{∂J(\bm{x}_t,t)}{∂\bm{x}}\bm{f}(\bm{x},\bm{u},τ) + \frac{∂J(\bm{x}_t,t)}{∂τ}
\right)
Δt
\right)
\right|_{τ=t}
{{< /katex >}}
člen {{< katex >}} Δt {{< /katex >}} lze vykrátit rovnici upravit do tvaru tzv. *Bellmanovy diferenciální rovnice*
{{< katex display >}}
\left. -\frac{∂J^*(\bm{x}_t,t)}{∂τ} \right|_{τ=t}
=
\left.
\min_{\bm{u}} \left(
	L(\bm{x},\bm{u},τ)
	+
	\frac{∂J(\bm{x}_t,t)}{∂\bm{x}}	
	\bm{f}(\bm{x},\bm{u},τ)
\right)
\right|_{τ=t}
{{< /katex >}}
z které lze přímo odvodit [LQR]({{< ref "LQR.md" >}}) a s úpravou, Pontrjaginův princip minima.