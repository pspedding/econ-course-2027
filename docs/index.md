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

<!-- Econometrics tutor — protected staging Worker -->
<!-- CDN: DOMPurify (XSS sanitisation) + marked (markdown rendering) -->
<script src="https://cdn.jsdelivr.net/npm/dompurify@3/dist/purify.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/marked@12/marked.min.js"></script>
<script>
window.MathJax = {
  tex: {
    inlineMath:  [["\(", "\)"]],
    displayMath: [["\[", "\]"]],
    processEscapes: true
  },
  options: { skipHtmlTags: ["script","noscript","style","textarea","pre"] }
};
</script>
<script src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js" id="MathJax-script" async></script>

<div id="econ-chat-widget" style="
  margin: 2rem 0;
  background: white;
  border: 1px solid #e2e8f0;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 2px 8px rgba(0,0,0,0.06);
">
  <h3 style="margin:0 0 0.5rem 0; font-size:1rem; color:#2d3748;">🎓 Ask a Question</h3>
  <p style="margin:0 0 1rem 0; font-size:0.85rem; color:#718096;">Support for ECMT5001 preparation using the M01–M10 self-study scope. 2027 syllabus alignment pending; the tutor does not receive lesson pages.</p>

  <!-- Mode toggle -->
  <div style="display:flex;gap:0.5rem;margin-bottom:0.8rem;">
    <button class="econ-mode-btn" data-mode="explain"
      style="padding:0.3rem 0.8rem;border:1px solid #9fa8da;border-radius:6px;cursor:pointer;font-size:0.82rem;background:#5c6bc0;color:white;">
      Explain
    </button>
    <button class="econ-mode-btn" data-mode="tutor"
      style="padding:0.3rem 0.8rem;border:1px solid #9fa8da;border-radius:6px;cursor:pointer;font-size:0.82rem;background:#e8eaf6;color:#3949ab;">
      Tutor
    </button>
  </div>

  <!-- Conversation thread -->
  <div id="econ-chat-thread" style="max-height:380px;overflow-y:auto;margin-bottom:0.8rem;display:flex;flex-direction:column;gap:0.3rem;"></div>

  <!-- Access code row — entered once, kept in memory only, never stored or embedded -->
  <div id="econ-access-row" style="display:flex;gap:0.5rem;margin-bottom:0.5rem;align-items:center;">
    <input id="econ-access-code" type="password" autocomplete="off"
      placeholder="Access code"
      style="width:140px;padding:0.5rem 0.7rem;border:1px solid #cbd5e0;border-radius:8px;font-size:0.9rem;outline:none;"
    />
    <span style="font-size:0.8rem;color:#718096;">Enter the access code provided to you</span>
  </div>

  <!-- Input row -->
  <div style="display:flex; gap:0.5rem;">
    <input id="econ-chat-input" type="text"
      placeholder="e.g. When is OLS unbiased?"
      style="flex:1; padding:0.6rem 0.9rem; border:1px solid #cbd5e0; border-radius:8px; font-size:0.9rem; outline:none;"
    />
    <button id="econ-chat-btn" style="
      padding:0.6rem 1.2rem; background:#5c6bc0; color:white;
      border:none; border-radius:8px; cursor:pointer; font-size:0.9rem; font-weight:600;
      white-space:nowrap;
    ">Ask →</button>
    <button id="econ-chat-clear" type="button" style="
      padding:0.6rem 0.8rem; background:#e8eaf6; color:#3949ab;
      border:1px solid #9fa8da; border-radius:8px; cursor:pointer; font-size:0.9rem;
    ">Clear</button>
  </div>

  <div id="econ-chat-response" style="
    margin-top:1rem; padding:1rem; background:#f7fafc;
    border-radius:8px; font-size:0.9rem; line-height:1.6;
    color:#2d3748; display:none;
  "></div>
</div>

<script>
(function(){
  // STAGING: points at staging Worker — swap to production URL after tests pass
  var WORKER='https://econ-chat-staging.dgg5dknmth.workers.dev';
  // PRODUCTION (do not activate until staging tests pass):
  // var WORKER='https://econ-chat.dgg5dknmth.workers.dev';

  var MAX_TURNS=10, MAX_Q=4000;
  var history=[], mode='explain', accessToken='';

  function estimateTokens(s){ return Math.ceil((s||'').length/4); }

  function trimHistory(h){
    var msgs=h.slice();
    while(msgs.length>1 && msgs.reduce(function(s,m){return s+estimateTokens(m.content);},0)>4000)
      msgs.splice(0,2);
    return msgs.slice(-(MAX_TURNS*2));
  }

  function detectContext(){
    var p=window.location.pathname;
    var cm=p.match(/macro-course|micro-course|econ-course/);
    var mm=p.match(/module-([0-9]+)/i);
    var lm=p.match(/(M[0-9]{2}[-.]L[0-9]{2}[^/]*)/i);
    return {
      course: cm ? ({'macro-course':'macroeconomics','micro-course':'microeconomics','econ-course':'econometrics'})[cm[0]]||cm[0].replace(/-course(-[0-9]+)?/,'') : null,
      module: mm ? 'M'+(mm[1].length<2?'0':'')+mm[1] : null,
      lesson: lm ? lm[1] : null
    };
  }

  function getWeakModules(){
    try{
      var keys=Object.keys(localStorage).filter(function(k){return k.indexOf('econ-')===0&&k.slice(-3)==='-v1';});
      for(var i=0;i<keys.length;i++){
        var s=JSON.parse(localStorage.getItem(keys[i])||'{}');
        var w=Object.keys(s.mastery||{}).filter(function(k){
          var v=s.mastery[k];
          return v.attempts>=3&&v.correct/v.attempts<0.65;
        }).slice(0,5);
        if(w.length) return w;
      }
    }catch(e){}
    return [];
  }

  function renderSafe(el,text){
    var t=text
      .split("\[").join("DLOPEN").split("\]").join("DLCLOSE")
      .split("\(").join("ILOPEN").split("\)").join("ILCLOSE");
    var html=marked.parse(t);
    html=html
      .split("DLOPEN").join("\[").split("DLCLOSE").join("\]")
      .split("ILOPEN").join("\(").split("ILCLOSE").join("\)");
    el.innerHTML=DOMPurify.sanitize(html,{USE_PROFILES:{html:true}});
    if(window.MathJax&&MathJax.typesetPromise) MathJax.typesetPromise([el]).catch(function(){});
  }

  function appendThread(role,text){
    var t=document.getElementById('econ-chat-thread');
    if(!t) return;
    var d=document.createElement('div');
    d.style.cssText=role==='user'
      ?'padding:0.55rem 0.8rem;background:#eef2ff;border-radius:8px;font-size:0.9rem;margin-bottom:0.2rem;'
      :'padding:0.55rem 0.8rem;background:#f7fafc;border-radius:8px;font-size:0.9rem;line-height:1.65;margin-bottom:0.2rem;';
    if(role==='user') d.textContent=text;
    else renderSafe(d,text);
    t.appendChild(d);
    t.scrollTop=t.scrollHeight;
  }

  function econAsk(){
    var input=document.getElementById('econ-chat-input');
    var btn=document.getElementById('econ-chat-btn');
    var resp=document.getElementById('econ-chat-response');
    var q=(input&&input.value||'').trim();
    if(!q) return;
    // Read access code from field each time — kept in memory only
    var codeInput=document.getElementById('econ-access-code');
    if(codeInput) accessToken=codeInput.value.trim();
    if(!accessToken){
      if(resp){resp.style.display='block';resp.textContent='Please enter your access code.';}
      if(codeInput) codeInput.focus();
      return;
    }
    if(q.length>MAX_Q){
      if(resp){resp.style.display='block';resp.textContent='Question too long (max 4,000 characters).';}
      return;
    }
    if(btn){btn.textContent='...';btn.disabled=true;}
    if(resp) resp.style.display='none';
    appendThread('user',q);
    if(input) input.value='';

    var ctx=detectContext();
    ctx.weakModules=getWeakModules();
    var payload={question:q,mode:mode,messages:trimHistory(history),context:ctx};

    fetch(WORKER,{method:'POST',headers:{'Content-Type':'application/json','Authorization':'Bearer '+accessToken},body:JSON.stringify(payload)})
      .then(function(r){return r.json();})
      .then(function(d){
        if(d.error) throw new Error(d.error);
        history.push({role:'user',content:q},{role:'assistant',content:d.answer});
        if(history.length>MAX_TURNS*2) history.splice(0,2);
        appendThread('assistant',d.answer);
      })
      .catch(function(e){
        if(resp){resp.style.display='block';resp.textContent=e.message||'Error: could not reach the AI. Please try again.';}
      })
      .finally(function(){
        if(btn){btn.textContent='Ask →';btn.disabled=false;}
        if(input) input.focus();
      });
  }

  function clearConversation(){
    history=[];
    var t=document.getElementById('econ-chat-thread');
    if(t) t.innerHTML='';
    var r=document.getElementById('econ-chat-response');
    if(r) r.style.display='none';
  }

  function setMode(m){
    mode=m;
    var btns=document.querySelectorAll('.econ-mode-btn');
    for(var i=0;i<btns.length;i++){
      btns[i].style.background=btns[i].getAttribute('data-mode')===m?'#5c6bc0':'#e8eaf6';
      btns[i].style.color=btns[i].getAttribute('data-mode')===m?'white':'#3949ab';
    }
  }

  function init(){
    var inp=document.getElementById('econ-chat-input');
    if(inp) inp.addEventListener('keydown',function(e){if(e.key==='Enter')econAsk();});
    var btn=document.getElementById('econ-chat-btn');
    if(btn) btn.addEventListener('click',econAsk);
    var clr=document.getElementById('econ-chat-clear');
    if(clr) clr.addEventListener('click',clearConversation);
    var mbtns=document.querySelectorAll('.econ-mode-btn');
    for(var i=0;i<mbtns.length;i++){
      (function(b){b.addEventListener('click',function(){setMode(b.getAttribute('data-mode'));});})(mbtns[i]);
    }
    setMode('explain');
  }

  if(document.readyState==='loading') document.addEventListener('DOMContentLoaded',init);
  else init();

  window.econAsk=econAsk;
})();
</script>
