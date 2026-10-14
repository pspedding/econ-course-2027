# 🎮 Daily Bite — ECMT5001 Econometrics

*One 10-minute econometrics workout: one concept, five quick questions, confidence check, and gentle XP/streak tracking.*

<div id="daily-bite-app" class="daily-bite-shell">
  <section class="db-hero">
    <div>
      <div class="db-kicker">Today's bite</div>
      <h2 id="db-title">Loading your bite…</h2>
      <p id="db-subtitle">Pulling a small practice set from the existing flashcard bank.</p>
    </div>
    <div class="db-stats-card">
      <div><span id="db-xp">0</span><small>XP</small></div>
      <div><span id="db-streak">0</span><small>day streak</small></div>
      <div><span id="db-ready">0%</span><small>mastery</small></div>
    </div>
  </section>

  <section class="db-controls">
    <label for="db-module">Focus:</label>
    <select id="db-module">
      <option value="daily">Daily recommended</option>
      <option value="weak">Weakest module</option>
      <option value="random">Random module</option>
    </select>
    <button id="db-new-bite" type="button">Generate bite</button>
    <button id="db-reset-today" type="button" class="secondary">Reset this bite</button>
  </section>

  <section class="db-card db-concept-card">
    <div class="db-label">1. Key concept</div>
    <div id="db-concept">Loading…</div>
  </section>

  <section class="db-card" id="db-visual-card" style="display:none;">
    <div class="db-label">2. Visual anchor</div>
    <div id="db-visual"></div>
  </section>

  <section class="db-card">
    <div class="db-label">3. Quick quiz</div>
    <div id="db-questions"></div>
    <div id="db-complete" class="db-complete" style="display:none;"></div>
  </section>

  <section class="db-card">
    <div class="db-label">4. Exam trap</div>
    <p id="db-trap">Answer first, then explain the econometric reasoning. In exams, marks often sit in the assumptions and interpretation, not just the final number or letter.</p>
  </section>

  <section class="db-card db-mastery-card">
    <div class="db-label">Mastery map</div>
    <div id="db-mastery-map"></div>
  </section>
</div>

<style>
.daily-bite-shell { --db-primary:#00897b; --db-ink:#1f2937; --db-muted:#667085; --db-soft:#f0fdfa; --db-border:#b2dfdb; }
.db-hero { display:flex; justify-content:space-between; gap:1rem; align-items:stretch; padding:1.2rem; border-radius:16px; background:linear-gradient(135deg,#e0f2f1,#f8fafc); border:1px solid var(--db-border); margin:1rem 0; }
.db-kicker,.db-label { font-size:0.78rem; font-weight:700; letter-spacing:.08em; text-transform:uppercase; color:var(--db-primary); margin-bottom:.35rem; }
.db-hero h2 { margin:.1rem 0 .35rem; }
.db-hero p { margin:0; color:var(--db-muted); }
.db-stats-card { min-width:230px; display:grid; grid-template-columns:repeat(3,1fr); gap:.5rem; }
.db-stats-card div { background:white; border:1px solid var(--db-border); border-radius:12px; padding:.75rem; text-align:center; }
.db-stats-card span { display:block; font-weight:800; font-size:1.35rem; color:var(--db-ink); }
.db-stats-card small { color:var(--db-muted); font-size:.72rem; }
.db-controls { display:flex; flex-wrap:wrap; gap:.6rem; align-items:center; margin:1rem 0; }
.db-controls select,.db-controls button { padding:.48rem .75rem; border-radius:8px; border:1px solid var(--db-border); }
.db-controls button { background:var(--db-primary); color:white; cursor:pointer; font-weight:700; }
.db-controls button.secondary { background:#e0f2f1; color:#00695c; }
.db-card { background:white; border:1px solid var(--db-border); border-radius:14px; padding:1rem; margin:1rem 0; box-shadow:0 1px 2px rgba(16,24,40,.04); }
.db-concept-title { font-weight:800; font-size:1.1rem; margin-bottom:.35rem; }
.db-chip { display:inline-block; background:var(--db-soft); color:#00695c; border:1px solid #80cbc4; border-radius:999px; padding:.15rem .55rem; margin:.15rem .25rem .15rem 0; font-size:.78rem; font-weight:700; }
.db-question { border-top:1px solid #edf0f7; padding:1rem 0; }
.db-question:first-child { border-top:none; padding-top:.2rem; }
.db-q-meta { color:var(--db-muted); font-size:.78rem; margin-bottom:.35rem; }
.db-q-text { font-weight:700; margin-bottom:.6rem; }
.db-option { display:block; width:100%; text-align:left; background:#f8fafc; border:1px solid #d0d5dd; border-radius:9px; padding:.62rem .75rem; margin:.4rem 0; cursor:pointer; }
.db-option:hover { border-color:var(--db-primary); background:var(--db-soft); }
.db-option.correct { background:#ecfdf3; border-color:#12b76a; }
.db-option.incorrect { background:#fff1f3; border-color:#f04438; }
.db-feedback { margin-top:.65rem; padding:.7rem; border-radius:9px; background:#f8fafc; color:#344054; display:none; }
.db-confidence { display:flex; flex-wrap:wrap; gap:.4rem; margin-top:.65rem; }
.db-confidence button { border:1px solid #d0d5dd; background:white; border-radius:999px; padding:.35rem .6rem; cursor:pointer; font-size:.82rem; }
.db-confidence button.selected { background:#e0f2f1; border-color:var(--db-primary); color:#00695c; font-weight:700; }
.db-complete { margin-top:1rem; padding:.9rem; border-radius:12px; background:#ecfdf3; border:1px solid #12b76a; }
.db-mastery-row { display:flex; align-items:center; gap:.55rem; margin:.42rem 0; }
.db-mastery-row span { width:3.2rem; font-weight:700; font-size:.84rem; }
.db-bar { flex:1; height:.55rem; background:#eef2f7; border-radius:999px; overflow:hidden; }
.db-bar > div { height:100%; background:linear-gradient(90deg,#00897b,#12b76a); }
.db-visual-img { max-width:100%; border-radius:12px; border:1px solid var(--db-border); background:white; }
@media (max-width: 720px) { .db-hero { flex-direction:column; } .db-stats-card { min-width:0; } }
</style>

<script>
(function() {
  const STORAGE_KEY = 'econometrics-daily-bite-v1';
  const todayKey = () => new Date().toISOString().slice(0, 10);
  const moduleNames = {
    M01:'Probability & statistics review', M02:'Simple linear regression', M03:'Multiple linear regression',
    M04:'Statistical inference', M05:'Functional forms & dummy variables', M06:'Heteroskedasticity',
    M07:'Specification & data issues', M08:'Time series basics', M09:'Serial correlation',
    M10:'Instrumental variables & DiD'
  };

  let allCards = [];
  let currentBite = [];
  let answers = {};
  let state = loadState();

  function loadState() {
    try { return JSON.parse(localStorage.getItem(STORAGE_KEY)) || { xp:0, streak:0, lastComplete:null, completed:{}, mastery:{} }; }
    catch(e) { return { xp:0, streak:0, lastComplete:null, completed:{}, mastery:{} }; }
  }
  function saveState() { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); }
  function hash(str) { let h = 2166136261; for (let i=0;i<str.length;i++) { h ^= str.charCodeAt(i); h += (h<<1)+(h<<4)+(h<<7)+(h<<8)+(h<<24); } return h >>> 0; }
  function rng(seed) { let x = seed || 123456789; return function() { x ^= x << 13; x ^= x >>> 17; x ^= x << 5; return ((x >>> 0) / 4294967296); }; }
  function shuffle(arr, rand) { for (let i=arr.length-1;i>0;i--) { const j=Math.floor(rand()*(i+1)); [arr[i],arr[j]]=[arr[j],arr[i]]; } return arr; }
  function strip(html) { const d=document.createElement('div'); d.innerHTML=html || ''; return d.textContent || d.innerText || ''; }
  function cleanTopic(t) { return (t || 'econometrics concept').replace(/[-_]/g,' ').replace(/\s+/g,' ').trim().replace(/^./, c => c.toUpperCase()).slice(0, 64); }
  function parseAnswerLetter(card) { const m = (card.back || '').match(/<strong>\s*([A-D])\)/i); return m ? m[1].toUpperCase() : null; }
  function parseMCQ(card) {
    const text = (card.front || '').replace(/<br\s*\/?>/gi, '\n');
    const optionMatches = [...text.matchAll(/(^|\n)\s*([A-D])\)\s*([^\n]+)/g)];
    const letter = parseAnswerLetter(card);
    if (!letter || optionMatches.length < 4) return null;
    const firstOpt = optionMatches[0].index;
    const q = strip(text.slice(0, firstOpt)).replace(/^\[.*?\]\s*/,'').trim();
    const options = optionMatches.slice(0, 4).map(m => ({ letter:m[2].toUpperCase(), text:m[3].trim() }));
    if (!q || options.some(o => !o.text)) return null;
    return { ...card, question:q, options, answerLetter:letter, answerHtml:card.back || '' };
  }
  function usableCards(cards) {
    return cards.map(parseMCQ).filter(Boolean).filter(c =>
      /^M\d\d$/.test(c.module || '') && c.question.length > 10 && c.question.length < 240 &&
      !/[{}]|undefined|null/.test(c.question) && strip(c.answerHtml).length > 15
    );
  }
  async function loadCards() {
    const res = await fetch('../flashcards/');
    if (!res.ok) throw new Error('Could not load flashcard page');
    const html = await res.text();
    const m = html.match(/const ALL_CARDS = ([\s\S]*?);?\s*\n\s*let deck/);
    if (!m) throw new Error('Could not find flashcard data');
    return usableCards(JSON.parse(m[1]));
  }
  function selectModule(mode) {
    const modules = [...new Set(allCards.map(c => c.module))].sort();
    if (mode === 'random') return modules[Math.floor(Math.random()*modules.length)];
    if (mode === 'weak') {
      return modules.map(m => {
        const s = state.mastery[m] || { attempts:0, correct:0 };
        const score = s.attempts ? s.correct / s.attempts : 0;
        return [m, score, s.attempts];
      }).sort((a,b) => (a[1]-b[1]) || (a[2]-b[2]))[0][0];
    }
    return modules[hash(todayKey()) % modules.length];
  }
  function generateBite() {
    const mode = document.getElementById('db-module').value;
    const module = selectModule(mode);
    const rand = rng(hash(todayKey() + '-' + mode + '-' + module));
    const moduleCards = allCards.filter(c => c.module === module);
    currentBite = shuffle(moduleCards.slice(), rand).slice(0, 5);
    if (currentBite.length < 5) currentBite = currentBite.concat(shuffle(allCards.slice(), rand).slice(0, 5-currentBite.length));
    answers = {};
    renderBite(module);
  }
  function renderStats() {
    document.getElementById('db-xp').textContent = state.xp || 0;
    document.getElementById('db-streak').textContent = state.streak || 0;
    const totals = Object.values(state.mastery || {}).reduce((a,m) => ({ attempts:a.attempts+(m.attempts||0), correct:a.correct+(m.correct||0) }), { attempts:0, correct:0 });
    document.getElementById('db-ready').textContent = totals.attempts ? Math.round((totals.correct/totals.attempts)*100) + '%' : '0%';
    renderMasteryMap();
  }
  function renderBite(module) {
    const anchor = currentBite[0];
    document.getElementById('db-title').textContent = `${module}: ${moduleNames[module] || 'Econometrics practice'}`;
    document.getElementById('db-subtitle').textContent = 'A bite-sized set from the econometrics flashcard bank.';
    document.getElementById('db-concept').innerHTML = `
      <div class="db-concept-title">${cleanTopic(anchor.topic)}</div>
      <span class="db-chip">${anchor.module}</span><span class="db-chip">${anchor.lesson || 'lesson'}</span><span class="db-chip">${anchor.type}</span>
      <p>${anchor.question}</p>
      <p style="color:#667085;margin-bottom:0;">Goal: answer the questions, then rate whether each answer was guessed, shaky, or confident.</p>`;
    // Legacy microeconomics diagrams do not depict these econometrics modules.
    document.getElementById('db-visual-card').style.display = 'none';
    document.getElementById('db-trap').textContent = makeTrap(anchor);
    renderQuestions();
    renderStats();
  }
  function makeTrap(card) {
    const topic = cleanTopic(card.topic).toLowerCase();
    if (/instrument|endogen|exclusion|2sls/.test(topic)) return 'Exam trap: instrument relevance alone is not enough; justify the exclusion restriction and the instrument’s independence from the error.';
    if (/heteroskedastic|robust|standard.error/.test(topic)) return 'Exam trap: heteroskedasticity-robust standard errors adjust inference, not the OLS coefficient estimates.';
    if (/serial.correlation|autocorrelation/.test(topic)) return 'Exam trap: serial correlation can invalidate usual standard errors even when coefficient consistency is preserved under the other assumptions.';
    if (/omitted.variable|exogen|bias/.test(topic)) return 'Exam trap: state which regressor-error correlation causes bias; a larger sample does not cure endogeneity.';
    if (/confidence|p.value|hypothesis|t.test/.test(topic)) return 'Exam trap: a p-value is not the probability that the null hypothesis is true.';
    return 'Exam trap: explain the assumptions and interpret the estimated effect, not only the answer letter.';
  }
  function renderQuestions() {
    const container = document.getElementById('db-questions');
    container.innerHTML = '';
    currentBite.forEach((card, idx) => {
      const q = document.createElement('div');
      q.className = 'db-question';
      q.innerHTML = `
        <div class="db-q-meta">${card.module} / ${card.lesson || 'Lesson'} / ${cleanTopic(card.topic)}</div>
        <div class="db-q-text">Q${idx+1}. ${card.question}</div>
        <div class="db-options"></div>
        <div class="db-feedback" id="db-fb-${idx}"></div>
        <div class="db-confidence" id="db-conf-${idx}" style="display:none;">
          <button type="button" data-conf="guess">Guessed</button>
          <button type="button" data-conf="shaky">Shaky</button>
          <button type="button" data-conf="confident">Confident</button>
        </div>`;
      const opts = q.querySelector('.db-options');
      card.options.forEach(opt => {
        const b = document.createElement('button');
        b.type = 'button';
        b.className = 'db-option';
        b.textContent = `${opt.letter}) ${opt.text}`;
        b.addEventListener('click', () => answerQuestion(idx, opt.letter, b));
        opts.appendChild(b);
      });
      container.appendChild(q);
    });
    document.getElementById('db-complete').style.display = 'none';
  }
  function answerQuestion(idx, letter, btn) {
    if (answers[idx]) return;
    const card = currentBite[idx];
    const correct = letter === card.answerLetter;
    answers[idx] = { correct, confidence:null };
    const block = btn.closest('.db-question');
    block.querySelectorAll('.db-option').forEach(b => {
      if (b.textContent.startsWith(card.answerLetter + ')')) b.classList.add('correct');
      else if (b === btn) b.classList.add('incorrect');
      b.disabled = true;
    });
    const fb = document.getElementById(`db-fb-${idx}`);
    fb.style.display = 'block';
    fb.innerHTML = `<strong>${correct ? 'Correct.' : 'Not quite.'}</strong><br>${card.answerHtml}`;
    const conf = document.getElementById(`db-conf-${idx}`);
    conf.style.display = 'flex';
    conf.querySelectorAll('button').forEach(b => b.addEventListener('click', () => {
      answers[idx].confidence = b.dataset.conf;
      conf.querySelectorAll('button').forEach(x => x.classList.remove('selected'));
      b.classList.add('selected');
      maybeComplete();
    }));
    updateMastery(card.module, correct);
    state.xp += correct ? 10 : 2;
    saveState();
    renderStats();
    maybeComplete();
  }
  function updateMastery(module, correct) {
    if (!state.mastery[module]) state.mastery[module] = { attempts:0, correct:0 };
    state.mastery[module].attempts += 1;
    if (correct) state.mastery[module].correct += 1;
  }
  function maybeComplete() {
    if (Object.keys(answers).length < currentBite.length) return;
    const completed = document.getElementById('db-complete');
    const correct = Object.values(answers).filter(a => a.correct).length;
    const today = todayKey();
    if (!state.completed[today]) {
      const yesterday = new Date(Date.now() - 86400000).toISOString().slice(0, 10);
      state.streak = state.lastComplete === yesterday ? (state.streak || 0) + 1 : 1;
      state.lastComplete = today;
      state.completed[today] = true;
      state.xp += 20;
      saveState();
    }
    completed.style.display = 'block';
    completed.innerHTML = `<strong>Bite complete: ${correct}/${currentBite.length}.</strong> +20 completion XP ${correct >= 4 ? '— strong bite.' : '— review the feedback, then try another bite.'}`;
    renderStats();
  }
  function renderMasteryMap() {
    const el = document.getElementById('db-mastery-map');
    const modules = Object.keys(moduleNames).filter(m => (state.mastery && state.mastery[m]) || currentBite.some(c => c.module === m));
    if (!modules.length) { el.innerHTML = '<p style="color:#667085;">Answer a bite to start building your local mastery map.</p>'; return; }
    el.innerHTML = modules.map(m => {
      const s = state.mastery[m] || { attempts:0, correct:0 };
      const pct = s.attempts ? Math.round(100*s.correct/s.attempts) : 0;
      const label = s.attempts === 0 ? 'New' : pct >= 85 ? 'Exam-ready' : pct >= 65 ? 'Practised' : 'Needs work';
      return `<div class="db-mastery-row"><span>${m}</span><div class="db-bar"><div style="width:${pct}%"></div></div><small>${pct}% · ${label}</small></div>`;
    }).join('');
  }

  document.getElementById('db-new-bite').addEventListener('click', generateBite);
  document.getElementById('db-reset-today').addEventListener('click', () => { answers = {}; renderQuestions(); });

  loadCards().then(cards => {
    allCards = cards;
    generateBite();
  }).catch(err => {
    document.getElementById('db-title').textContent = 'Daily Bite could not load';
    document.getElementById('db-subtitle').textContent = err.message;
    document.getElementById('db-concept').textContent = 'Try reloading the page. If it persists, the flashcard data format may have changed.';
  });
})();
</script>
