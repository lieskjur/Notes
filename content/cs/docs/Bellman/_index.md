---
title: Bellmanův princip optimality
draft: false
---

# Bellmanův princip optimality

Pro dynamický systém ve tvaru
{{< katex display >}}
\dot{\bm{x}} = \bm{f}(\bm{x},\bm{u},τ)
{{< /katex >}}
kde {{< katex >}} \bm{x}(τ) {{< /katex >}} jsou stavy systému a {{< katex >}} \bm{u} {{< /katex >}} vstupy, můžeme definovat pro trajektorii ze stavu {{< katex >}} \bm{x}(t) {{< /katex >}} do stavu {{< katex >}} \bm{x}(T) {{< /katex >}} kritérium optimality
{{< katex display >}}
J_{⟨t,T⟩}(\bm{u},τ) = ∫_{t}^{T} L(\bm{x},\bm{u},τ)\,dτ
{{< /katex >}}
Také můzeme definovat tzv. *cenou do cíle* {{< katex >}} J^*_{⟨t,T⟩}(τ) {{< /katex >}} pro zpětnovazební řízení {{< katex >}} \bm{u}(\bm{x}(τ)) {{< /katex >}}.

---

Pak musí existovat minimalizující zpětnovazební řízení {{< katex >}} \bm{u}_\text{opt} {{< /katex >}}
{{< katex display >}}
\bm{u}_\text{opt} = \argmin_{\bm{u}} J^*_{⟨t,T⟩}
{{< /katex >}}
které budeme nazývat optimálním. *Bellmanovou funkcí* nazýváme cenu do cíle při optimálním řízení
{{< katex display >}}
V_{⟨t,T⟩} = \min_{\bm{u}} J^*_{⟨t,T⟩}
{{< /katex >}}

## Bellmanova rovnice

Pokud hledáme optimální řízení ve stavu {{< katex >}} \bm{x}(t) {{< /katex >}}, můžeme rozdělit celou trajektorii na dva úseky:

1. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t,t+Δt) {{< /katex >}} s kritériem optimality {{< katex >}} \int_t^{t+Δt} L\,dτ {{< /katex >}}
2. {{< katex >}} \bm{x}(τ) \,,\; τ ∈ ⟨t+Δt,T⟩ {{< /katex >}} s cenou do cíle {{< katex >}} J^*_{⟨t+Δt,T⟩} {{< /katex >}}

![trajektorie](trajektorie.png)

S definovanými úseky můžeme Bellmanovu funkci rozepsat do tvaru tzv. *Bellmanovy rovnice*
{{< katex display >}}
V_{⟨t,T⟩} = \min_{\bm{u}} \left( \int_t^{t+Δt} L\,dτ + J^*_{⟨t+Δt,T⟩} \right)
{{< /katex >}}

## Bellmanova diferenciání rovnice

Člen {{< katex >}} J_{⟨t+Δt,T⟩} {{< /katex >}} můžeme rozepsat jako
{{< katex display >}}
J^*_{⟨t+Δt,T⟩}
=
J^*_{⟨t,T⟩}
+
∫_{t}^{t+Δt} \frac{dJ^*}{dτ} dτ
{{< /katex >}}
kdy dosazením získáme
{{< katex display >}}
V_{⟨t,T⟩}
=
\min_{\bm{u}} \left(
	∫_t^{t+Δt} L\,dτ
	+
	J^*_{⟨t,T⟩}
	+
	∫_{t}^{t+Δt} \frac{dJ^*}{dτ} dτ
\right)
{{< /katex >}}
Jelikož platí
{{< katex display >}}
V_{⟨t,T⟩} = \min_{\bm{u}} \left( J^*_{⟨t,T⟩} \right)
{{< /katex >}}
člen {{< katex >}} J^*_{⟨t,T⟩} {{< /katex >}} můžeme vykrátit s levou stranou a dále provést úpravu
{{< katex display >}}
\frac{dJ^*}{dτ}
=
\frac{∂J^*}{∂\bm{x}} \bm{f}
+
\frac{∂J^*}{∂τ}
{{< /katex >}}
Výsledkem je po-té rovnice
{{< katex display >}}
0
=
\min_{\bm{u}} \left(
∫_t^{t+Δt}
\left(
L + \frac{∂J^*}{∂\bm{x}}\bm{f} + \frac{∂J^*}{∂τ}
\right)
\ dτ
\right)
{{< /katex >}}

---

Pokud {{< katex >}} Δt→0 {{< /katex >}}, můžeme aproximovat integrál pomocí Reimannova součtu a výslednou rovnici upravit do tvaru tzv. *Bellmanovy diferenciální rovnice*
{{< katex display >}}
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
{{< /katex >}}
vyjádřené v čase {{< katex >}} τ = t {{< /katex >}}, kde předpokládáme, že člen {{< katex >}} \frac{∂J^*}{∂τ} {{< /katex >}} je nezávislý na {{< katex >}} \bm{u} {{< /katex >}}. Z ní lze přímo odvodit [LQR]({{< ref "LQR.md" >}}) a s úpravou, [Pontrjaginův princip minima]({{< ref "Pontrjagin.md" >}}).