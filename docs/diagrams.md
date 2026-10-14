# 📊 Key Diagrams — ECMT5001 Econometrics

*Core econometrics diagrams for quick reference and exam revision. All diagrams are inline SVG — zoom in on any device.*

---

## 1. OLS Scatter Plot and Fitted Line

*The fundamental picture of OLS regression: minimising the sum of squared vertical distances from each point to the fitted line.*

<div style="overflow-x: auto; margin: 1rem 0;">
<svg viewBox="0 0 760 400" width="100%" xmlns="http://www.w3.org/2000/svg">
  <style>
    .ax { stroke: #333; stroke-width: 2; fill: none; }
    .lbl { font: 14px Arial, sans-serif; fill: #333; }
    .title { font: 15px Arial, sans-serif; font-weight: 700; fill: #222; }
    .formula { font: 13px Arial, sans-serif; fill: #1a5276; font-style: italic; }
    .note { font: 12px Arial, sans-serif; fill: #666; }
  </style>
  <!-- Axes -->
  <line x1="80" y1="340" x2="700" y2="340" class="ax"/>
  <line x1="80" y1="340" x2="80" y2="40" class="ax"/>
  <!-- Arrowheads -->
  <polygon points="700,340 690,335 690,345" fill="#333"/>
  <polygon points="80,40 75,50 85,50" fill="#333"/>
  <!-- Axis labels -->
  <text x="700" y="360" class="lbl">x</text>
  <text x="55" y="40" class="lbl">y</text>
  <!-- Fitted line: y = 40 + 0.55x (in SVG coords) -->
  <!-- SVG coords: x from 100 to 680, y inverted (340=bottom) -->
  <!-- Fitted line through (100, 285) to (670, 95) -->
  <line x1="100" y1="285" x2="670" y2="95" stroke="#1a5276" stroke-width="2.5"/>
  <!-- Scatter points (x_svg, y_svg) -->
  <!-- Points: (130,265),(170,250),(220,230),(260,200),(300,210),(340,175),(390,160),(430,150),(480,130),(530,110),(580,95),(630,80) -->
  <circle cx="130" cy="265" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="170" cy="240" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="220" cy="255" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="260" cy="195" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="300" cy="220" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="340" cy="160" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="390" cy="175" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="430" cy="145" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="480" cy="130" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="530" cy="105" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="580" cy="110" r="6" fill="#e74c3c" opacity="0.85"/>
  <circle cx="630" cy="75" r="6" fill="#e74c3c" opacity="0.85"/>
  <!-- Residual lines (vertical dashed from point to fitted line) -->
  <!-- For point (340,160): fitted y at x=340 is 285 - (340-100)*(285-95)/(670-100) = 285 - 240*(190/570) = 285 - 80 = 205 -->
  <!-- For point (430,145): fitted y ≈ 285 - (430-100)*190/570 = 285 - 110 = 175 -->
  <!-- Show 3 representative residuals -->
  <line x1="220" y1="255" x2="220" y2="237" stroke="#27ae60" stroke-width="1.5" stroke-dasharray="4,3"/>
  <line x1="430" y1="145" x2="430" y2="172" stroke="#27ae60" stroke-width="1.5" stroke-dasharray="4,3"/>
  <line x1="530" y1="105" x2="530" y2="126" stroke="#27ae60" stroke-width="1.5" stroke-dasharray="4,3"/>
  <!-- Label residual -->
  <text x="435" y="160" class="note" fill="#27ae60">ûᵢ = yᵢ − ŷᵢ</text>
  <!-- Fitted line label -->
  <text x="490" y="85" class="formula">ŷ = β̂₀ + β̂₁x</text>
  <!-- Axis tick labels -->
  <text x="60" y="344" class="lbl">0</text>
  <text x="660" y="360" class="lbl">x (regressor)</text>
  <text x="18" y="200" class="lbl" transform="rotate(-90,35,200)">y (outcome)</text>
  <!-- Title -->
  <text x="380" y="25" class="title" text-anchor="middle">OLS: Minimising Sum of Squared Residuals</text>
  <!-- Legend -->
  <circle cx="105" cy="375" r="5" fill="#e74c3c"/>
  <text x="115" y="379" class="note">Data points (xᵢ, yᵢ)</text>
  <line x1="230" y1="375" x2="260" y2="375" stroke="#1a5276" stroke-width="2.5"/>
  <text x="265" y="379" class="note">Fitted line ŷ = β̂₀ + β̂₁x</text>
  <line x1="400" y1="375" x2="430" y2="375" stroke="#27ae60" stroke-width="1.5" stroke-dasharray="4,3"/>
  <text x="435" y="379" class="note">Residuals ûᵢ</text>
</svg>
</div>

**Key facts:**
- OLS chooses $\hat{\beta}_0, \hat{\beta}_1$ to minimise $\sum_{i=1}^n \hat{u}_i^2$
- Residuals $\hat{u}_i = y_i - \hat{y}_i$ are the vertical distances (not perpendicular)
- The line always passes through $(\bar{x}, \bar{y})$; residuals sum to zero

---

## 2. SST = SSE + SSR Decomposition

*Total variation in y is decomposed into explained (SSE) and unexplained (SSR) parts. R² = SSE/SST.*

<div style="overflow-x: auto; margin: 1rem 0;">
<svg viewBox="0 0 760 380" width="100%" xmlns="http://www.w3.org/2000/svg">
  <style>
    .ax { stroke: #333; stroke-width: 2; fill: none; }
    .lbl { font: 13px Arial, sans-serif; fill: #333; }
    .title { font: 15px Arial, sans-serif; font-weight: 700; fill: #222; }
  </style>
  <!-- Axes -->
  <line x1="100" y1="320" x2="680" y2="320" class="ax"/>
  <line x1="100" y1="320" x2="100" y2="50" class="ax"/>
  <!-- Fitted line -->
  <line x1="130" y1="280" x2="660" y2="110" stroke="#1a5276" stroke-width="2"/>
  <!-- Mean line ȳ -->
  <line x1="100" y1="200" x2="680" y2="200" stroke="#888" stroke-width="1.5" stroke-dasharray="8,5"/>
  <text x="685" y="204" style="font:12px Arial;fill:#888">ȳ</text>
  <!-- Pick one observation point -->
  <!-- Point at x=380, y_actual=120, y_fitted≈185, y_bar=200 -->
  <circle cx="380" cy="120" r="7" fill="#e74c3c"/>
  <!-- SST bar: from yᵢ to ȳ (120 to 200) — total deviation -->
  <line x1="380" y1="120" x2="380" y2="200" stroke="#8e44ad" stroke-width="4"/>
  <!-- SSE bar: from ŷᵢ to ȳ (185 to 200) — explained -->
  <line x1="360" y1="185" x2="360" y2="200" stroke="#27ae60" stroke-width="4"/>
  <!-- SSR bar: from yᵢ to ŷᵢ (120 to 185) — residual -->
  <line x1="400" y1="120" x2="400" y2="185" stroke="#e67e22" stroke-width="4"/>
  <!-- Fitted value dot on line -->
  <circle cx="380" cy="185" r="5" fill="#1a5276"/>
  <line x1="360" y1="185" x2="400" y2="185" stroke="#1a5276" stroke-width="1" stroke-dasharray="3,2"/>
  <!-- Labels -->
  <text x="408" y="155" style="font:12px Arial;fill:#e67e22;font-weight:700">SSR (residual)</text>
  <text x="408" y="168" style="font:11px Arial;fill:#e67e22">= (yᵢ − ŷᵢ)²</text>
  <text x="270" y="193" style="font:12px Arial;fill:#27ae60;font-weight:700">SSE (explained)</text>
  <text x="270" y="206" style="font:11px Arial;fill:#27ae60">= (ŷᵢ − ȳ)²</text>
  <text x="330" y="140" style="font:12px Arial;fill:#8e44ad;font-weight:700">SST (total)</text>
  <text x="325" y="153" style="font:11px Arial;fill:#8e44ad">= (yᵢ − ȳ)²</text>
  <!-- yᵢ label -->
  <text x="386" y="116" style="font:12px Arial;fill:#e74c3c">yᵢ</text>
  <!-- ŷᵢ label -->
  <text x="362" y="180" style="font:12px Arial;fill:#1a5276">ŷᵢ</text>
  <!-- Axis labels -->
  <text x="680" y="336" class="lbl">x</text>
  <text x="75" y="52" class="lbl">y</text>
  <!-- Formula box -->
  <rect x="120" y="340" width="500" height="30" fill="#eaf2f8" rx="5"/>
  <text x="370" y="360" text-anchor="middle" style="font:13px Arial;fill:#1a5276;font-weight:700">SST = SSE + SSR  →  R² = SSE/SST = 1 − SSR/SST</text>
  <!-- Title -->
  <text x="380" y="30" class="title" text-anchor="middle">SST = SSE + SSR Decomposition</text>
</svg>
</div>

| Quantity | Formula | Meaning |
|---|---|---|
| $\text{SST}$ | $\sum(y_i - \bar{y})^2$ | Total variation in $y$ |
| $\text{SSE}$ | $\sum(\hat{y}_i - \bar{y})^2$ | Variation **explained** by the regression |
| $\text{SSR}$ | $\sum \hat{u}_i^2 = \sum(y_i - \hat{y}_i)^2$ | **Residual** (unexplained) variation |
| $R^2$ | $\text{SSE}/\text{SST} = 1 - \text{SSR}/\text{SST}$ | Proportion of variance explained |

---

## 3. Omitted Variable Bias — Direction Table

*The sign and magnitude of OVB depends on two things: the correlation between the omitted and included variable, and the sign of the omitted variable's true coefficient.*

**OVB formula:** $\tilde{\beta}_1 = \beta_1 + \underbrace{\beta_2 \cdot \delta_{12}}_{\text{bias}}$ where $\delta_{12} = \text{Cov}(x_2, x_1)/\text{Var}(x_1)$

| | **Omitted has positive effect ($\beta_2 > 0$)** | **Omitted has negative effect ($\beta_2 < 0$)** |
|---|---|---|
| **Omitted correlated positively with $x_1$** ($\delta_{12} > 0$) | ⬆️ **Upward bias** — $\tilde{\beta}_1 > \beta_1$ | ⬇️ **Downward bias** — $\tilde{\beta}_1 < \beta_1$ |
| **Omitted correlated negatively with $x_1$** ($\delta_{12} < 0$) | ⬇️ **Downward bias** — $\tilde{\beta}_1 < \beta_1$ | ⬆️ **Upward bias** — $\tilde{\beta}_1 > \beta_1$ |

!!! example "Classic OVB example"
    Regressing wages on education only, omitting ability:

    - Ability raises wages → $\beta_2 > 0$
    - Ability is positively correlated with education → $\delta_{12} > 0$
    - **Bias = upward**: the estimated return to education is overstated because it partly captures the return to unobserved ability.

---

## 4. Heteroskedasticity: Residual Plots

*Left panel: homoskedastic (constant variance — OLS valid). Right panel: heteroskedastic (fan pattern — OLS SEs biased).*

<div style="overflow-x: auto; margin: 1rem 0;">
<svg viewBox="0 0 760 320" width="100%" xmlns="http://www.w3.org/2000/svg">
  <style>
    .ax { stroke: #555; stroke-width: 1.5; fill: none; }
    .panel { font: 14px Arial, sans-serif; fill: #fff; font-weight: 700; }
    .lbl { font: 12px Arial, sans-serif; fill: #333; }
    .cap { font: 13px Arial, sans-serif; font-weight: 700; }
  </style>
  <!-- LEFT PANEL: Homoskedastic -->
  <rect x="20" y="20" width="345" height="280" rx="8" fill="#f8f9fa" stroke="#ddd" stroke-width="1"/>
  <!-- Panel label -->
  <rect x="20" y="20" width="345" height="30" rx="8" fill="#27ae60"/>
  <text x="192" y="40" class="panel" text-anchor="middle">Homoskedastic (MLR.5 holds) ✓</text>
  <!-- Axes -->
  <line x1="60" y1="240" x2="340" y2="240" class="ax"/>
  <line x1="60" y1="60" x2="60" y2="250" class="ax"/>
  <!-- Zero line -->
  <line x1="60" y1="155" x2="340" y2="155" stroke="#aaa" stroke-width="1" stroke-dasharray="5,4"/>
  <!-- Axis labels -->
  <text x="340" y="260" class="lbl">ŷ (fitted values)</text>
  <text x="30" y="100" class="lbl" transform="rotate(-90,40,155)">Residual û</text>
  <!-- Scatter: random pattern, constant spread -->
  <circle cx="80" cy="130" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="100" cy="175" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="120" cy="145" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="140" cy="165" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="160" cy="135" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="180" cy="170" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="200" cy="140" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="220" cy="160" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="240" cy="145" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="260" cy="168" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="280" cy="138" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="300" cy="172" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="320" cy="148" r="4" fill="#e74c3c" opacity="0.7"/>
  <!-- Band lines showing constant spread -->
  <line x1="65" y1="120" x2="335" y2="120" stroke="#27ae60" stroke-width="1" stroke-dasharray="3,3" opacity="0.5"/>
  <line x1="65" y1="190" x2="335" y2="190" stroke="#27ae60" stroke-width="1" stroke-dasharray="3,3" opacity="0.5"/>
  <text x="192" y="275" class="lbl" text-anchor="middle">Var(û) constant — OLS SEs valid</text>

  <!-- RIGHT PANEL: Heteroskedastic -->
  <rect x="395" y="20" width="345" height="280" rx="8" fill="#f8f9fa" stroke="#ddd" stroke-width="1"/>
  <rect x="395" y="20" width="345" height="30" rx="8" fill="#c0392b"/>
  <text x="568" y="40" class="panel" text-anchor="middle">Heteroskedastic (MLR.5 violated) ✗</text>
  <!-- Axes -->
  <line x1="430" y1="240" x2="715" y2="240" class="ax"/>
  <line x1="430" y1="60" x2="430" y2="250" class="ax"/>
  <!-- Zero line -->
  <line x1="430" y1="155" x2="715" y2="155" stroke="#aaa" stroke-width="1" stroke-dasharray="5,4"/>
  <!-- Axis labels -->
  <text x="715" y="260" class="lbl">ŷ (fitted values)</text>
  <text x="400" y="100" class="lbl" transform="rotate(-90,410,155)">Residual û</text>
  <!-- Scatter: fan pattern, increasing spread -->
  <circle cx="450" cy="152" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="460" cy="148" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="470" cy="158" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="490" cy="140" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="510" cy="168" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="530" cy="125" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="550" cy="182" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="570" cy="108" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="590" cy="195" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="610" cy="90" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="630" cy="210" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="650" cy="78" r="4" fill="#e74c3c" opacity="0.7"/>
  <circle cx="680" cy="215" r="4" fill="#e74c3c" opacity="0.7"/>
  <!-- Fan/funnel boundary lines -->
  <line x1="445" y1="148" x2="700" y2="60" stroke="#c0392b" stroke-width="1" stroke-dasharray="3,3" opacity="0.5"/>
  <line x1="445" y1="162" x2="700" y2="250" stroke="#c0392b" stroke-width="1" stroke-dasharray="3,3" opacity="0.5"/>
  <text x="568" y="275" class="lbl" text-anchor="middle">Var(û) increases with ŷ — fan pattern ⚠️</text>
</svg>
</div>

**What to do when you see heteroskedasticity:**

1. **Formal tests**: Breusch-Pagan (LM = n·R²_aux ~ χ²_k) or White test (more general)
2. **Always report** robust (HC/White) standard errors in applied work
3. If variance function is known: use WLS with weights $w_i = 1/h_i$

---

## 5. Instrumental Variables — Causal Path Diagram

*A valid instrument z must affect y ONLY through x (exclusion restriction), and must be correlated with x (relevance).*

<div style="overflow-x: auto; margin: 1rem 0;">
<svg viewBox="0 0 760 300" width="100%" xmlns="http://www.w3.org/2000/svg">
  <style>
    .box { rx: 8; ry: 8; }
    .node-lbl { font: 16px Arial, sans-serif; font-weight: 700; text-anchor: middle; }
    .edge-lbl { font: 12px Arial, sans-serif; fill: #555; }
    .arrow { fill: #333; }
    .title { font: 15px Arial, sans-serif; font-weight: 700; fill: #222; }
  </style>
  <!-- Nodes -->
  <!-- z (instrument) -->
  <rect x="60" y="110" width="120" height="60" fill="#d5e8d4" stroke="#82b366" stroke-width="2" rx="8"/>
  <text x="120" y="138" class="node-lbl" fill="#1e5631">z</text>
  <text x="120" y="157" style="font:11px Arial;fill:#1e5631;text-anchor:middle">Instrument</text>
  <!-- x (endogenous) -->
  <rect x="300" y="110" width="140" height="60" fill="#dae8fc" stroke="#6c8ebf" stroke-width="2" rx="8"/>
  <text x="370" y="135" class="node-lbl" fill="#1a3a5c">x</text>
  <text x="370" y="154" style="font:11px Arial;fill:#1a3a5c;text-anchor:middle">Endogenous regressor</text>
  <!-- y (outcome) -->
  <rect x="560" y="110" width="140" height="60" fill="#f8cecc" stroke="#b85450" stroke-width="2" rx="8"/>
  <text x="630" y="138" class="node-lbl" fill="#7b1a16">y</text>
  <text x="630" y="157" style="font:11px Arial;fill:#7b1a16;text-anchor:middle">Outcome</text>
  <!-- u (error/confounder) -->
  <rect x="430" y="210" width="120" height="55" fill="#fff2cc" stroke="#d6b656" stroke-width="2" rx="8"/>
  <text x="490" y="234" class="node-lbl" fill="#7d5a00" style="font:15px Arial">u</text>
  <text x="490" y="253" style="font:11px Arial;fill:#7d5a00;text-anchor:middle">Confounder/error</text>
  <!-- Arrow z → x (relevance) -->
  <line x1="180" y1="140" x2="298" y2="140" stroke="#27ae60" stroke-width="2.5" marker-end="url(#green-arrow)"/>
  <text x="238" y="130" class="edge-lbl" fill="#27ae60" text-anchor="middle">Relevance</text>
  <text x="238" y="145" class="edge-lbl" fill="#27ae60" text-anchor="middle">Cov(z,x) ≠ 0</text>
  <!-- Arrow x → y -->
  <line x1="440" y1="140" x2="558" y2="140" stroke="#2980b9" stroke-width="2.5" marker-end="url(#blue-arrow)"/>
  <text x="499" y="130" class="edge-lbl" fill="#2980b9" text-anchor="middle">β₁ (causal)</text>
  <!-- Arrow u → y -->
  <line x1="490" y1="210" x2="617" y2="173" stroke="#e67e22" stroke-width="2" marker-end="url(#orange-arrow)"/>
  <!-- Arrow x ← u (endogeneity) -->
  <line x1="460" y1="213" x2="405" y2="173" stroke="#e67e22" stroke-width="2" marker-end="url(#orange-arrow)"/>
  <text x="425" y="205" class="edge-lbl" fill="#e67e22">Cov(x,u)≠0</text>
  <text x="418" y="218" class="edge-lbl" fill="#e67e22">(endogeneity!)</text>
  <!-- BLOCKED arrow z → y (exclusion restriction) -->
  <line x1="180" y1="132" x2="557" y2="120" stroke="#c0392b" stroke-width="1.5" stroke-dasharray="8,5"/>
  <text x="370" y="108" class="edge-lbl" fill="#c0392b" text-anchor="middle">✗ Exclusion restriction: Cov(z,u) = 0</text>
  <text x="370" y="120" class="edge-lbl" fill="#c0392b" text-anchor="middle">z affects y ONLY through x</text>
  <!-- Arrow marker definitions -->
  <defs>
    <marker id="green-arrow" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="#27ae60"/>
    </marker>
    <marker id="blue-arrow" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="#2980b9"/>
    </marker>
    <marker id="orange-arrow" markerWidth="10" markerHeight="7" refX="9" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" fill="#e67e22"/>
    </marker>
  </defs>
  <!-- Title -->
  <text x="380" y="28" class="title" text-anchor="middle">Instrumental Variables: Causal Structure</text>
  <!-- 2SLS note -->
  <rect x="55" y="230" width="260" height="50" fill="#f0f0f0" rx="5"/>
  <text x="185" y="250" style="font:11px Arial;fill:#333;text-anchor:middle;font-weight:700">2SLS Procedure:</text>
  <text x="185" y="265" style="font:11px Arial;fill:#333;text-anchor:middle">Stage 1: regress x on z → get x̂</text>
  <text x="185" y="278" style="font:11px Arial;fill:#333;text-anchor:middle">Stage 2: regress y on x̂</text>
</svg>
</div>

| Condition | What it means | Testable? |
|---|---|---|
| **Relevance**: $\text{Cov}(z,x) \neq 0$ | Instrument must move the endogenous regressor | ✅ Yes — first-stage F-stat (rule of thumb: F > 10) |
| **Exclusion**: $\text{Cov}(z,u) = 0$ | Instrument affects $y$ only through $x$, not directly | ❌ No — requires economic argument |

---

## 6. Differences-in-Differences: Parallel Trends

*DiD estimates the treatment effect by comparing the change in the treated group to the change in the control group over the same period.*

<div style="overflow-x: auto; margin: 1rem 0;">
<svg viewBox="0 0 760 360" width="100%" xmlns="http://www.w3.org/2000/svg">
  <style>
    .ax { stroke: #555; stroke-width: 1.5; fill: none; }
    .lbl { font: 13px Arial, sans-serif; fill: #333; }
    .title { font: 15px Arial, sans-serif; font-weight: 700; fill: #222; }
  </style>
  <!-- Axes -->
  <line x1="100" y1="300" x2="680" y2="300" class="ax"/>
  <line x1="100" y1="300" x2="100" y2="50" class="ax"/>
  <!-- Treatment line (vertical) -->
  <line x1="380" y1="55" x2="380" y2="300" stroke="#888" stroke-width="1.5" stroke-dasharray="8,5"/>
  <text x="383" y="72" style="font:12px Arial;fill:#888">Treatment</text>
  <text x="383" y="86" style="font:12px Arial;fill:#888">occurs</text>
  <!-- Pre-period labels -->
  <text x="235" y="325" class="lbl" text-anchor="middle">Pre-treatment</text>
  <!-- Post-period labels -->
  <text x="530" y="325" class="lbl" text-anchor="middle">Post-treatment</text>
  <!-- CONTROL GROUP: blue line, gentle slope -->
  <!-- Pre: (100,220)→(380,200); Post: (380,200)→(660,175) -->
  <line x1="100" y1="220" x2="380" y2="195" stroke="#2980b9" stroke-width="2.5"/>
  <line x1="380" y1="195" x2="660" y2="170" stroke="#2980b9" stroke-width="2.5"/>
  <circle cx="100" cy="220" r="5" fill="#2980b9"/>
  <circle cx="380" cy="195" r="5" fill="#2980b9"/>
  <circle cx="660" cy="170" r="5" fill="#2980b9"/>
  <text x="665" y="168" class="lbl" fill="#2980b9">Control</text>
  <!-- TREATED GROUP: red line -->
  <!-- Pre: (100,200)→(380,175); Post ACTUAL: (380,175)→(660,115) -->
  <line x1="100" y1="200" x2="380" y2="175" stroke="#e74c3c" stroke-width="2.5"/>
  <line x1="380" y1="175" x2="660" y2="115" stroke="#e74c3c" stroke-width="2.5"/>
  <circle cx="100" cy="200" r="5" fill="#e74c3c"/>
  <circle cx="380" cy="175" r="5" fill="#e74c3c"/>
  <circle cx="660" cy="115" r="5" fill="#e74c3c"/>
  <text x="665" y="113" class="lbl" fill="#e74c3c">Treated</text>
  <!-- COUNTERFACTUAL: dashed red (parallel to control in post period) -->
  <!-- Control moves from 195 to 170 = -25. Counterfactual: 175 to 150 -->
  <line x1="380" y1="175" x2="660" y2="150" stroke="#e74c3c" stroke-width="1.5" stroke-dasharray="8,5"/>
  <text x="665" y="148" class="lbl" fill="#e74c3c" opacity="0.6">Counterfactual</text>
  <text x="665" y="162" class="lbl" fill="#e74c3c" opacity="0.6">(no treatment)</text>
  <!-- Treatment effect bracket at post-period -->
  <line x1="645" y1="115" x2="645" y2="150" stroke="#8e44ad" stroke-width="3"/>
  <line x1="638" y1="115" x2="652" y2="115" stroke="#8e44ad" stroke-width="2"/>
  <line x1="638" y1="150" x2="652" y2="150" stroke="#8e44ad" stroke-width="2"/>
  <text x="580" y="130" class="lbl" fill="#8e44ad" font-weight="700">β̂_DD</text>
  <text x="575" y="144" class="lbl" fill="#8e44ad">(treatment</text>
  <text x="575" y="158" class="lbl" fill="#8e44ad"> effect)</text>
  <!-- Y-axis labels -->
  <text x="80" y="125" class="lbl">Y</text>
  <!-- Time labels on x axis -->
  <text x="100" y="318" class="lbl" text-anchor="middle">t₀</text>
  <text x="380" y="318" class="lbl" text-anchor="middle">t₁</text>
  <text x="660" y="318" class="lbl" text-anchor="middle">t₂</text>
  <!-- Formula box -->
  <rect x="105" y="55" width="250" height="55" fill="#f5eef8" rx="6"/>
  <text x="230" y="74" style="font:12px Arial;fill:#8e44ad;font-weight:700;text-anchor:middle">β̂_DD = (Ȳ₁₁ − Ȳ₁₀) − (Ȳ₀₁ − Ȳ₀₀)</text>
  <text x="230" y="90" style="font:11px Arial;fill:#555;text-anchor:middle">= Change in treated</text>
  <text x="230" y="104" style="font:11px Arial;fill:#555;text-anchor:middle">minus Change in control</text>
  <!-- Parallel trends note -->
  <rect x="105" y="245" width="250" height="40" fill="#eafaf1" rx="6"/>
  <text x="230" y="262" style="font:11px Arial;fill:#27ae60;text-anchor:middle;font-weight:700">Parallel Trends Assumption:</text>
  <text x="230" y="277" style="font:11px Arial;fill:#27ae60;text-anchor:middle">Counterfactual trend = Control trend</text>
  <!-- Title -->
  <text x="380" y="30" class="title" text-anchor="middle">Differences-in-Differences: Parallel Trends</text>
</svg>
</div>

**The logic of DiD:**
- **First difference** (treated group: post − pre): removes time-invariant characteristics of the treated group
- **Second difference** (control group: post − pre): estimates the counterfactual trend
- **DiD**: treatment effect = $(\bar{Y}_{1,1} - \bar{Y}_{1,0}) - (\bar{Y}_{0,1} - \bar{Y}_{0,0})$

**Regression form:** $y_{it} = \alpha + \gamma D_i^{treat} + \lambda D_t^{post} + \beta(D_i^{treat} \times D_t^{post}) + \varepsilon_{it}$

The coefficient $\beta$ on the interaction term is the DiD estimate.

---

## 7. Quick Reference: OVB Formula

$$\tilde{\beta}_1 = \underbrace{\beta_1}_{\text{true effect}} + \underbrace{\beta_2 \cdot \frac{\text{Cov}(x_2, x_1)}{\text{Var}(x_1)}}_{\text{omitted variable bias}}$$

where $x_2$ is the omitted variable, $\beta_2$ is its true coefficient, and the second term is zero only if $\text{Cov}(x_2, x_1) = 0$.

---

## 8. Key Formulas at a Glance

| Concept | Formula |
|---|---|
| OLS slope | $\hat{\beta}_1 = \dfrac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})^2} = \dfrac{\widehat{\text{Cov}}(x,y)}{\widehat{\text{Var}}(x)}$ |
| OLS intercept | $\hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x}$ |
| R-squared | $R^2 = 1 - \text{SSR}/\text{SST}$ |
| Variance of OLS slope | $\text{Var}(\hat{\beta}_1) = \dfrac{\sigma^2}{\sum(x_i-\bar{x})^2}$ |
| Error variance estimator | $\hat{\sigma}^2 = \dfrac{\text{SSR}}{n-k-1}$ |
| t-statistic | $t = \dfrac{\hat{\beta}_j - \beta_{j,0}}{\text{se}(\hat{\beta}_j)} \sim t_{n-k-1}$ |
| F-statistic | $F = \dfrac{(\text{SSR}_r - \text{SSR}_{ur})/q}{\text{SSR}_{ur}/(n-k-1)} \sim F_{q,\,n-k-1}$ |
| BP LM test | $LM = n \cdot R^2_{\text{aux}} \sim \chi^2_k$ |
| IV estimator | $\hat{\beta}_{IV} = \dfrac{\text{Cov}(z,y)}{\text{Cov}(z,x)}$ |
| DiD estimator | $\hat{\beta}_{DD} = (\bar{Y}_{1,1} - \bar{Y}_{1,0}) - (\bar{Y}_{0,1} - \bar{Y}_{0,0})$ |
| Durbin-Watson | $DW \approx 2(1-\hat{\rho})$ |
| Quadratic turning point | $x^* = -\hat{\beta}_1/(2\hat{\beta}_2)$ |
