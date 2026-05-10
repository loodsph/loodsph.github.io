---
layout: post
title: "Heart meds, trauma, and free will"
seo_title: "Propranolol and memory: heart medication for trauma and PTSD"
date: 2026-05-02
categories: [farmacologia, filosofia]
tags: [propranolol, neuroscience, ptsd, memory, free will]
description: "When heart medications directly interfere with our brain"
pixel_icon: "free_will.png"
smooth_image: true
lang: en
ref: propranolol
---

## Philosophical part

> We are a lump of meat and neurons moving through the world.

There is no little man inside the man making decisions; our actions are the result of electrical signals propagating, responding to stimuli caused by other stimuli, and so on back to the Big Bang.

Yet free will is a very strong perception and a fundamental pillar of our entire society, basically to punish violent behaviors.

So let's play this game. I don't know if it exists, but having the perception of it, I behave as if it did, as if I truly had power over my actions.

Let's take an interesting case. [Here](https://www.niskanencenter.org/research-roundup-lead-exposure-causes-crime/) the effects of lead poisoning on people are analyzed. It increases aggression and decreases IQ. Crimes literally increase in a contaminated area. Can we say that the behaviors of people exposed to this metal are their "fault"?

This is a very clear example, *imho*, of how external chemistry impacts our behaviors. In the previous case, negatively. **What if it could be used positively?**

## But what do heart meds have to do with it?

Premise: no official guidelines include the use of these drugs for such purposes. We must wait for the end of more concrete and concordant studies. So far the results are too conflicting.

I can already hear the criticisms: *"You don't need drugs to solve problems, it's all a matter of willpower"*, *"you are spoiled"*, etc...

Give me the benefit of the doubt:

Drugs, as seen in [previous posts](https://loodsph.github.io/farmacologia/2026/03/31/cytisine.html), act by binding to receptors. **Propranolol** is a drug that reduces heart rate in those who take it by blocking some receptors stimulated by adrenaline (in particular, it blocks β-adrenergic receptors). These receptors are also present in the brain. We have all experienced an "adrenaline rush" (it's not really adrenaline, but you get the point). Propranolol has the interesting ability (due to its lipophilicity) to reach the brain and bind to these receptors.

Following a traumatic event, a bereavement, but also a heartbreak (ironic that a heart drug also helps with "broken hearts"), massive doses of neurotransmitters are released.

A memory is a [complex thing](https://loodsph.github.io/complexity/filosofia/psychology/2026/01/13/bugs-bunny.html). When we recall a memory, various areas of the brain activate: the **hippocampus**, the more "rational" area that processes facts, and the **amygdala**, the more "emotional" area that recalls the emotions linked to the memory. Interfering with the amygdala doesn't change the facts, but the emotions we associate with them.

Trauma makes sense. It makes us run away when we find ourselves in a previously experienced situation that we know is dangerous. It's an important thing: avoiding moderate trauma at all costs is a problem. Living in a bubble is not a good idea. However, it can happen that the response is disproportionate, and I don't believe that suffering uselessly serves any purpose.

When we recall a memory, the amygdala activates, sending all those danger signals via adrenaline. This triggers a series of mechanisms that cause the creation of new communications between neurons. These cause the thought and the [consolidation of the memory](https://istss.org/student-perspectives-the-effect-of-beta-blockers-on-traumatic-memory-consolidation-and-reconsolidation-tara-frem-ba/). Propranolol theoretically decreases the possibility of creating these bridges.

## The three stages of propranolol

[They tried](https://pubmed.ncbi.nlm.nih.gov/26454715/) administering the drug immediately after a trauma, but it produced inconsistent evidence. Perhaps because the rush at that moment is too strong.

Then they tried administering it later, when recalling the memory by reading a written text or in a short psychological session (10-15 minutes). In some cases, the results have been extraordinary: most participants lost the clinical diagnostic criteria for **PTSD** (post-traumatic stress disorder). Overall, however, the literature is still conflicting and there is no consensus.

For now, the treatment of trauma is not based on reconsolidation, but on **fear extinction**. During prolonged exposure sessions (usually 60-90 minutes), the repetition of the experience without a negative outcome induces a "new" inhibitory memory. This new memory overlaps the old one, but doesn't erase it. The original pathological memories remain latent and can resurface following sudden stress.

If the therapeutic session is short (10-15 minutes), the memory is only reactivated and made labile (reconsolidation). In that instant, propranolol can help rewrite the original trace. If the session lasts beyond 30-45 minutes, reconsolidation is depotentiated and the extinction pathway is triggered. Extinction, however, in order to be learned needs the exact same adrenaline that propranolol blocks: administering it during a long session would risk sabotaging the therapy itself.

{% raw %}
<style>
.pw {
  --pw-bg: var(--card-bg, #ffffff);
  --pw-ink: var(--text-color, #222222);
  --pw-muted: var(--text-muted, #6b6b6b);
  --pw-line: var(--border-color, #e5e5e5);
  --pw-amigdala: #c0392b;
  --pw-vmpfc: #1f6e62;
  --pw-warn: #c07c0e;
  --pw-hover: var(--bg-color, #fafafa);

  font-family: 'JetBrains Mono', ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
  background: var(--pw-bg);
  color: var(--pw-ink);
  padding: 1.25rem;
  border: 1px solid var(--pw-line);
  max-width: 700px;
  margin: 2rem auto;
  font-size: 13.5px;
  line-height: 1.55;
  box-sizing: border-box;
  position: relative;
  background-image: radial-gradient(circle at 1px 1px, rgba(0,0,0,0.04) 1px, transparent 0);
  background-size: 8px 8px;
}
@media (prefers-color-scheme: dark) {
  :root:not([data-theme="light"]) .pw {
    --pw-amigdala: #e05c4a;
    --pw-vmpfc: #3db99f;
    --pw-warn: #e8a030;
    background-image: radial-gradient(circle at 1px 1px, rgba(255,255,255,0.04) 1px, transparent 0);
  }
}
:root[data-theme="dark"] .pw {
  --pw-amigdala: #e05c4a;
  --pw-vmpfc: #3db99f;
  --pw-warn: #e8a030;
  background-image: radial-gradient(circle at 1px 1px, rgba(255,255,255,0.04) 1px, transparent 0);
}
.pw *, .pw *::before, .pw *::after { box-sizing: border-box; }
.pw-content { background: var(--pw-bg); padding: 0.5rem; margin: -0.5rem; position: relative; }
.pw-header { display: flex; justify-content: space-between; align-items: baseline; border-bottom: 1px solid var(--pw-line); padding-bottom: 0.6rem; margin-bottom: 1rem; gap: 1rem; flex-wrap: wrap; }
.pw-title { font-size: 0.95rem; font-weight: 600; letter-spacing: -0.01em; }
.pw-title::before { content: "// "; color: var(--pw-muted); font-weight: 400; }
.pw-tag { font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.18em; color: var(--pw-muted); }
.pw-controls { display: grid; gap: 0.75rem; margin-bottom: 1rem; }
.pw-label { font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.18em; color: var(--pw-muted); margin-bottom: 0.4rem; display: block; }
.pw-buttons { display: grid; grid-template-columns: repeat(3, 1fr); border: 1px solid var(--pw-line); }
.pw-btn { background: var(--pw-bg); border: none; border-right: 1px solid var(--pw-line); padding: 0.6rem 0.4rem; font-family: inherit; font-size: 0.72rem; cursor: pointer; color: var(--pw-ink); transition: background 0.12s ease; line-height: 1.3; }
.pw-btn:last-child { border-right: none; }
.pw-btn:hover { background: var(--pw-hover); }
.pw-btn.active { background: var(--pw-ink); color: var(--pw-bg); }
.pw-toggle { display: flex; align-items: center; gap: 0.7rem; border: 1px solid var(--pw-line); padding: 0.5rem 0.7rem; cursor: pointer; user-select: none; background: var(--pw-bg); }
.pw-toggle:hover { background: var(--pw-hover); }
.pw-toggle-box { width: 14px; height: 14px; border: 1px solid var(--pw-line); background: var(--pw-bg); flex-shrink: 0; position: relative; }
.pw-toggle.on .pw-toggle-box { background: var(--pw-ink); }
.pw-toggle.on .pw-toggle-box::after { content: ""; position: absolute; inset: 3px; background: var(--pw-bg); }
.pw-toggle-label { font-size: 0.8rem; font-weight: 500; }
.pw-toggle-state { margin-left: auto; font-size: 0.65rem; letter-spacing: 0.18em; text-transform: uppercase; color: var(--pw-muted); }
.pw-bars { display: grid; gap: 0.85rem; padding: 1rem; border: 1px solid var(--pw-line); margin-bottom: 0.85rem; background: var(--pw-bg); }
.pw-bar-row { display: grid; gap: 0.35rem; }
.pw-bar-header { display: flex; justify-content: space-between; align-items: baseline; font-size: 0.75rem; gap: 0.5rem; }
.pw-bar-name { font-weight: 500; }
.pw-bar-region { color: var(--pw-muted); font-size: 0.65rem; font-style: italic; margin-left: 0.3rem; }
.pw-bar-value { font-variant-numeric: tabular-nums; font-size: 0.72rem; color: var(--pw-muted); white-space: nowrap; }
.pw-bar-track { height: 12px; background: var(--pw-bg); border: 1px solid var(--pw-line); position: relative; overflow: hidden; }
.pw-bar-fill { height: 100%; width: 0%; transition: width 0.6s cubic-bezier(0.4, 0, 0.2, 1); }
.pw-bar-fill.amigdala { background: var(--pw-amigdala); }
.pw-bar-fill.vmpfc { background: var(--pw-vmpfc); }
.pw-readout { border: 1px solid var(--pw-line); padding: 0.85rem 0.95rem; background: var(--pw-bg); }
.pw-readout-tag { font-size: 0.62rem; letter-spacing: 0.2em; text-transform: uppercase; color: var(--pw-muted); margin-bottom: 0.45rem; display: flex; align-items: center; gap: 0.5rem; }
.pw-dot { width: 7px; height: 7px; background: var(--pw-vmpfc); display: inline-block; }
.pw-dot.warn { background: var(--pw-warn); }
.pw-dot.bad { background: var(--pw-amigdala); }
.pw-dot.neutral { background: var(--pw-muted); }
.pw-readout-text { font-size: 0.85rem; line-height: 1.55; }
.pw-readout-text em { font-style: italic; color: var(--pw-amigdala); font-weight: 500; }
.pw-footer { margin-top: 0.85rem; font-size: 0.62rem; color: var(--pw-muted); text-align: right; letter-spacing: 0.04em; }
.pw-footer::before { content: "→ "; }
@media (max-width: 480px) {
  .pw { padding: 1rem; font-size: 12.5px; }
  .pw-btn { font-size: 0.68rem; padding: 0.55rem 0.3rem; }
  .pw-title { font-size: 0.85rem; }
  .pw-readout-text { font-size: 0.8rem; }
}
</style>

<div class="pw" id="propranololoWidget">
  <div class="pw-content">
    <div class="pw-header">
      <div class="pw-title">the three stages of propranolol</div>
      <div class="pw-tag">simulated scenario</div>
    </div>
    <div class="pw-controls">
      <div>
        <span class="pw-label">timing of administration</span>
        <div class="pw-buttons" role="tablist">
          <button class="pw-btn active" data-time="subito">Right after<br>the trauma</button>
          <button class="pw-btn" data-time="breve">Short session<br>(10–15 min)</button>
          <button class="pw-btn" data-time="lunga">Long session<br>(60–90 min)</button>
        </div>
      </div>
      <div class="pw-toggle on" id="pwToggle" tabindex="0" role="switch" aria-checked="true">
        <div class="pw-toggle-box"></div>
        <span class="pw-toggle-label">propranolol</span>
        <span class="pw-toggle-state" id="pwToggleState">active</span>
      </div>
    </div>
    <div class="pw-bars">
      <div class="pw-bar-row">
        <div class="pw-bar-header">
          <div>
            <span class="pw-bar-name">emotional charge of memory</span>
            <span class="pw-bar-region">amygdala</span>
          </div>
          <span class="pw-bar-value" id="pwAmigdalaVal">—</span>
        </div>
        <div class="pw-bar-track">
          <div class="pw-bar-fill amigdala" id="pwAmigdalaFill"></div>
        </div>
      </div>
      <div class="pw-bar-row">
        <div class="pw-bar-header">
          <div>
            <span class="pw-bar-name">safety memory</span>
            <span class="pw-bar-region">prefrontal cortex</span>
          </div>
          <span class="pw-bar-value" id="pwVmpfcVal">—</span>
        </div>
        <div class="pw-bar-track">
          <div class="pw-bar-fill vmpfc" id="pwVmpfcFill"></div>
        </div>
      </div>
    </div>
    <div class="pw-readout">
      <div class="pw-readout-tag">
        <span class="pw-dot" id="pwDot"></span>
        <span id="pwOutcome">outcome</span>
      </div>
      <div class="pw-readout-text" id="pwDescription">—</div>
    </div>
    <div class="pw-footer">conceptual model, not clinical</div>
  </div>
</div>

<script>
(function() {
  const widget = document.getElementById('propranololoWidget');
  if (!widget) return;
  const scenari = {
    'subito-on': { amigdala: 88, vmpfc: 0, outcome: 'no effect', dotClass: 'neutral', desc: 'The adrenergic discharge is too intense: the drug cannot interfere with the initial consolidation. The trauma sets in anyway.' },
    'subito-off': { amigdala: 95, vmpfc: 0, outcome: 'full consolidation', dotClass: 'bad', desc: 'The trauma is stored with full emotional charge. This is the starting condition that brings people to therapy months or years later.' },
    'breve-on': { amigdala: 32, vmpfc: 8, outcome: 'rewriting', dotClass: 'vmpfc', desc: 'The memory is labile and propranolol intercepts the reconsolidation: the original trace is <em>rewritten</em> with less emotional charge. This is where the most surprising results live.' },
    'breve-off': { amigdala: 82, vmpfc: 5, outcome: 'unchanged reconsolidation', dotClass: 'neutral', desc: 'Reactivating the memory makes it temporarily labile, but without the drug it sets back as it was. Nothing changes.' },
    'lunga-on': { amigdala: 78, vmpfc: 12, outcome: 'sabotaged therapy', dotClass: 'warn', desc: 'Paradox. The new inhibitory memory needs the same adrenaline that propranolol blocks: the drug prevents the therapy from consolidating.' },
    'lunga-off': { amigdala: 55, vmpfc: 78, outcome: 'extinction', dotClass: 'vmpfc', desc: 'Extinction: the prefrontal cortex builds a safety memory that inhibits the amygdala one. The trauma remains latent but is kept at bay — this is the current gold standard.' }
  };
  let state = { time: 'subito', drug: true };
  const buttons = widget.querySelectorAll('.pw-btn');
  const toggle = widget.querySelector('#pwToggle');
  const toggleState = widget.querySelector('#pwToggleState');
  const amigdalaFill = widget.querySelector('#pwAmigdalaFill');
  const amigdalaVal = widget.querySelector('#pwAmigdalaVal');
  const vmpfcFill = widget.querySelector('#pwVmpfcFill');
  const vmpfcVal = widget.querySelector('#pwVmpfcVal');
  const outcome = widget.querySelector('#pwOutcome');
  const description = widget.querySelector('#pwDescription');
  const dot = widget.querySelector('#pwDot');
  function render() {
    const key = state.time + '-' + (state.drug ? 'on' : 'off');
    const s = scenari[key];
    amigdalaFill.style.width = s.amigdala + '%';
    vmpfcFill.style.width = s.vmpfc + '%';
    amigdalaVal.textContent = s.amigdala + '/100';
    vmpfcVal.textContent = s.vmpfc + '/100';
    outcome.textContent = s.outcome;
    description.innerHTML = s.desc;
    dot.className = 'pw-dot ' + s.dotClass;
    buttons.forEach(b => b.classList.toggle('active', b.dataset.time === state.time));
    toggle.classList.toggle('on', state.drug);
    toggle.setAttribute('aria-checked', state.drug);
    toggleState.textContent = state.drug ? 'active' : 'inactive';
  }
  buttons.forEach(btn => { btn.addEventListener('click', () => { state.time = btn.dataset.time; render(); }); });
  function flipDrug() { state.drug = !state.drug; render(); }
  toggle.addEventListener('click', flipDrug);
  toggle.addEventListener('keydown', e => { if (e.key === ' ' || e.key === 'Enter') { e.preventDefault(); flipDrug(); } });
  render();
})();
</script>
{% endraw %}

In some cases, qualitative interviews corroborated the quantitative data, with patients reporting the downgrading of the event from a source of daily, burning anguish to an "*anesthetized scar*", impossible to forget but incapable of generating vivid pain.

If an external intervention, apparently designed for something else entirely, has an effect on such an important part of everyone's personality, can we really say we are steering the ship?

Suppose you wake up from a coma after a bad accident and have forgotten everything. Are you still you? Will you like the same things? Will you love the same people? Something that really happened in the past has effects on the present because its consequences are "visible" to us. If an event no longer has any link to the present, did it really happen to you?

If you went to Japan, loved it, internalized their idea of respect, and it made your life better, more fulfilling, but then you forget everything? Can you say you've ever been there? Sure, there are photos on Instagram, but then what?

Our experiences characterize us, for better or worse. What these interventions try to do is go and rewrite ourselves.

I try to be pragmatic. In allergic reactions, the immune system gets "confused", mistaking something relatively harmless seen in the past for a huge danger and activating a series of responses that end up being the real problem. No one would have any doubts about modulating a hyper-reactive immune system, why should we treat another system differently?