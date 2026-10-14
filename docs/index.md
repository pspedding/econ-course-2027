# Econometrics 2027

**ECMT5001 Principles of Econometrics — USYD-aligned self-study course**

This course follows the structure of USYD's ECMT5001 unit, using **Wooldridge's *Introductory Econometrics*** (5th–7th editions) as the primary textbook. It is designed for students starting the Graduate Certificate of Economics (Semester 1, 2027).

---

## Course Structure

| Module | Topic | Wooldridge Chapters |
|--------|-------|-------------------|
| [M01](modules/module-01/M01.L01-descriptive-stats-summation.md) | Probability & Statistics Review | Appendix A–C |
| [M02](modules/module-02/M02.L01-simple-regression-model.md) | Simple Linear Regression | Chapter 2 |
| [M03](modules/module-03/M03.L01-multiple-regression-model.md) | Multiple Linear Regression | Chapter 3 |
| [M04](modules/module-04/M04.L01-sampling-distributions.md) | Statistical Inference | Chapters 4–5 |
| [M05](modules/module-05/M05.L01-log-transformations.md) | Functional Forms & Dummy Variables | Chapters 6–7 |
| [M06](modules/module-06/M06.L01-nature-consequences.md) | Heteroskedasticity | Chapter 8 |
| [M07](modules/module-07/M07.L01-specification-errors.md) | Specification & Data Issues | Chapter 9 |
| [M08](modules/module-08/M08.L01-nature-time-series.md) | Time Series Basics | Chapter 10 |
| [M09](modules/module-09/M09.L01-ols-serial-correlation.md) | Serial Correlation & Autocorrelation | Chapter 12 |
| [M10](modules/module-10/M10.L01-endogeneity-causality.md) | Instrumental Variables | Chapters 15–16 |

---

## Assessment (ECMT5001 structure)

| Assessment | Weight | Coverage |
|-----------|--------|---------|
| Mid-semester exam | 40% | M01–M04 (Lectures 1–6) |
| Final exam | 50% | Full course |
| Online quizzes (×2) | 10% | In-class |

---

## How to Use This Course

1. Work through each module in order — later modules build on earlier ones
2. Complete the **practice prompts** at the end of each lesson before checking answers
3. Use the **Formula Sheet** in Exam Prep as a running reference
4. Attempt **Past Exams** under timed conditions once you've finished each module cluster

!!! tip "Maths prerequisite"
    This course assumes comfort with basic algebra and summation notation (Σ). If you need a refresher, start with M01.L01 which covers summation notation from scratch.

---

## 🎓 Ask a Question

<!-- Econometrics AI Chat Widget -->
<div id="econ-chat-widget" style="
  margin: 2rem 0;
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.06);
">
  <h3 style="margin:0 0 0.5rem 0; font-size:1rem; color:#2d3748;">🎓 Ask a Question</h3>
  <p style="margin:0 0 1rem 0; font-size:0.85rem; color:#718096;">Ask anything about the course content — OLS, hypothesis testing, heteroskedasticity, time series, IV, and more.</p>
  <div style="display:flex; gap:0.5rem;">
    <input id="econ-chat-input" type="text"
      placeholder="e.g. What is the difference between OLS and WLS?"
      style="flex:1; padding:0.6rem 0.9rem; border:1px solid #cbd5e0; border-radius:8px; font-size:0.9rem; outline:none;"
      onkeydown="if(event.key==='Enter') econAsk()"
    />
    <button onclick="econAsk()" id="econ-chat-btn" style="
      padding:0.6rem 1.2rem; background:#5c6bc0; color:white;
      border:none; border-radius:8px; cursor:pointer; font-size:0.9rem; font-weight:600;
      white-space:nowrap;
    ">Ask →</button>
  </div>
  <div id="econ-chat-response" style="
    margin-top:1rem; padding:1rem; background:#f7fafc;
    border-radius:8px; font-size:0.9rem; line-height:1.6;
    color:#2d3748; display:none;
  "></div>
</div>
<script>
async function econAsk() {
  const input = document.getElementById('econ-chat-input');
  const btn = document.getElementById('econ-chat-btn');
  const resp = document.getElementById('econ-chat-response');
  const q = input.value.trim();
  if (!q) return;
  btn.textContent = '...'; btn.disabled = true;
  resp.style.display = 'block';
  resp.textContent = 'Thinking...';
  try {
    const r = await fetch('https://econ-chat.dgg5dknmth.workers.dev', {
      method: 'POST',
      headers: {'Content-Type':'application/json'},
      body: JSON.stringify({question: q})
    });
    const d = await r.json();
    resp.innerHTML = d.answer.replace(/\n/g,'<br>');
  } catch(e) {
    resp.textContent = 'Error: could not reach the AI. Please try again.';
  }
  btn.textContent = 'Ask →'; btn.disabled = false;
}
</script>
