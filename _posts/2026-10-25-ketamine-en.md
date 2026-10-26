---
layout: post
title: "Ketamine"
seo_title: "Ketamine: from dissociative anesthetic to treatment-resistant depression"
date: 2026-10-25
categories: [farmacologia]
tags: [ketamine, esketamine, pharmacology, neuroscience, depression, receptors]
description: "Ketamine and depression: rapid effects, differences between enantiomers, neuroplasticity hypotheses, and limits of the evidence, with two interactive simulations."
pixel_icon: "ketamine.png"
smooth_image: true
lang: en
ref: ketamine
---

I find ketamine an extremely fascinating molecule.
It has almost everything:

1. Like every antidepressant, it makes me question how much control we really have over our own agency. Much less than we think, yet not zero: choosing whether or not to take a substance from the outside remains an internal choice, with everything that follows from it. And choosing to seek treatment is also a cultural matter: you need to know you have an illness, know that a treatment exists, and be able to access it.
2. The question "what is it for?"—which I deeply hate—makes especially little sense here. Depending on the dose, the route of administration, the person, and the context, it can do wildly different things:
   - it is an anesthetic;
   - it is an analgesic;
   - it is a dissociative recreational substance (capable of causing perceptual alterations, loss of bodily awareness, and the infamous *K-hole*);
   - it is studied and used in the treatment of depression.
3. The way its atoms are arranged in space shapes its pharmacological effects in a very distinctive way.

Yet it is also a molecule about which it is all too easy to tell a neater story than the data actually allow. So I will try to keep three levels separate: **what we observe in patients, what emerges from mechanistic experiments, and the metaphors we use to make sense of it**.

## Depression

To talk about ketamine as an antidepressant, we first have to talk a bit about depression.
Even though, honestly, it's a minefield.

Let's get the nonsense out of the way right now. Depression is a **real** clinical disorder that can profoundly impair a person's life. It has nothing to do with laziness or a lack of willpower.[^depression] Functional MRI studies show differences in the connectivity and activity of several brain networks in patients with depression.[^fmri] We could go on, but arguing over whether depression exists as a disease "is beyond the scope of this course."

The real point is that we are increasingly skeptical that "depression" exists as a single, uniform disease. Under the same label we lump together clinical pictures that differ widely in symptoms, course, and treatment response: which is why it may make more sense to speak of **"depressions" in the plural**. I think of it a bit like type 1 and type 2 diabetes: conditions similar enough to produce overlapping effects and hit the same organs, yet different enough to require different pharmacological strategies.

### A system that has learned a state too well?

We can also look at at least some forms of depression from another perspective: **a system that has learned a state too well**.

A network in which certain patterns become extremely stable:
- rumination;
- negative interpretation;
- anhedonia;
- avoidance;
- stress response;
- pessimistic expectations.

Not because a literal "negative-thought circuit" exists, of course, nor because depression is a bad habit we taught ourselves, but because the brain is an adaptive machine.

What gets repeated tends to become easier to repeat.
And what goes unused tends to weaken.

From this angle, depression can be seen, at least in part, not merely as a "chemical imbalance," but as a problem of neuronal circuit dynamics and rigidity. Ketamine might temporarily loosen that rigidity.

As an analogy, think of how much harder it is to quit smoking after twenty years than after six months. The addiction circuit has dug much deeper and reached many more areas: we associate a cigarette with far more situations and experiences. Every coffee, every break, every moment of stress becomes a trigger. Depression is not an addiction, obviously—it is just a way to convey how hard it is to step off a path once it has become the most heavily traveled one.

### Hours and weeks

"Classic" antidepressants such as SSRIs often take weeks to produce a full clinical response, even though early improvements over placebo can appear within the first week.[^ssri] The intuitive idea is that the brain needs time to remodel its pathways.

Ketamine, by contrast, works in a subset of patients within **hours**.[^clinical]

From the simulation below, I think it becomes clear what I mean: there are "states" and pathways that tend to steer an event toward one reading or another. *(It is a visual metaphor to make the concept intuitive: it pairs different clinical timescales with an invented cognitive diagram).*

{% raw %}
<div id="thought-path-sim">
  <style>
    #thought-path-sim {
      --negative: #ff637d; --alternative: #59dfbc; --shared: #73b6ff;
      --neg-width: 7; --alt-width: 3; --neg-opacity: .85; --alt-opacity: .45;
      color: #edf5ff; background: radial-gradient(circle at 8% 10%, #173552 0, transparent 55%), #07111f;
      border: 1px solid #28415c; border-radius: 22px; padding: 24px; margin: 2rem 0;
      font: 15px/1.6 Inter, ui-sans-serif, system-ui, sans-serif;
    }
    #thought-path-sim * { box-sizing: border-box; }
    #thought-path-sim h3 { color: #edf5ff; margin: 0 0 12px; font-size: 1.65rem; line-height: 1.2; }
    #thought-path-sim p { margin: 0 0 12px; }
    #thought-path-sim .eyebrow { color: #a9cfff; font-size: .72rem; font-weight: 800; text-transform: uppercase; letter-spacing: .1em; }
    #thought-path-sim .lead, #thought-path-sim .note { color: #b9c9da; font-size: .88rem; }
    #thought-path-sim .notice { padding: 12px 15px; border-left: 3px solid #73b6ff; background: #10243a; border-radius: 0 10px 10px 0; font-size: .84rem; margin-bottom: 18px; }
    #thought-path-sim .modes { display: grid; grid-template-columns: repeat(3, 1fr); gap: 10px; }
    #thought-path-sim button, #thought-path-sim select { font: inherit; }
    #thought-path-sim button { cursor: pointer; color: #dbeaff; background: #10243a; border: 1px solid #385a7c; border-radius: 12px; padding: 12px; line-height: 1.35; }
    #thought-path-sim .mode { text-align: left; }
    #thought-path-sim .mode strong, #thought-path-sim .mode small { display: block; }
    #thought-path-sim .mode small { color: #b9c9da; margin-top: 5px; font-size: .75rem; }
    #thought-path-sim .mode[aria-pressed="true"] { background: #1a3c58; border-color: #8acbff; }
    #thought-path-sim .mode[data-mode="ssri"][aria-pressed="true"] { background: #2c284a; border-color: #bca3ff; }
    #thought-path-sim .mode[data-mode="ketamine"][aria-pressed="true"] { background: #3a301d; border-color: #f5b942; }
    #thought-path-sim button:focus-visible, #thought-path-sim select:focus-visible, #thought-path-sim input:focus-visible { outline: 3px solid #ffdc74; outline-offset: 3px; }
    #thought-path-sim button:disabled { opacity: .55; cursor: default; }
    #thought-path-sim .settings { display: grid; grid-template-columns: 1fr 1fr; gap: 18px; margin: 18px 0; padding: 15px; background: #0e1d30; border-radius: 12px; }
    #thought-path-sim label { font-size: .85rem; color: #dce8f4; display: block; }
    #thought-path-sim input[type="range"] { display: block; width: 100%; accent-color: #73b6ff; margin: 12px 0 5px; }
    #thought-path-sim select { display: block; width: 100%; margin-top: 8px; background: #10243a; color: #edf5ff; padding: 8px; border: 1px solid #385a7c; border-radius: 8px; }
    #thought-path-sim .phase-caption { font-size: .76rem; color: #b9c9da; }
    #thought-path-sim .network-wrap { overflow-x: auto; border: 1px solid #28415c; border-radius: 16px; background: #091827; }
    #thought-path-sim #tps-network { display: block; width: 100%; min-width: 600px; height: auto; }
    #thought-path-sim .synapse { fill: none; stroke-linecap: round; vector-effect: non-scaling-stroke; transition: stroke-width .3s, opacity .3s; }
    #thought-path-sim .synapse.shared { stroke: #73b6ff; stroke-width: 3; opacity: .6; }
    #thought-path-sim .synapse.negative { stroke: var(--negative); stroke-width: var(--neg-width); opacity: var(--neg-opacity); }
    #thought-path-sim .synapse.alternative { stroke: var(--alternative); stroke-width: var(--alt-width); opacity: var(--alt-opacity); }
    #thought-path-sim .synapse.ambient { stroke: #57799c; opacity: .25; stroke-width: 1; stroke-dasharray: 3 8; }
    #thought-path-sim .synapse.loop { stroke-dasharray: 7 9; }
    #thought-path-sim .neuron .halo { fill: #73b6ff10; stroke: #73b6ff25; transition: fill .22s ease, stroke .22s ease; }
    #thought-path-sim .neuron .core { fill: #102a45; stroke: #71a8dc; stroke-width: 2; transition: fill .22s ease, stroke .22s ease; }
    #thought-path-sim .neuron.negative .core { fill: #351a2c; stroke: #ff637d; }
    #thought-path-sim .neuron.alternative .core { fill: #12352f; stroke: #59dfbc; }
    #thought-path-sim .neuron.firing .halo { fill: #ffffff26; stroke: #ffffff66; }
    #thought-path-sim .neuron.firing .core { fill: #fff; stroke: #fff; }
    #thought-path-sim .node-label { fill: #b3c5d9; font-size: 12px; text-anchor: middle; }
    #thought-path-sim .path-label { font-size: 13px; font-weight: 800; }
    #thought-path-sim .path-label.negative { fill: #ff9aac; }
    #thought-path-sim .path-label.alternative { fill: #8fecda; }
    #thought-path-sim .output-box { fill: #06111fd1; stroke-width: 1.5; }
    #thought-path-sim .output-box.negative { stroke: #ff637d; }
    #thought-path-sim .output-box.alternative { stroke: #59dfbc; }
    #thought-path-sim .output-title { fill: white; font-size: 14px; font-weight: 800; }
    #thought-path-sim .output-copy { fill: #b6c5d6; font-size: 12px; }
    #thought-path-sim #tps-pulse { opacity: 0; pointer-events: none; }
    #thought-path-sim #tps-pulse.visible { opacity: 1; }
    #thought-path-sim .controls { display: flex; flex-wrap: wrap; gap: 10px; margin-top: 14px; }
    #thought-path-sim .primary { color: #07111f; background: #a9d9ff; font-weight: 750; }
    #thought-path-sim .result { margin: 14px 0; padding: 14px 16px; border: 1px solid #385a7c; border-radius: 12px; background: #0e1d30; }
    #thought-path-sim .result.negative { border-color: #ff637d; }
    #thought-path-sim .result.alternative { border-color: #59dfbc; }
    #thought-path-sim .result blockquote { color: #edf5ff; border: 0; margin: 0; padding: 0; font: inherit; letter-spacing: normal; }
    #thought-path-sim .stats { color: #b9c9da; font-size: .8rem; margin-top: 9px; }
    @media (max-width: 640px) {
      #thought-path-sim { padding: 16px; }
      #thought-path-sim .modes, #thought-path-sim .settings { grid-template-columns: 1fr; }
      #thought-path-sim .controls button { flex: 1 1 100%; }
    }
    @media (prefers-reduced-motion: reduce) { #thought-path-sim * { transition: none !important; } }
  </style>
  <p class="eyebrow">Interactive metaphor · Different timescales, variable responses</p>
  <h3>When a thought takes a path</h3>
  <p class="lead">A colleague doesn't say hello. "They're avoiding me" and "Maybe they didn't see me" are two possible interpretations. The diagram illustrates how easy it can be to fall back into a habitual pattern or consider alternatives.</p>
  <p class="notice"><strong>How to read the model.</strong> Nodes, line weights, and frequencies are symbolic, with no correspondence to brain measurements or clinical percentages. Progress does not represent days or doses, and reaching the same final level in both examples does not imply equivalent clinical efficacy. Duration of benefit and relapse are not simulated.</p>
  <div class="modes" role="group" aria-label="Choose an illustrative scenario">
    <button class="mode" type="button" data-mode="baseline" aria-pressed="true"><strong>Initial state</strong><small>A habitual reading prevails.</small></button>
    <button class="mode" type="button" data-mode="ssri" aria-pressed="false"><strong>Gradual example · SSRI</strong><small>Early changes possible within days; fuller response often over weeks.</small></button>
    <button class="mode" type="button" data-mode="ketamine" aria-pressed="false"><strong>Rapid example · Ketamine</strong><small>In some patients, benefit may emerge within hours.</small></button>
  </div>
  <div class="settings">
    <div>
      <label for="tps-phase">Progress in the diagram</label>
      <input id="tps-phase" type="range" min="0" max="4" step="1" value="0" aria-valuetext="Start of diagram" disabled>
      <span class="phase-caption" id="tps-phase-copy">Start of diagram</span>
    </div>
    <div>
      <label for="tps-response">Pictured response</label>
      <select id="tps-response" disabled><option value="yes">Example with improvement</option><option value="no">Example without improvement</option></select>
    </div>
  </div>
  <p class="note" id="tps-scenario-note" aria-live="polite">The habitual pattern prevails, though alternatives remain possible. This is not a definition of depression.</p>
  <div class="network-wrap" role="region" aria-label="Diagram of interpretations, horizontally scrollable on small screens" tabindex="0">
<svg id="tps-network" viewBox="0 0 1000 500" role="img" aria-labelledby="tps-network-title tps-network-desc">
          <title id="tps-network-title">Metaphor of two possible interpretations of the same event</title>
          <desc id="tps-network-desc">Two pathways illustrate a negative pattern and an alternative reading. Nodes, frequencies, and line weights are symbolic: they do not represent identified neurons or clinical measurements.</desc>

          <defs>
            <filter id="tpsPulseGlow" x="-250%" y="-250%" width="500%" height="500%">
              <feGaussianBlur stdDeviation="8" result="blur"/>
              <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
            </filter>
            <marker id="tpsArrowNeg" markerWidth="8" markerHeight="8" refX="6" refY="3" orient="auto" markerUnits="userSpaceOnUse">
              <path d="M0,0 L0,6 L7,3 z" fill="#ff637d" opacity=".72"/>
            </marker>
          </defs>

          <!-- Background secondary connections -->
          <g aria-hidden="true">
            <path class="synapse ambient" d="M110 245 Q190 112 290 190"/>
            <path class="synapse ambient" d="M210 250 Q310 105 415 225"/>
            <path class="synapse ambient" d="M295 310 Q390 390 510 352"/>
            <path class="synapse ambient" d="M420 250 Q510 245 610 172"/>
            <path class="synapse ambient" d="M420 250 Q505 280 610 330"/>
            <path class="synapse ambient" d="M525 145 Q625 250 735 340"/>
            <path class="synapse ambient" d="M525 355 Q625 245 735 160"/>
            <path class="synapse ambient" d="M620 145 Q715 80 825 135"/>
            <path class="synapse ambient" d="M620 355 Q715 420 825 365"/>
          </g>

          <!-- Shared trunk -->
          <g id="tps-shared-paths">
            <path id="tps-s0" class="synapse shared" d="M78 250 C115 250 137 250 170 250"/>
            <path id="tps-s1" class="synapse shared" d="M190 250 C225 250 247 210 280 210"/>
            <path id="tps-s2" class="synapse shared" d="M300 210 C338 210 362 250 400 250"/>
          </g>

          <!-- Negative branch -->
          <g id="tps-negative-paths">
            <path id="tps-n0" class="synapse negative" d="M420 250 C455 250 462 164 500 154"/>
            <path id="tps-n1" class="synapse negative" d="M520 150 C554 150 566 112 600 120"/>
            <path id="tps-n2" class="synapse negative" d="M620 125 C660 128 678 160 715 160"/>
            <path id="tps-n3" class="synapse negative" d="M735 160 C772 160 793 138 825 138"/>
            <path id="tps-rumination-loop" class="synapse negative loop" d="M843 126 C838 55 684 48 604 104" marker-end="url(#tpsArrowNeg)"/>
          </g>

          <!-- Alternative branch -->
          <g id="tps-alternative-paths">
            <path id="tps-a0" class="synapse alternative" d="M420 250 C455 250 462 336 500 346"/>
            <path id="tps-a1" class="synapse alternative" d="M520 350 C554 350 566 388 600 380"/>
            <path id="tps-a2" class="synapse alternative" d="M620 375 C660 372 678 340 715 340"/>
            <path id="tps-a3" class="synapse alternative" d="M735 340 C772 340 793 362 825 362"/>
          </g>

          <!-- Symbolic metaphor nodes -->
          <g id="tps-node-input" class="neuron shared" transform="translate(62 250)"><circle class="halo" r="27"/><circle class="core" r="15"/><text class="node-label" y="38">event</text></g>
          <g id="tps-node-s1" class="neuron shared" transform="translate(180 250)"><circle class="halo" r="24"/><circle class="core" r="12"/><text class="node-label" y="35">attention</text></g>
          <g id="tps-node-s2" class="neuron shared" transform="translate(290 210)"><circle class="halo" r="24"/><circle class="core" r="12"/><text class="node-label" y="35">memory</text></g>
          <g id="tps-node-choice" class="neuron shared" transform="translate(410 250)"><circle class="halo" r="28"/><circle class="core" r="15"/><text class="node-label" y="39">interpretation</text></g>

          <g id="tps-node-n1" class="neuron negative" transform="translate(510 150)"><circle class="halo" r="25"/><circle class="core" r="12"/></g>
          <g id="tps-node-n2" class="neuron negative" transform="translate(610 122)"><circle class="halo" r="25"/><circle class="core" r="12"/></g>
          <g id="tps-node-n3" class="neuron negative" transform="translate(725 160)"><circle class="halo" r="25"/><circle class="core" r="12"/></g>
          <g id="tps-node-n4" class="neuron negative" transform="translate(835 138)"><circle class="halo" r="28"/><circle class="core" r="14"/></g>

          <g id="tps-node-a1" class="neuron alternative" transform="translate(510 350)"><circle class="halo" r="25"/><circle class="core" r="12"/></g>
          <g id="tps-node-a2" class="neuron alternative" transform="translate(610 378)"><circle class="halo" r="25"/><circle class="core" r="12"/></g>
          <g id="tps-node-a3" class="neuron alternative" transform="translate(725 340)"><circle class="halo" r="25"/><circle class="core" r="12"/></g>
          <g id="tps-node-a4" class="neuron alternative" transform="translate(835 362)"><circle class="halo" r="28"/><circle class="core" r="14"/></g>

          <text class="path-label negative" x="490" y="90">negative pattern</text>
          <text class="path-label alternative" x="490" y="425">alternative interpretation</text>

          <g class="rumination-badge" id="tps-rumination-badge" aria-hidden="true">
            <rect x="660" y="55" width="132" height="28" rx="14" fill="rgba(255,99,125,.13)" stroke="rgba(255,99,125,.38)"/>
            <text x="726" y="74" text-anchor="middle" fill="#ffacba" font-size="11" font-weight="800">RUMINATION ↻</text>
          </g>

          <g transform="translate(866 88)">
            <rect class="output-box negative" width="124" height="100" rx="14"/>
            <text class="output-title" x="14" y="27">"Avoiding me"</text>
            <text class="output-copy" x="14" y="50">I must have</text>
            <text class="output-copy" x="14" y="68">done something</text>
            <text class="output-copy" x="14" y="86">wrong.</text>
          </g>
          <g transform="translate(866 310)">
            <rect class="output-box alternative" width="124" height="118" rx="14"/>
            <text class="output-title" x="14" y="27">"Maybe…"</text>
            <text class="output-copy" x="14" y="50">They didn't</text>
            <text class="output-copy" x="14" y="68">see me: I lack</text>
            <text class="output-copy" x="14" y="86">enough</text>
            <text class="output-copy" x="14" y="104">information.</text>
          </g>

          <g id="tps-pulse" filter="url(#tpsPulseGlow)" aria-hidden="true">
            <circle id="tps-pulse-glow" r="15"/>
            <circle id="tps-pulse-core" r="5"/>
          </g>
        </svg>
  </div>
  <div class="controls">
    <button class="primary" id="tps-generate" type="button">Generate an example</button>
    <button id="tps-reset" type="button">Start over</button>
  </div>
  <div class="result" id="tps-result" aria-live="polite">
    <blockquote id="tps-result-text">Choose a scenario and generate an example. Any single outcome can vary even within the same scenario.</blockquote>
    <div class="stats">Examples generated: <span id="tps-total">0</span> · Negative reading: <span id="tps-negative-count">0</span> · Alternative: <span id="tps-alternative-count">0</span></div>
  </div>
  <p class="note">Greater ease in considering alternatives is the metaphor chosen here, not a measure of antidepressant efficacy. In reality, responses may be absent, partial, or broader, and must be evaluated over time.</p>
  <noscript><p>Interaction requires JavaScript. The diagram remains a metaphor: clinical timescales and limits of the evidence are described in the article text.</p></noscript>
</div>
<script>
(() => {
  'use strict';
  const root = document.getElementById('thought-path-sim');
  if (!root) return;
  const $ = selector => root.querySelector(selector);
  const buttons = [...root.querySelectorAll('[data-mode]')];
  const phase = $('#tps-phase');
  const response = $('#tps-response');
  const generate = $('#tps-generate');
  const pulse = $('#tps-pulse');
  const result = $('#tps-result');
  const resultText = $('#tps-result-text');
  const reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)');
  const state = { mode: 'baseline', negative: 0, alternative: 0, token: 0 };
  const phaseNames = ['Start of diagram', 'First illustrative step', 'Intermediate step', 'Later step', 'End of illustrative diagram'];
  // Arbitrary weights for a cognitive metaphor, never clinical response estimates.
  function bias() {
    if (state.mode === 'baseline' || response.value === 'no') return .80;
    const p = Number(phase.value);
    const change = state.mode === 'ssri' ? [0, .02, .08, .17, .25][p] : [0, .25, .25, .25, .25][p];
    return .80 - change;
  }
  function stop() {
    state.token += 1;
    generate.disabled = false;
    pulse.classList.remove('visible');
    root.querySelectorAll('.firing').forEach(node => node.classList.remove('firing'));
  }
  function clearExamples() {
    state.negative = 0;
    state.alternative = 0;
    $('#tps-total').textContent = '0';
    $('#tps-negative-count').textContent = '0';
    $('#tps-alternative-count').textContent = '0';
    result.className = 'result';
    resultText.textContent = 'Generate an example in the selected scenario. Frequencies are illustrative, not clinical data.';
  }
  function render() {
    const p = bias();
    root.style.setProperty('--neg-width', String(2 + p * 7));
    root.style.setProperty('--alt-width', String(2 + (1 - p) * 7));
    root.style.setProperty('--neg-opacity', String(.3 + p * .6));
    root.style.setProperty('--alt-opacity', String(.3 + (1 - p) * .6));
    buttons.forEach(button => button.setAttribute('aria-pressed', String(button.dataset.mode === state.mode)));
    phase.disabled = state.mode === 'baseline';
    response.disabled = state.mode === 'baseline';
    phase.setAttribute('aria-valuetext', phaseNames[Number(phase.value)]);
    $('#tps-phase-copy').textContent = phaseNames[Number(phase.value)];
    let note = 'The habitual pattern prevails, though alternatives remain possible. This is not a definition of depression.';
    if (state.mode !== 'baseline') {
      if (response.value === 'no') {
        note = 'Example without improvement: the pattern does not shift. Lack of response does not mean a lack of effort by the person.';
      } else if (Number(phase.value) === 0) {
        note = 'Starting point. Advance the slider to see the selected example; steps do not correspond to fixed clinical intervals.';
      } else if (state.mode === 'ssri') {
        note = 'Example of gradual change. Early effects are possible; fuller response is evaluated over longer timescales. The diagram does not measure serotonin, BDNF, or synapses.';
      } else {
        note = 'Example of rapid change. Initial benefit does not guarantee remission or durability; follow-up care requires clinical assessment.';
      }
    }
    $('#tps-scenario-note').textContent = note;
  }
  function flashNode(nodeId, token) {
    if (reduceMotion.matches) return;
    const node = $('#' + nodeId);
    if (!node) return;
    node.classList.add('firing');
    setTimeout(() => {
      if (token === state.token) node.classList.remove('firing');
    }, 220);
  }
  function travel(pathId, token) {
    if (reduceMotion.matches) return Promise.resolve(token === state.token);
    const path = $('#' + pathId);
    const length = path.getTotalLength();
    const start = performance.now();
    return new Promise(resolve => {
      function frame(now) {
        if (token !== state.token) { resolve(false); return; }
        const progress = Math.min((now - start) / 180, 1);
        const point = path.getPointAtLength(length * progress);
        pulse.setAttribute('transform', `translate(${point.x} ${point.y})`);
        if (progress < 1) requestAnimationFrame(frame);
        else resolve(true);
      }
      requestAnimationFrame(frame);
    });
  }
  async function generateExample() {
    if (generate.disabled) return;
    generate.disabled = true;
    const token = ++state.token;
    const kind = Math.random() < bias() ? 'negative' : 'alternative';
    const prefix = kind === 'negative' ? 'n' : 'a';
    $('#tps-pulse-glow').setAttribute('fill', kind === 'negative' ? '#ff637d80' : '#59dfbc80');
    $('#tps-pulse-core').setAttribute('fill', '#fff');
    if (!reduceMotion.matches) pulse.classList.add('visible');
    const steps = [
      ['tps-node-input', 'tps-s0'],
      ['tps-node-s1', 'tps-s1'],
      ['tps-node-s2', 'tps-s2'],
      ['tps-node-choice', `tps-${prefix}0`],
      [`tps-node-${prefix}1`, `tps-${prefix}1`],
      [`tps-node-${prefix}2`, `tps-${prefix}2`],
      [`tps-node-${prefix}3`, `tps-${prefix}3`],
    ];
    for (const [nodeId, pathId] of steps) {
      flashNode(nodeId, token);
      if (!(await travel(pathId, token))) return;
    }
    if (token !== state.token) return;
    flashNode(`tps-node-${prefix}4`, token);
    state[kind] += 1;
    $('#tps-total').textContent = String(state.negative + state.alternative);
    $('#tps-negative-count').textContent = String(state.negative);
    $('#tps-alternative-count').textContent = String(state.alternative);
    result.className = 'result ' + kind;
    resultText.textContent = kind === 'negative'
      ? '“They’re avoiding me. I probably did something wrong.”'
      : '“Maybe they didn’t see me or were distracted. I don’t have enough information to conclude it’s about me.”';
    pulse.classList.remove('visible');
    generate.disabled = false;
  }
  buttons.forEach(button => button.addEventListener('click', () => {
    if (state.mode === button.dataset.mode) return;
    stop();
    state.mode = button.dataset.mode;
    phase.value = state.mode === 'baseline' ? '0' : '1';
    clearExamples();
    render();
  }));
  [phase, response].forEach(control => control.addEventListener('input', () => {
    stop(); clearExamples(); render();
  }));
  generate.addEventListener('click', generateExample);
  $('#tps-reset').addEventListener('click', () => {
    stop(); state.mode = 'baseline'; phase.value = '0'; response.value = 'yes'; clearExamples(); render();
  });
  render();
})();
</script>
{% endraw %}

<aside class="ket-aside-box" aria-label="Aside box: do antidepressants barely work?">
  <style>
    .ket-aside-box {
      margin: 2rem 0;
      padding: 18px 20px;
      border: 1px solid #28415c;
      border-left: 4px solid #73b6ff;
      border-radius: 14px;
      background: #0e1d30;
      color: #dce8f4;
      box-shadow: 0 12px 32px rgba(0, 0, 0, 0.16);
      font: 15px/1.6 Inter, ui-sans-serif, system-ui, sans-serif;
    }
    .ket-aside-box .ket-aside-kicker {
      display: block;
      margin: 0 0 4px;
      font-size: 0.7rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      color: #a9cfff;
    }
    .ket-aside-box h4 {
      margin: 0 0 8px;
      font-size: 1.12rem;
      line-height: 1.3;
      color: #ffffff;
    }
    .ket-aside-box p {
      margin: 0;
      color: #dce8f4;
    }
  </style>
  <span class="ket-aside-kicker">Aside</span>
  <h4>Do antidepressants barely work?</h4>
  <p>It's not that they barely work: it's that they work very well in some people, poorly in others, and not at all in others still. This (<em>imho</em>) also happens because all depressions end up in the same diagnostic bucket. If we could better distinguish what people who respond really well to a specific antidepressant have in common—beyond comorbidities and treatment features—we would probably be telling a very different story.</p>
</aside>

## How much do we know about the antidepressant effect?

Let's start with patients before diving into receptors.

In a 2013 randomized trial of 73 people with treatment-resistant depression, a single intravenous infusion of ketamine was compared with midazolam (used as an active control). At 24 hours, **64%** of the ketamine group achieved a **response**—meaning at least a 50% drop in symptom scores—compared with **28%** of the control group.[^clinical]

In clinical practice we also distinguish **response** from **remission** (reaching a very low symptom threshold): reducing symptoms at 24 hours does not mean "64% are cured forever," and the real question becomes how long the improvement lasts and how to sustain it over time.[^clinical][^ema]

### Hours, when hours matter

Speed can make a real difference in a crisis. In an individual-participant meta-analysis, a single ketamine infusion reduced suicidal ideation as early as the next day, with measurable effects lasting up to a week and only partly explained by mood improvement.[^si]

In a trial of 156 patients hospitalized for suicidal ideation across different diagnoses, remission of ideation on day 3 was roughly twice as high with ketamine as with placebo. Yet the result varied sharply by diagnosis: the benefit was particularly clear in the bipolar disorder subgroup, whereas in the depressive disorders subgroup the difference was not statistically significant. The overall figure should therefore not be automatically generalized to unipolar depression. By week 6, the difference across the full sample was no longer statistically significant either.[^abbar]

Here too, a sharp distinction is needed: reducing suicidal ideation in the short term does not automatically mean reducing suicide attempts. Over the six weeks of that same trial, 6 people in the ketamine group and 8 in the placebo group attempted suicide; the study was not powered to detect a difference on that outcome.[^abbar] With esketamine, in trials of patients with active suicidal ideation and intent, depressive symptoms improved more rapidly than with placebo, whereas the specific measure of suicidality severity did not separate from control.[^aspire]

In the European Union, esketamine is also authorized for the acute short-term treatment of depressive symptoms that constitute a psychiatric emergency, within a structured clinical pathway.[^ema] A bridge, not a destination.

## One molecule, two mirror images

Racemic ketamine contains equal parts of two enantiomers: molecules made of the exact same atoms connected in the same order, but arranged in space as mirror images, like a right hand and a left hand.

<div class="ket-enantiomers-wrap">
  <style>
    .ket-enantiomers-wrap {
      margin: 1.75rem 0;
      border: 1px solid #28415c;
      border-radius: 16px;
      background: #0e1d30;
      color: #edf5ff;
      box-shadow: 0 12px 32px rgba(0, 0, 0, 0.18);
      overflow-x: auto;
      font: 15px/1.55 Inter, ui-sans-serif, system-ui, sans-serif;
    }
    .ket-enantiomers-table {
      width: 100%;
      border-collapse: collapse;
      margin: 0;
      font-size: 0.94rem;
      line-height: 1.55;
      color: #edf5ff;
      background: transparent;
      border: 0;
    }
    .ket-enantiomers-table thead th {
      text-align: left;
      padding: 13px 16px;
      font-size: 0.72rem;
      font-weight: 800;
      text-transform: uppercase;
      letter-spacing: 0.09em;
      color: #a9cfff;
      background: #10243a;
      border: 0;
      border-bottom: 1px solid #28415c;
    }
    .ket-enantiomers-table tbody tr {
      background: transparent !important;
    }
    .ket-enantiomers-table tbody td {
      padding: 15px 16px;
      vertical-align: top;
      border: 0;
      border-bottom: 1px solid #28415c;
      color: #dce8f4;
      background: transparent !important;
    }
    .ket-enantiomers-table tbody td strong {
      color: #ffffff;
    }
    .ket-enantiomers-table tbody tr:last-child td {
      border-bottom: 0;
    }
    .ket-pill {
      display: inline-block;
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
      font-size: 0.84rem;
      font-weight: 700;
      padding: 3px 9px;
      border-radius: 7px;
      white-space: nowrap;
    }
    .ket-pill.s-form {
      color: #fde68a;
      background: rgba(245, 185, 66, 0.16);
      border: 1px solid rgba(245, 185, 66, 0.45);
    }
    .ket-enantiomers-table .col-name {
      font-weight: 700;
      color: #ffffff;
      white-space: nowrap;
    }
    @media (max-width: 560px) {
      .ket-enantiomers-table thead { display: none; }
      .ket-enantiomers-table,
      .ket-enantiomers-table tbody,
      .ket-enantiomers-table tr,
      .ket-enantiomers-table td { display: block; width: 100%; }
      .ket-enantiomers-table tbody tr {
        padding: 12px 14px;
        border-bottom: 1px solid #28415c;
      }
      .ket-enantiomers-table tbody tr:last-child { border-bottom: 0; }
      .ket-enantiomers-table tbody td {
        padding: 5px 0;
        border: 0;
      }
      .ket-enantiomers-table tbody td::before {
        content: attr(data-label);
        display: block;
        font-size: 0.68rem;
        font-weight: 800;
        text-transform: uppercase;
        letter-spacing: 0.08em;
        color: #a9cfff;
        margin-bottom: 3px;
      }
    }
  </style>
  <table class="ket-enantiomers-table">
    <thead>
      <tr>
        <th scope="col">Form</th>
        <th scope="col">Name</th>
        <th scope="col">Key properties to remember</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td data-label="Form"><span class="ket-pill s-form">S(+)-ketamine</span></td>
        <td class="col-name" data-label="Name">Esketamine</td>
        <td data-label="Key properties to remember">It is <strong>dextrorotatory</strong> and acts as an <strong>NMDA receptor channel blocker</strong>.</td>
      </tr>
    </tbody>
  </table>
</div>

*For sticklers: R/S do not, in general, mean dextrorotatory/levorotatory. They describe absolute spatial configuration, whereas the +/− sign indicates experimentally measured optical rotation. Esketamine has the S configuration and positive optical rotation: hence S(+).*[^stereo][^structure]

What is approved in Europe as a nasal spray for treatment-resistant depression is **esketamine** (combined with an SSRI or SNRI, after at least two antidepressants have failed, and always under strict medical supervision).[^ema] Intravenous racemic ketamine, by contrast, is used **off-label** in hospital and specialist clinical settings.[^euda]

## How does it work? The dose paradox

So we've realized that we haven't fully understood depression. For decades we focused almost exclusively on serotonin, norepinephrine, and dopamine; ketamine instead barges straight into the **glutamate** system, the brain's main excitatory neurotransmitter.

Specifically, ketamine acts like a **plug inside the NMDA receptor channel**: it enters the pore and blocks the flow of ions.[^structure][^nmda]

And here a beautiful paradox arises: the NMDA receptor is an *excitatory* receptor. If you plug it, you should shut down brain activity, right?
And indeed, at **high doses** it acts as an anesthetic. Yet at **low doses** it does the opposite: it *turns up* transmission in parts of the cortex.

### Inhibiting inhibition: weights, counterweights, mirrors, and levers

Our brain is a delicate balance of weights and counterweights.
This is the slightly more technical paragraph. One of the most studied hypotheses for subanesthetic doses involves certain **GABAergic interneurons**, the "brakes" of the cortex: their job is to keep excitatory pyramidal neurons in check. In rodents, ketamine appears to quiet down some of these brakes more than it quiets the excitatory neurons they control.[^gaba] It is not an exclusive target (ketamine also plugs NMDA receptors on pyramidal neurons), but the net balance shifts.

If you block the brake—that is, **inhibit inhibition**—you get excitation: disinhibition. In animal models, the released pyramidal neurons increase glutamate release, which activates another receptor, **AMPA**, and sets off cellular signaling pathways linked to neuroplasticity such as **BDNF/TrkB** and **mTORC1**.[^gaba]

Nice cascade. The problem is translating it to humans. In a small clinical study, patients received rapamycin (which blocks mTORC1) before ketamine, and the antidepressant effect at 24 hours did not disappear.[^mtor] That does not refute the hypothesis—partly because oral rapamycin may not cross into the brain in sufficient amounts—but it is a good reminder that an elegant cascade in mice is not yet a complete explanation in patients.

When the dose climbs, the blockade becomes much more widespread and, through a complicated system of mirrors and levers, activity across the entire cortical network reorganizes: some neuronal populations shut down while others that were previously silent light up.[^network] That is dissociative anesthesia (and, in non-medical or high-exposure settings, the extreme dissociative state colloquially known as a *K-hole*).

Picture a basin with a narrow pipe near the bottom and a wide pipe higher up. When the fluid level is low, flow goes mainly through the lower pipe (easier to engage, meaning higher affinity); as we raise the dose and the level rises, the upper pipe—which has much larger capacity—kicks in massively, completely changing the net outcome across the network:

{% raw %}
<div id="para-sim">
  <style>
    #para-sim {
      --bg:#0E1520; --panel:#17202E; --border:#26344A; --text:#E4EAF2;
      --muted:#8A99AD; --teal:#3DD6C4; --coral:#FF6B5C; --gold:#F2C14E;
      --red:#FF4059; --blue:#91BAEE; --mono:ui-monospace,SFMono-Regular,Consolas,monospace;
      color-scheme:dark; font:15px/1.6 system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
      background:var(--bg); color:var(--text);
      border:1px solid var(--border); border-radius:22px; padding:24px; margin:2rem 0;
    }
    #para-sim *, #para-sim *::before, #para-sim *::after { box-sizing:border-box; }
    #para-sim button, #para-sim input { font:inherit; }
    #para-sim button { cursor:pointer; color:var(--text); border:1px solid #3b4c64; border-radius:8px; background:#1D293B; padding:8px 12px; }
    #para-sim button:hover { background:#293950; border-color:#7891ae; }
    #para-sim button:disabled { opacity:.45; cursor:default; }
    #para-sim button:focus-visible, #para-sim input:focus-visible, #para-sim summary:focus-visible, #para-sim a:focus-visible {
      outline:3px solid var(--gold); outline-offset:5px;
    }
    #para-sim a { color:var(--blue); text-underline-offset:3px; }
    #para-sim .mono, #para-sim output { font-family:var(--mono); font-variant-numeric:tabular-nums; }
    #para-sim .eyebrow { font:11px/1.5 var(--mono); letter-spacing:.15em; text-transform:uppercase; color:var(--muted); }
    #para-sim .ps-hero { padding:0 0 20px; display:flex; align-items:flex-end; justify-content:space-between; gap:20px; flex-wrap:wrap; }
    #para-sim .ps-hero .eyebrow { color:var(--teal); }
    #para-sim .ps-title { font-size:clamp(24px,3.5vw,34px); line-height:1.1; letter-spacing:-.035em; margin:8px 0 10px; font-weight:700; color:var(--text); }
    #para-sim .intro { max-width:620px; color:#B6C3D3; margin:0; font-size:14.5px; }
    #para-sim .panel { border:1px solid var(--border); border-radius:14px; background:var(--panel); }
    #para-sim .dose-panel { padding:20px 22px 17px; margin-bottom:18px; position:relative; overflow:hidden; }
    #para-sim .dose-panel::before { content:""; position:absolute; top:0; left:0; right:0; height:2px; background:linear-gradient(90deg,var(--teal),var(--gold) 45%,var(--coral)); }
    #para-sim .dose-top { display:flex; justify-content:space-between; align-items:center; gap:16px; flex-wrap:wrap; }
    #para-sim .dose-title { display:flex; gap:19px; align-items:center; }
    #para-sim .dose-title label { display:block; font-weight:650; font-size:15px; color:var(--text); }
    #para-sim #ps-dose-value { font-size:36px; line-height:1; letter-spacing:-.04em; color:white; }
    #para-sim .unit { font-size:18px; color:var(--muted); }
    #para-sim .dose-hint { color:var(--muted); font-size:11px; }
    #para-sim .state-badge { display:flex; align-items:center; gap:8px; padding:7px 10px; border:1px solid var(--border); border-radius:30px; font:11px var(--mono); color:var(--teal); }
    #para-sim .state-badge::before { content:""; width:6px; height:6px; background:currentColor; border-radius:50%; }
    #para-sim .state-badge[data-state="damage"] { color:var(--red); border-color:#6d3043; background:#331f30; }
    #para-sim .state-badge[data-state="no-equilibrium"] { color:var(--gold); border-color:#695634; background:#302b24; }
    #para-sim .range-area { position:relative; margin-top:17px; }
    #para-sim input[type="range"] { display:block; width:100%; height:30px; margin:0; accent-color:var(--teal); cursor:ew-resize; }
    #para-sim #ps-dose { appearance:none; -webkit-appearance:none; background:transparent; position:relative; z-index:2; }
    #para-sim #ps-dose::-webkit-slider-runnable-track { height:6px; border-radius:8px; background:linear-gradient(90deg,#3DD6C4 0%,#3DD6C4 var(--threshold-position,12.3%),#FF6B5C var(--threshold-position,12.3%),#FF6B5C var(--capacity-position,50%),#354154 var(--capacity-position,50%)); }
    #para-sim #ps-dose::-moz-range-track { height:6px; border-radius:8px; background:linear-gradient(90deg,#3DD6C4 0%,#3DD6C4 var(--threshold-position,12.3%),#FF6B5C var(--threshold-position,12.3%),#FF6B5C var(--capacity-position,50%),#354154 var(--capacity-position,50%)); }
    #para-sim #ps-dose::-webkit-slider-thumb { appearance:none; -webkit-appearance:none; width:21px; height:21px; margin-top:-7.5px; border:4px solid #E4EAF2; border-radius:50%; background:#17202E; box-shadow:0 0 0 5px #e4eaf212; }
    #para-sim #ps-dose::-moz-range-thumb { width:14px; height:14px; border:4px solid #E4EAF2; border-radius:50%; background:#17202E; }
    #para-sim .ticks { display:flex; justify-content:space-between; font:10px var(--mono); color:var(--muted); margin:1px 7px 11px; }
    #para-sim .dose-bottom { display:flex; justify-content:space-between; align-items:center; flex-wrap:wrap; gap:10px; }
    #para-sim .presets { display:flex; flex-wrap:wrap; gap:7px; }
    #para-sim .presets button { font-size:11px; padding:6px 10px; }
    #para-sim .threshold-note { color:var(--gold); font:11px var(--mono); }
    #para-sim .disclaimer { color:var(--muted); font-size:11px; margin:12px 0 0; }
    #para-sim .dashboard { display:grid; grid-template-columns:1fr; gap:18px; align-items:stretch; }
    #para-sim .panel-head { display:flex; justify-content:space-between; gap:15px; align-items:start; padding:20px 22px 0; }
    #para-sim .ps-h2 { font-size:19px; line-height:1.3; font-weight:600; letter-spacing:-.025em; margin:5px 0 0; color:var(--text); }
    #para-sim .icon-button { font-size:11px; padding:6px 9px; white-space:nowrap; }
    #para-sim .diagram { width:100%; height:auto; display:block; }
    #para-sim .diagram text { font-family:system-ui,sans-serif; }
    #para-sim .diagram .number { font-family:var(--mono); font-variant-numeric:tabular-nums; }
    #para-sim .diagram .svg-title { font:600 11px var(--mono); letter-spacing:.08em; }
    #para-sim .diagram .svg-small { font-size:10px; }
    #para-sim .stream { stroke-dasharray:5 9; animation:psStream 1.1s linear infinite; }
    #para-sim .stream.slow { animation-duration:1.7s; }
    @keyframes psStream { to { stroke-dashoffset:-56; } }
    #para-sim.motion-off .stream { animation:none; }
    #para-sim .diagram-note { color:var(--muted); font-size:11px; line-height:1.6; margin:-3px 22px 14px; }
    #para-sim .readouts { margin:0 22px 15px; display:grid; grid-template-columns:repeat(4,1fr); border:1px solid var(--border); border-radius:9px; }
    #para-sim .readout { padding:11px 12px; min-width:0; }
    #para-sim .readout+.readout { border-left:1px solid var(--border); }
    #para-sim .readout dt { color:var(--muted); font-size:10px; margin:0 0 4px; }
    #para-sim .readout dd { font:20px var(--mono); margin:0; color:var(--teal); }
    #para-sim .readout:nth-child(2) dd { color:var(--coral); }
    #para-sim .readout:nth-child(3) dd { color:var(--gold); }
    #para-sim .readout:nth-child(4) dd { color:var(--red); }
    #para-sim .readout small { color:var(--muted); font-size:9px; display:block; margin-top:3px; }
    #para-sim .live-explanation { margin:0 22px 20px; padding:11px 13px; border-left:2px solid var(--gold); background:#101A28; color:#B8C6D7; font-size:12px; min-height:56px; border-radius:0 5px 5px 0; }
    #para-sim .charts-panel { padding-bottom:7px; }
    #para-sim .legend { display:flex; gap:15px; flex-wrap:wrap; margin:13px 22px 12px; color:var(--muted); font-size:10px; }
    #para-sim .legend span::before { content:""; display:inline-block; width:12px; height:3px; margin-right:5px; vertical-align:middle; background:var(--swatch); border-radius:1px; }
    #para-sim .chart-block { padding:0 19px; margin-bottom:5px; }
    #para-sim .chart-title { display:flex; align-items:baseline; justify-content:space-between; gap:8px; padding:0 4px; }
    #para-sim .chart-title h4 { font-size:12px; font-weight:500; margin:0; color:var(--text); }
    #para-sim .chart-title output { font-size:11px; color:var(--muted); }
    #para-sim .chart { display:block; width:100%; height:auto; overflow:visible; }
    #para-sim .chart text { font-family:var(--mono); font-size:10px; fill:var(--muted); }
    #para-sim .chart-note { font-size:10px; color:var(--muted); line-height:1.5; margin:0 22px 12px; }
    #para-sim .bottom-grid { display:grid; grid-template-columns:1fr 1fr; gap:14px; margin-top:18px; align-items:start; }
    #para-sim details.settings { padding:0 18px; }
    #para-sim summary { cursor:pointer; padding:16px 0; font-size:13px; font-weight:600; color:var(--text); }
    #para-sim summary .eyebrow { margin-left:8px; font-size:9px; }
    #para-sim .settings-content { border-top:1px solid var(--border); padding:15px 0 18px; }
    #para-sim .param { margin-bottom:16px; }
    #para-sim .param-heading { display:flex; justify-content:space-between; gap:12px; font-size:12px; }
    #para-sim .param-heading output { font-size:14px; }
    #para-sim .param p { margin:5px 0 3px; color:var(--muted); font-size:11px; }
    #para-sim #ps-vmax1 { accent-color:var(--teal); }
    #para-sim #ps-rgsh { accent-color:var(--gold); }
    #para-sim .param:nth-child(2) output { color:var(--gold); }
    #para-sim .fixed-params { color:var(--muted); font:10px/1.7 var(--mono); }
    #para-sim .settings-footer { display:flex; justify-content:space-between; align-items:center; gap:12px; flex-wrap:wrap; }
    #para-sim .settings-footer button { font-size:11px; }
    #para-sim .comparison { padding:16px 18px; background:linear-gradient(115deg,#202631,var(--panel)); }
    #para-sim .comparison .ps-h2 { font-size:16px; margin-top:6px; }
    #para-sim .comparison p { color:#B8C6D7; font-size:12px; margin:10px 0; }
    #para-sim .comparison strong { color:var(--text); }
    #para-sim .comparison .numbers { display:flex; align-items:center; gap:14px; margin:12px 0; }
    #para-sim .comparison .numbers span { display:block; font:20px var(--mono); }
    #para-sim .comparison .numbers small { display:block; color:var(--muted); font-size:10px; }
    #para-sim .comparison .numbers b { color:var(--muted); font-weight:400; }
    #para-sim .comparison button { font-size:11px; }
    #para-sim .sr-only { position:absolute; width:1px; height:1px; margin:-1px; padding:0; overflow:hidden; clip:rect(0,0,0,0); white-space:nowrap; border:0; }
    @media(max-width:640px) {
      #para-sim { padding:16px; }
      #para-sim .bottom-grid { grid-template-columns:1fr; }
      #para-sim .readouts { grid-template-columns:repeat(2,1fr); margin-left:15px; margin-right:15px; }
      #para-sim .readout:nth-child(3) { border-left:0; }
      #para-sim .readout:nth-child(n+3) { border-top:1px solid var(--border); }
      #para-sim .diagram-note, #para-sim .live-explanation { margin-left:15px; margin-right:15px; }
    }
    @media(prefers-reduced-motion:reduce) { #para-sim *, #para-sim *::before, #para-sim *::after { animation:none !important; transition:none !important; } }
  </style>

  <div class="ps-hero">
    <div>
      <div class="eyebrow">Ketamine · Affinity and network-threshold metaphor</div>
      <h3 class="ps-title">The hidden threshold of the dose.</h3>
      <p class="intro">Two targets with different sensitivity in the circuit and a finite margin of compensation. Move the dose and watch when releasing the brake (disinhibition) turns into shutting down or disconnecting the network.</p>
    </div>
  </div>

  <section class="panel dose-panel" aria-labelledby="ps-dose-label">
    <div class="dose-top">
      <div class="dose-title">
        <div>
          <label id="ps-dose-label" for="ps-dose">Input dose / exposure</label>
          <div class="dose-hint">Inflow D · normalized units</div>
        </div>
        <div><output id="ps-dose-value" for="ps-dose">1.00</output><span class="unit"> ×</span></div>
      </div>
      <span class="state-badge" id="ps-state-badge" data-state="protected">Subanesthetic window</span>
    </div>
    <div class="range-area">
      <input id="ps-dose" type="range" min="0" max="10" step="0.01" value="1" aria-describedby="ps-units-note ps-dose-keyboard">
      <div class="ticks" aria-hidden="true"><span>0</span><span>2</span><span>4</span><span>6</span><span>8</span><span>10×</span></div>
    </div>
    <div class="dose-bottom">
      <div class="presets" aria-label="Example doses">
        <button type="button" data-dose="1">Subanesthetic · 1×</button>
        <button type="button" id="ps-near-threshold">Just above threshold</button>
        <button type="button" data-dose="3.5">High exposure · 3.5×</button>
      </div>
      <div class="threshold-note">Model threshold <output id="ps-threshold">1.23×</output></div>
    </div>
    <p class="disclaimer" id="ps-units-note"><strong>1× is an educational reference, not a dose in mg or a universal clinical cutoff.</strong> The basin is a hydraulic metaphor for how two targets with different sensitivities respond as concentration rises.</p>
    <span id="ps-dose-keyboard" class="sr-only">Use arrow keys to change the dose; Home sets zero and End sets ten.</span>
  </section>

  <div class="dashboard">
    <section class="panel" aria-labelledby="ps-basin-title">
      <div class="panel-head">
        <div>
          <div class="eyebrow">01 / The path of the molecule</div>
          <h4 class="ps-h2" id="ps-basin-title">One basin, two NMDA targets.</h4>
        </div>
        <button type="button" class="icon-button" id="ps-motion" aria-pressed="true">Animations: on</button>
      </div>
      <svg class="diagram" id="ps-basin" viewBox="0 0 700 500" role="img" aria-labelledby="ps-diagram-title ps-diagram-desc">
        <title id="ps-diagram-title">Concentration basin, two NMDA targets, and downstream network compensation</title>
        <desc id="ps-diagram-desc">The low, narrow pipe represents blockade on GABAergic brakes (more sensitive at low doses). The high, wide pipe represents direct blockade on excitatory pyramidal neurons. When direct blockade exceeds network compensation, disconnection prevails.</desc>
        <defs>
          <pattern id="ps-tank-grid" width="23" height="23" patternUnits="userSpaceOnUse"><path d="M23 0H0V23" fill="none" stroke="#26344A" stroke-width=".5"/></pattern>
          <linearGradient id="ps-water-gradient" x1="0" y1="0" x2="0" y2="1"><stop stop-color="#91BAEE" stop-opacity=".28"/><stop offset="1" stop-color="#3F759B" stop-opacity=".12"/></linearGradient>
          <linearGradient id="ps-gsh-gradient" x1="0" y1="0" x2="0" y2="1"><stop stop-color="#F2C14E" stop-opacity=".55"/><stop offset="1" stop-color="#F2C14E" stop-opacity=".14"/></linearGradient>
          <clipPath id="ps-tank-clip"><rect x="180" y="61" width="228" height="264" rx="4"/></clipPath>
          <clipPath id="ps-gsh-clip"><rect x="492" y="313" width="120" height="72" rx="3"/></clipPath>
        </defs>
        <text x="27" y="47" fill="#3DD6C4" class="svg-title">PATH 1 · GABA BRAKES</text>
        <text x="27" y="66" fill="#8A99AD" class="svg-small">High sensitivity · low capacity</text>
        <text x="27" y="84" fill="#3DD6C4" class="number svg-small" id="ps-safe-param">Km 0.30 / Vmax 1.00</text>
        <text x="458" y="47" fill="#FF6B5C" class="svg-title">PATH 2 · PYRAMIDAL</text>
        <text x="458" y="66" fill="#8A99AD" class="svg-small">Low sensitivity · high capacity</text>
        <text x="458" y="84" fill="#FF6B5C" class="number svg-small">Km 4.00 / Vmax 4.00</text>
        <rect x="178" y="60" width="232" height="267" rx="6" fill="#101A28"/>
        <rect x="180" y="61" width="228" height="264" fill="url(#ps-tank-grid)"/>
        <g clip-path="url(#ps-tank-clip)"><rect id="ps-water" x="180" y="303.56" width="228" height="21.44" fill="url(#ps-water-gradient)"/><path id="ps-water-line" d="M180 303.56H408" stroke="#91BAEE" stroke-width="1.5"/></g>
        <path d="M178 61V321Q178 329 186 329H402Q410 329 410 321V61" fill="none" stroke="#62778F" stroke-width="3"/>
        <g fill="#8A99AD" class="number svg-small"><text x="190" y="319">0</text><text x="190" y="190">2.75</text><text x="190" y="77">5.50</text></g>
        <path d="M165 325h10M165 193h10M165 61h10" stroke="#62778F"/>
        <text x="294" y="354" fill="#8A99AD" text-anchor="middle" class="svg-small">Circuit concentration</text>
        <text x="294" y="382" fill="#E4EAF2" text-anchor="middle" class="number" font-size="24" id="ps-concentration">C = 0.45</text>
        <text x="294" y="401" fill="#91BAEE" text-anchor="middle" class="svg-small" id="ps-level-note">Level proportional to C</text>
        <path d="M294 14V55" stroke="#3B4C64" stroke-width="13"/>
        <path id="ps-inlet" d="M294 20V302" fill="none" stroke="#91BAEE" stroke-width="3" class="stream"/>
        <text x="315" y="27" fill="#91BAEE" class="number svg-small" id="ps-inlet-label">D = 1.00</text>
        <g id="ps-above-scale" opacity="0"><path d="M189 62l9 -7 10 7 10 -7 10 7 10 -7 10 7M340 62l9 -7 10 7 10 -7 10 7 10 -7 10 7" stroke="#91BAEE" stroke-width="2" fill="none"/><text x="294" y="81" text-anchor="middle" fill="#C4DCFA" class="svg-small">LEVEL ABOVE SCALE</text></g>
        <path id="ps-pipe1-border" d="M180 310.6H111V379" fill="none" stroke="#456264" stroke-width="20" stroke-linejoin="round"/>
        <path id="ps-pipe1" d="M180 310.6H111V379" fill="none" stroke="#182C34" stroke-width="14" stroke-linejoin="round"/>
        <path id="ps-flow1" d="M180 310.6H111V430" fill="none" stroke="#3DD6C4" stroke-width="8" stroke-linejoin="round" class="stream slow"/>
        <ellipse id="ps-pipe1-mouth" cx="180" cy="310.6" rx="4" ry="7" fill="#153D3D" stroke="#3DD6C4"/>
        <text x="32" y="289" fill="#3DD6C4" class="number svg-small">Height Km₁ = 0.30</text>
        <path d="M410 133H552V286" fill="none" stroke="#674443" stroke-width="34" stroke-linejoin="round"/>
        <path d="M410 133H552V286" fill="none" stroke="#342831" stroke-width="28" stroke-linejoin="round"/>
        <path id="ps-flow2" d="M410 133H552V322" fill="none" stroke="#FF6B5C" stroke-width="9" stroke-linejoin="round" class="stream"/>
        <ellipse cx="410" cy="133" rx="8" ry="14" fill="#4B2A31" stroke="#FF6B5C"/>
        <text x="429" y="109" fill="#FF6B5C" class="number svg-small">Height Km₂ = 4.00</text>
        <path d="M392 280V151" stroke="#FF6B5C" stroke-opacity=".35" stroke-dasharray="3 5"/>
        <text x="394" y="218" fill="#A7B7CA" class="svg-small" text-anchor="end">Engaged too</text>
        <text x="394" y="233" fill="#8A99AD" class="svg-small" text-anchor="end">whenever C &gt; 0</text>
        <text x="577" y="231" fill="#FF6B5C" class="number" font-size="15" id="ps-napqi-flow">0.402</text>
        <text x="577" y="247" fill="#8A99AD" class="svg-small">pyramidal block</text>
        <rect x="489" y="309" width="126" height="79" rx="4" fill="#141D28"/>
        <g clip-path="url(#ps-gsh-clip)"><rect id="ps-gsh-water" x="492" y="332.4" width="120" height="52.6" fill="url(#ps-gsh-gradient)"/></g>
        <path d="M488 308V383Q488 390 495 390H609Q616 390 616 383V308" fill="none" stroke="#F2C14E" stroke-width="3"/>
        <path d="M485 313H620" stroke="#F2C14E" stroke-width="1" stroke-dasharray="3 5" opacity=".7"/>
        <text x="552" y="357" text-anchor="middle" fill="#F5DA97" class="number" font-size="18" id="ps-gsh-usage">73%</text>
        <text x="552" y="375" text-anchor="middle" fill="#D9C28F" class="svg-small">margin engaged</text>
        <text x="552" y="412" text-anchor="middle" fill="#F2C14E" class="svg-title">03 · NETWORK BUFFER</text>
        <text x="552" y="430" text-anchor="middle" fill="#8A99AD" class="number svg-small" id="ps-gsh-capacity">Rnet = 0.55</text>
        <path id="ps-spill" d="M613 316H650V438" stroke="#FF4059" fill="none" stroke-linejoin="round" stroke-width="0" class="stream" opacity="0"/>
        <path id="ps-liver" d="M633 453C637 443 653 444 664 449L679 453C672 457 667 467 653 470L634 467Z" fill="#362431" stroke="#5D3442"/>
        <text x="650" y="489" text-anchor="middle" fill="#FF4059" class="svg-small">dissociation</text>
        <circle cx="111" cy="453" r="14" fill="#163C3D" stroke="#3DD6C4" stroke-opacity=".45"/>
        <path d="M105 453l4 4 8 -9" fill="none" stroke="#3DD6C4" stroke-width="2"/>
        <text x="111" y="486" text-anchor="middle" fill="#8A99AD" class="svg-small">Disinhibition (AMPA)</text>
        <text x="294" y="447" text-anchor="middle" fill="#8A99AD" class="number svg-small" id="ps-mass-balance">inflow 1.00 = outflow 1.00</text>
        <text x="294" y="464" text-anchor="middle" fill="#8A99AD" class="svg-small">Two NMDA targets. The threshold lies downstream.</text>
      </svg>
      <p class="diagram-note">Pipe height marks Km, <strong>not an all-or-none cutoff</strong>: pyramidal neurons (upper pipe) also undergo some blockade even at low doses, but at low concentrations discharge through the GABAergic brakes prevails.</p>
      <dl class="readouts">
        <div class="readout"><dt>GABA brakes · f₁</dt><dd id="ps-f1-value">0.598</dd><small>disinhibitory drive</small></div>
        <div class="readout"><dt>Pyramidal · f₂</dt><dd id="ps-f2-value">0.402</dd><small>excitatory block</small></div>
        <div class="readout"><dt>Network buffer</dt><dd id="ps-gsh-value">73%</dd><small id="ps-gsh-readout-capacity">of Rnet = 0.55</small></div>
        <div class="readout"><dt>Disconnection</dt><dd id="ps-damage-value">0.000</dd><small>max(0, f₂ − Rnet)</small></div>
      </dl>
      <p class="live-explanation" id="ps-live-explanation">Direct blockade on pyramidal neurons is still contained: releasing the GABAergic brake prevails (subanesthetic disinhibition window).</p>
    </section>

    <section class="panel charts-panel" aria-labelledby="ps-charts-title">
      <div class="panel-head">
        <div>
          <div class="eyebrow">02 / Same equations, three views</div>
          <h4 class="ps-h2" id="ps-charts-title">Where the network response shifts.</h4>
        </div>
      </div>
      <div class="legend"><span style="--swatch:var(--teal)">GABA brakes</span><span style="--swatch:var(--coral)">Pyramidal</span><span style="--swatch:var(--gold)">Network threshold</span></div>
      <div class="chart-block"><div class="chart-title"><h4>Engagement of the two NMDA targets</h4><output id="ps-flow-chart-value">D = 1.00×</output></div><svg id="ps-flow-chart" class="chart" viewBox="0 0 520 159" role="img" aria-label="Engagement of the two targets versus dose; the GABAergic brake saturates first."></svg></div>
      <div class="chart-block"><div class="chart-title"><h4>Share on direct pyramidal block · f₂ / D</h4><output id="ps-fraction-value">40.2%</output></div><svg id="ps-fraction-chart" class="chart" viewBox="0 0 520 159" role="img" aria-label="Fraction of the effect falling directly on excitatory pyramidal neurons."></svg></div>
      <div class="chart-block"><div class="chart-title"><h4>Cortical disconnection / anesthesia</h4><output id="ps-damage-chart-value">0.000</output></div><svg id="ps-damage-chart" class="chart" viewBox="0 0 520 159" role="img" aria-label="Disconnection stays contained within the network buffer; past the threshold it rises steeply."></svg></div>
      <p class="chart-note">Horizontal axis: dose D (×). Bright line: current dose. Gold: crossing the subanesthetic margin. Hatched area: full saturation.</p>
    </section>
  </div>

  <div class="bottom-grid">
    <details class="panel settings">
      <summary>Explore parameters <span class="eyebrow">Capacity and buffer</span></summary>
      <div class="settings-content">
        <div class="param"><div class="param-heading"><label for="ps-vmax1">Weight of GABAergic brake · Vmax₁</label><output id="ps-vmax1-value" for="ps-vmax1">1.00</output></div><input type="range" id="ps-vmax1" min="0.25" max="2" step="0.05" value="1"><p>A wider lower pipe absorbs a larger share before saturating.</p></div>
        <div class="param"><div class="param-heading"><label for="ps-rgsh">Network buffer · Rnet</label><output id="ps-rgsh-value" for="ps-rgsh">0.55</output></div><input type="range" id="ps-rgsh" min="0" max="2" step="0.05" value="0.55"><p>Shrink the margin and the dissociative threshold shifts left.</p></div>
        <div class="settings-footer"><div class="fixed-params">Fixed: Km₁ = 0.30 · Km₂ = 4.00<br>Vmax₂ = 4.00 · Cmax = 1,000,000</div><button id="ps-reset" type="button">Reset all</button></div>
      </div>
    </details>
    <section class="panel comparison" aria-labelledby="ps-comparison-title">
      <div class="eyebrow">An experiment near the threshold</div>
      <h4 class="ps-h2" id="ps-comparison-title">Twice the dose. How much disconnection?</h4>
      <div class="numbers">
        <div><span id="ps-comparison-dose-a">1.35×</span><small>just above threshold</small></div>
        <b aria-hidden="true">→</b>
        <div><span id="ps-comparison-dose-b">2.71×</span><small>doubled dose</small></div>
      </div>
      <p id="ps-comparison-copy">Disconnection increases more than twofold.</p>
      <button id="ps-compare-dose" type="button">Show first dose</button>
    </section>
  </div>
  <div class="sr-only" role="status" aria-live="polite" aria-atomic="true" id="ps-accessible-status"></div>
</div>
<script>
(() => {
  'use strict';
  const root = document.getElementById('para-sim');
  if (!root) return;
  const Modello = (() => {
    const DEFAULTS = Object.freeze({km1:.3, vmax1:1, km2:4, vmax2:4, rgsh:.55});
    const CMAX = 1e6;
    function fluxes(c,p) {
      return {f1:p.vmax1*c/(p.km1+c), f2:p.vmax2*c/(p.km2+c)};
    }
    function solve(d,p=DEFAULTS) {
      if (!Number.isFinite(d) || d<0 || !Number.isFinite(p.km1) || p.km1<=0 || !Number.isFinite(p.km2) || p.km2<=0 || !Number.isFinite(p.vmax1) || p.vmax1<=0 || !Number.isFinite(p.vmax2) || p.vmax2<=0 || !Number.isFinite(p.rgsh) || p.rgsh<0) throw new RangeError('Parameters out of domain');
      const capacity=p.vmax1+p.vmax2;
      const atMax=fluxes(CMAX,p);
      if (d>=capacity || d>atMax.f1+atMax.f2) return {equilibrium:false,c:null,f1:null,f2:null,damage:null,fraction:null,capacity,reason:d>=capacity?'capacity':'range'};
      if (d===0) return {equilibrium:true,c:0,f1:0,f2:0,damage:0,fraction:null,capacity};
      let lo=0,hi=CMAX;
      for(let i=0;i<80;i++) {
        const mid=(lo+hi)/2, f=fluxes(mid,p);
        if(f.f1+f.f2<d) lo=mid; else hi=mid;
      }
      const c=(lo+hi)/2, {f1,f2}=fluxes(c,p);
      return {equilibrium:true,c,f1,f2,damage:Math.max(0,f2-p.rgsh),fraction:f2/d,capacity};
    }
    function threshold(p) {
      if(p.rgsh>=p.vmax2) return Infinity;
      const c=p.km2*p.rgsh/(p.vmax2-p.rgsh);
      return fluxes(c,p).f1+p.rgsh;
    }
    return {DEFAULTS,CMAX,fluxes,solve,threshold};
  })();

  const $=id=>root.querySelector('#ps-'+id), NS='http://www.w3.org/2000/svg';
  const nf=new Intl.NumberFormat('en-US',{minimumFractionDigits:2,maximumFractionDigits:2});
  const fmt=(n,d=2)=>d===2?nf.format(n):n.toLocaleString('en-US',{minimumFractionDigits:d,maximumFractionDigits:d});
  const reduced=window.matchMedia('(prefers-reduced-motion: reduce)');
  const state={dose:1,p:{...Modello.DEFAULTS},motion:!reduced.matches};
  const charts=[];
  let targetVisual={c:0,f1:0,f2:0,damage:0,gsh:0}, visual={...targetVisual},frame=0,lastTime=0,statusTimer=0,comparisonFirst=true;
  function svg(tag,attrs={},parent) { const el=document.createElementNS(NS,tag); Object.entries(attrs).forEach(([k,v])=>el.setAttribute(k,v)); if(parent)parent.append(el); return el; }
  function text(parent,x,y,copy,attrs={}) {const el=svg('text',{x,y,...attrs},parent);el.textContent=copy;return el;}
  const X=42,Y=13,W=458,H=112,MAXDOSE=10;
  function makeChart(id,kind) {
    const chartRoot=$(id);const defs=svg('defs',{},chartRoot), pattern=svg('pattern',{id:'ps-'+id+'-hatch',width:7,height:7,patternUnits:'userSpaceOnUse'},defs);
    svg('path',{d:'M-1 1L1 -1M0 7L7 0M6 8L8 6',stroke:'#43516A','stroke-width':.6,opacity:.65},pattern);
    const clip=svg('clipPath',{id:'ps-'+id+'-clip'},defs);svg('rect',{x:X-1,y:Y-3,width:W+2,height:H+6},clip);
    const grid=svg('g',{},chartRoot),zone=svg('rect',{y:Y,height:H,fill:'url(#ps-'+id+'-hatch)'},chartRoot);
    const zoneLabel=text(chartRoot,410,38,'BEYOND CAPACITY',{'text-anchor':'middle',style:'font-size:9px;fill:#91A0B5'});
    const zoneSub=text(chartRoot,410,52,'saturation',{'text-anchor':'middle',style:'font-size:9px;fill:#788BA4'});
    const curves=svg('g',{'clip-path':'url(#ps-'+id+'-clip)'},chartRoot);
    const area=svg('path',{fill:'#FF4059',opacity:.09},curves);
    const path1=svg('path',{fill:'none',stroke:kind==='damage'?'#FF4059':kind==='fraction'?'#FF6B5C':'#3DD6C4','stroke-width':2.5,'stroke-linejoin':'round'},curves);
    const path2=svg('path',{fill:'none',stroke:'#FF6B5C','stroke-width':2.5,'stroke-linejoin':'round'},curves);
    const thresholdLine=svg('line',{y1:Y,y2:Y+H,stroke:'#F2C14E','stroke-width':1,'stroke-dasharray':'3 4',opacity:.8},chartRoot);
    const marker=svg('line',{y1:Y,y2:Y+H,stroke:'#E4EAF2','stroke-width':1,opacity:.7},chartRoot);
    const point1=svg('circle',{r:3.5,fill:kind==='damage'?'#FF4059':kind==='fraction'?'#FF6B5C':'#3DD6C4',stroke:'#17202E','stroke-width':1.5},chartRoot);
    const point2=svg('circle',{r:3.5,fill:'#FF6B5C',stroke:'#17202E','stroke-width':1.5},chartRoot);
    const zero=svg('circle',{cx:X,r:3,fill:'#17202E',stroke:'#FF6B5C','stroke-width':1.5},chartRoot);
    const chart={root:chartRoot,kind,grid,zone,zoneLabel,zoneSub,area,path1,path2,thresholdLine,marker,point1,point2,zero,maxY:4};charts.push(chart);return chart;
  }
  makeChart('flow-chart','flow');makeChart('fraction-chart','fraction');makeChart('damage-chart','damage');
  function redrawCurves() {
    const p=state.p,cap=p.vmax1+p.vmax2,t=Modello.threshold(p);
    const samples=[];
    for(let i=0;i<=450;i++) {const d=cap*i/451;samples.push({d,...Modello.solve(d,p)});}
    samples.push({d:cap-1e-4,...Modello.solve(cap-1e-4,p)});
    for(const ch of charts) {
      ch.maxY=ch.kind==='fraction'?1:4;ch.grid.replaceChildren();
      const y=v=>Y+H-H*v/ch.maxY;
      for(let i=0;i<=4;i++) {const value=ch.maxY*i/4;svg('line',{x1:X,x2:X+W,y1:y(value),y2:y(value),stroke:'#26344A','stroke-width':1},ch.grid);text(ch.grid,X-9,y(value)+3,ch.kind==='fraction'?Math.round(value*100)+'%':fmt(value,0),{'text-anchor':'end'});}
      for(let i=0;i<=10;i+=2) {const x=X+W*i/MAXDOSE;svg('line',{x1:x,x2:x,y1:Y,y2:Y+H,stroke:'#26344A','stroke-width':.5,opacity:.7},ch.grid);text(ch.grid,x,Y+H+19,String(i),{'text-anchor':'middle'});}
      const zoneX=X+cap/MAXDOSE*W;ch.zone.setAttribute('x',zoneX);ch.zone.setAttribute('width',X+W-zoneX);
      ch.zoneLabel.setAttribute('x',(zoneX+X+W)/2);ch.zoneSub.setAttribute('x',(zoneX+X+W)/2);
      const path=key=>samples.filter(s=>s.equilibrium&&s[key]!==null).map((s,i)=>(i?'L':'M')+(X+s.d/MAXDOSE*W).toFixed(2)+' '+y(s[key]).toFixed(2)).join(' ');
      const key=ch.kind==='flow'?'f1':ch.kind==='fraction'?'fraction':'damage';
      ch.path1.setAttribute('d',path(key));ch.path2.setAttribute('d',ch.kind==='flow'?path('f2'):'');
      ch.area.setAttribute('d',ch.kind==='damage'?path('damage')+' L'+(X+(cap-1e-4)/MAXDOSE*W)+' '+y(0)+' L'+X+' '+y(0)+' Z':'');
      ch.thresholdLine.setAttribute('x1',X+t/MAXDOSE*W);ch.thresholdLine.setAttribute('x2',X+t/MAXDOSE*W);ch.thresholdLine.setAttribute('visibility',Number.isFinite(t)?'visible':'hidden');
      const lowFraction=(p.vmax2/p.km2)/(p.vmax1/p.km1+p.vmax2/p.km2);
      ch.zero.setAttribute('cy',y(lowFraction));ch.zero.setAttribute('visibility',ch.kind==='fraction'?'visible':'hidden');
    }
    $('dose').style.setProperty('--threshold-position',Math.min(100,t/MAXDOSE*100)+'%');
    $('dose').style.setProperty('--capacity-position',cap/MAXDOSE*100+'%');
    $('threshold').textContent=Number.isFinite(t)?fmt(t)+'×':'none';
    $('vmax1-value').textContent=fmt(p.vmax1);$('rgsh-value').textContent=fmt(p.rgsh);
    $('safe-param').textContent='Km 0.30 / Vmax '+fmt(p.vmax1);
    $('gsh-capacity').textContent='Rnet = '+fmt(p.rgsh);
    $('gsh-readout-capacity').textContent='of Rnet = '+fmt(p.rgsh);
    const diameter=14*Math.sqrt(p.vmax1);
    $('pipe1-border').setAttribute('stroke-width',diameter+6);$('pipe1').setAttribute('stroke-width',diameter);$('pipe1-mouth').setAttribute('ry',diameter/2);$('pipe1-mouth').setAttribute('rx',diameter/3.5);
    comparisonFirst=true;updateComparison();
  }
  function updateComparison() {
    const t=Modello.threshold(state.p),d1=Math.max(.1,Math.round(t*1.1*100)/100),d2=Math.round(d1*200)/100,a=Modello.solve(d1,state.p),b=Modello.solve(d2,state.p);
    state.comparison=[d1,d2];
    $('comparison-dose-a').textContent=fmt(d1)+'×';$('comparison-dose-b').textContent=fmt(d2)+'×';
    if(!b.equilibrium) $('comparison-copy').textContent='With this buffer, doubling the starting dose exceeds the total capacity of the model.';
    else {
      const ratio=b.damage/a.damage;
      $('comparison-copy').replaceChildren(document.createTextNode('Disconnection: '+fmt(a.damage,3)+' → '+fmt(b.damage,3)+'. '));
      const strong=document.createElement('strong');strong.textContent='Dose ×2, excess ×'+fmt(ratio,1)+'.';$('comparison-copy').append(strong);
    }
    $('compare-dose').textContent=comparisonFirst?'Show first dose':'Now double it';
  }
  function paintDiagram(v) {
    const level=325-48*Math.min(5.5,Math.max(0,v.c));
    $('water').setAttribute('y',level);$('water').setAttribute('height',325-level);$('water-line').setAttribute('d','M180 '+level+'H408');
    $('inlet').setAttribute('d','M294 20V'+Math.max(61,level));$('inlet').setAttribute('stroke-width',state.dose>0?Math.sqrt(state.dose)*3:0);
    $('flow1').setAttribute('stroke-width',v.f1>0?12*Math.sqrt(v.f1):0);$('flow2').setAttribute('stroke-width',v.f2>0?13*Math.sqrt(v.f2):0);
    const gshLevel=385-72*v.gsh;$('gsh-water').setAttribute('y',gshLevel);$('gsh-water').setAttribute('height',385-gshLevel);
    $('spill').setAttribute('stroke-width',v.damage>0?8*Math.sqrt(v.damage):0);$('spill').setAttribute('opacity',v.damage>1e-8?1:0);
    $('liver').setAttribute('fill',v.damage>1e-8?'#6D293A':'#362431');$('liver').setAttribute('stroke',v.damage>1e-8?'#FF4059':'#5D3442');
  }
  function animate(now) {
    const factor=1-Math.exp(-Math.min(64,now-lastTime)/160);lastTime=now;let distance=0;
    for(const k in visual){visual[k]+=(targetVisual[k]-visual[k])*factor;distance+=Math.abs(targetVisual[k]-visual[k]);}
    paintDiagram(visual);
    if(distance>.0001)frame=requestAnimationFrame(animate);else {visual={...targetVisual};paintDiagram(visual);frame=0;}
  }
  function transitionVisual(next) {
    targetVisual=next;
    if(!state.motion||reduced.matches){cancelAnimationFrame(frame);frame=0;visual={...next};paintDiagram(visual);}
    else if(!frame){lastTime=performance.now();frame=requestAnimationFrame(animate);}
  }
  function render() {
    const {dose:d,p}=state,s=Modello.solve(d,p),damage=s.equilibrium&&s.damage>1e-9;
    $('dose-value').textContent=fmt(d);$('dose').setAttribute('aria-valuetext',fmt(d)+' times the educational reference');
    $('inlet-label').textContent='D = '+fmt(d);$('flow-chart-value').textContent='D = '+fmt(d)+'×';
    $('f1-value').textContent=s.equilibrium?fmt(s.f1,3):'—';$('f2-value').textContent=s.equilibrium?fmt(s.f2,3):'—';$('damage-value').textContent=s.equilibrium?fmt(s.damage,3):'—';
    $('fraction-value').textContent=s.fraction===null?'undefined':fmt(s.fraction*100,1)+'%';$('damage-chart-value').textContent=s.equilibrium?fmt(s.damage,3):'undefined';
    $('concentration').textContent=s.equilibrium?'C = '+fmt(s.c):'C undefined';
    $('napqi-flow').textContent=s.equilibrium?fmt(s.f2,3):'→ '+fmt(p.vmax2);
    $('above-scale').setAttribute('opacity',!s.equilibrium||s.c>5.5?1:0);
    $('level-note').textContent=!s.equilibrium?'Model at capacity limit, not in equilibrium':s.c>5.5?'Off scale: exact C value still shown':'Level proportional to C';
    $('mass-balance').textContent=s.equilibrium?'inflow '+fmt(d)+' = outflow '+fmt(s.f1+s.f2):'inflow ≥ capacity '+fmt(s.capacity);
    const usage=s.equilibrium?(p.rgsh===0?(s.f2>0?1:0):Math.min(1,s.f2/p.rgsh)):1;
    $('gsh-usage').textContent=p.rgsh===0?'0 buffer':fmt(usage*100,0)+'%';
    $('gsh-value').textContent=!s.equilibrium?'—':p.rgsh===0?'none':fmt(usage*100,0)+'%';
    const badge=$('state-badge');badge.dataset.state=!s.equilibrium?'no-equilibrium':damage?'damage':'protected';
    badge.textContent=!s.equilibrium?'Beyond capacity':damage?'Disconnection prevails':d===0?'No drug':'Subanesthetic window';
    const explanation=!s.equilibrium
      ?'D has reached or exceeded Vmax₁ + Vmax₂ = '+fmt(s.capacity)+'. The diagram shows the limit of full saturation.'
      :d===0?'Without ketamine, C and both flows are zero. The network is at baseline.'
      :damage?'Direct blockade on pyramidal neurons ('+fmt(s.f2,3)+') exceeds the compensation buffer ('+fmt(p.rgsh,3)+'). The excess '+fmt(s.damage,3)+' pushes the network toward disconnection and dissociative anesthesia.'
      :'At this exposure, releasing the GABAergic brakes ('+fmt(s.f1,3)+') prevails, while direct blockade on pyramidal neurons ('+fmt(s.f2,3)+') stays within the network buffer.';
    $('live-explanation').textContent=explanation;
    const v1=s.equilibrium?s.f1:p.vmax1,v2=s.equilibrium?s.f2:p.vmax2;
    transitionVisual({c:s.equilibrium?Math.min(s.c,5.6):5.6,f1:v1,f2:v2,damage:s.equilibrium?s.damage:Math.max(0,p.vmax2-p.rgsh),gsh:usage});
    for(const ch of charts) {
      const x=X+d/MAXDOSE*W,y=v=>Y+H-H*v/ch.maxY;
      ch.marker.setAttribute('x1',x);ch.marker.setAttribute('x2',x);
      const value=ch.kind==='flow'?s.f1:ch.kind==='fraction'?s.fraction:s.damage;
      ch.point1.setAttribute('cx',x);ch.point1.setAttribute('cy',value===null?Y+H:y(value));ch.point1.setAttribute('visibility',s.equilibrium&&value!==null?'visible':'hidden');
      ch.point2.setAttribute('cx',x);ch.point2.setAttribute('cy',s.f2===null?Y+H:y(s.f2));ch.point2.setAttribute('visibility',ch.kind==='flow'&&s.equilibrium?'visible':'hidden');
    }
    clearTimeout(statusTimer);statusTimer=setTimeout(()=>{$('accessible-status').textContent='Dose '+fmt(d)+'. '+explanation;},180);
  }
  function setDose(value) {state.dose=Math.min(10,Math.max(0,Math.round(value*100)/100));$('dose').value=state.dose;render();}
  $('dose').addEventListener('input',e=>{state.dose=Number(e.target.value);render();});
  root.querySelectorAll('[data-dose]').forEach(button=>button.addEventListener('click',()=>setDose(Number(button.dataset.dose))));
  $('near-threshold').addEventListener('click',()=>setDose(Modello.threshold(state.p)+.05));
  $('vmax1').addEventListener('input',e=>{state.p.vmax1=Number(e.target.value);redrawCurves();render();});
  $('rgsh').addEventListener('input',e=>{state.p.rgsh=Number(e.target.value);redrawCurves();render();});
  $('reset').addEventListener('click',()=>{state.p={...Modello.DEFAULTS};$('vmax1').value=state.p.vmax1;$('rgsh').value=state.p.rgsh;redrawCurves();setDose(1);});
  $('compare-dose').addEventListener('click',()=>{setDose(state.comparison[comparisonFirst?0:1]);comparisonFirst=!comparisonFirst;updateComparison();});
  function updateMotion() {const enabled=state.motion&&!reduced.matches;root.classList.toggle('motion-off',!enabled);$('motion').setAttribute('aria-pressed',String(enabled));$('motion').textContent=enabled?'Animations: on':'Animations: off';if(!enabled)transitionVisual(targetVisual);}
  $('motion').addEventListener('click',()=>{state.motion=!state.motion;updateMotion();});
  reduced.addEventListener('change',()=>{if(reduced.matches)state.motion=false;updateMotion();});
  updateMotion();redrawCurves();render();
})();
</script>
{% endraw %}

### A window, not a switch

Even on the link between "new synapses" and mood, there is a crucial experimental detail. In a study in mice, behavioral improvement after ketamine appeared *before* new dendritic spines grew: new synapses were not needed to initiate the rapid effect, but they were required to **sustain it over time**.[^spines]

So there is no magic along the lines of "new synapses sprout right away and depression vanishes." The more compelling idea is that ketamine opens a temporary window in which circuits are less rigid. That is why researchers are testing whether pairing psychotherapy shortly after dosing can help consolidate the benefit: early results are encouraging, though still preliminary.[^cbt]

And one thing needs to be stated clearly: **if a relapse occurs after treatment, it does not mean the person "wasted" the window.** Depression is not an exam you pass by making good use of your allotted time.

## Then why not take ketamine on your own?

I know how tempting it is to self-medicate, to look for a simple fix to a complex problem. Now, I have nothing against simple fixes—it's just that, at least in this case, they don't work.

It is very easy to fall into a logical short-circuit here:

`ketamine → plasticity → antidepressant`

and therefore:

`more ketamine → more plasticity → less depression`.

No.

That is the exact kind of linear reasoning pharmacology keeps punishing.

Recreational (or DIY) exposure and clinical treatment of depression are two completely different systems. In clinical treatment we have:

`selected patient → scheduled treatment → controlled exposure → monitoring → response assessment → possible maintenance`.[^ema]

In unsupervised use, by contrast, we can easily end up with:

`pleasant or dissociative effect → redosing → tolerance → escalating exposure → use as an emotional regulator → craving`

(on top of acute cardiovascular and respiratory risks and, with repeated use, severe urinary and hepatobiliary complications).[^safety]

The very same dissociative effect that in the clinic is a monitored side effect can become, in someone who is suffering, a powerful reinforcement loop:

> I feel awful  
> ↓  
> I take ketamine  
> ↓  
> for a while I don't feel myself anymore  
> ↓  
> relief  
> ↓  
> the brain learns.

That is plasticity too.

Just not the kind we were looking for.


<style>
  .ket-sources .footnotes { margin-top: 0; }
  .ket-sources .footnotes ol { margin-bottom: 0; padding-left: 1.35em; }
  .ket-sources .footnotes li { margin-bottom: 0.65em; font-size: 0.92rem; }
  .ket-sources .footnotes li:last-child,
  .ket-sources .footnotes li p { margin-bottom: 0; }
</style>
<details class="ket-sources" id="ket-sources">
  <summary>Sources and notes (18)</summary>
</details>
<script>
(() => {
  const details = document.getElementById('ket-sources');
  if (!details) return;
  function attachFootnotes() {
    const scope = details.closest('.post-content') || document;
    const footnotes = scope.querySelector('.footnotes');
    if (footnotes && footnotes.parentElement !== details) {
      details.appendChild(footnotes);
    }
    if (window.location.hash && window.location.hash.startsWith('#fn:')) {
      details.open = true;
    }
  }
  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', attachFootnotes, { once: true });
  } else {
    attachFootnotes();
  }
  window.addEventListener('hashchange', () => {
    if (window.location.hash && window.location.hash.startsWith('#fn:')) {
      details.open = true;
    }
  });
  document.addEventListener('click', event => {
    const link = event.target.closest && event.target.closest('a.footnote');
    if (link) details.open = true;
  });
})();
</script>

[^depression]: National Institute of Mental Health, [Depression](https://www.nimh.nih.gov/health/publications/depression). Symptoms, diagnosis, and treatments; clinical evaluation also serves to rule out conditions with similar symptoms.
[^fmri]: Zhang et al. (2025), [Resting-state network alterations in depression: a comprehensive meta-analysis of functional connectivity](https://pubmed.ncbi.nlm.nih.gov/40008424/). Meta-analysis of 58 studies; group-level findings.
[^ssri]: Taylor et al. (2006), [Early onset of selective serotonin reuptake inhibitor antidepressant action](https://pubmed.ncbi.nlm.nih.gov/17088502/). Synthesis of randomized trials detecting improvements over placebo within the first week.
[^clinical]: Murrough et al. (2013), [Antidepressant efficacy of ketamine in treatment-resistant major depression: a two-site randomized controlled trial](https://pubmed.ncbi.nlm.nih.gov/23982301/). Trial in 73 patients, comparison with midazolam, and primary assessment at 24 hours.
[^si]: Wilkinson et al. (2018), [The Effect of a Single Dose of Intravenous Ketamine on Suicidal Ideation: A Systematic Review and Individual Participant Data Meta-Analysis](https://pubmed.ncbi.nlm.nih.gov/28969441/). Individual-participant data from 10 trials controlled with saline or midazolam; analysis of the 167 participants with baseline suicidal ideation. Outcomes derive mainly from single items of depression scales rather than dedicated instruments.
[^abbar]: Abbar et al. (2022), [Ketamine for the acute treatment of severe suicidal ideation: double blind, randomised placebo controlled trial](https://www.bmj.com/content/376/bmj-2021-067194). 156 voluntarily hospitalized patients with bipolar disorder, depressive disorders, or other diagnoses; two infusions 24 hours apart. Day-3 remission of ideation, ketamine vs. placebo: 63.0% vs. 31.6% in the full sample; 84.6% vs. 28.0% in the bipolar subgroup; 42.3% vs. 35.7% in the depressive disorders subgroup (p = 0.6). At week 6 in the full sample: 69.5% vs. 56.3%, difference not statistically significant. Patients who attempted suicide over the six weeks: 6 in the ketamine group and 8 in the placebo group; the trial was not powered to evaluate this outcome.
[^aspire]: Fu et al. (2020), [Esketamine Nasal Spray for Rapid Reduction of Major Depressive Disorder Symptoms in Patients Who Have Active Suicidal Ideation With Intent (ASPIRE I)](https://pubmed.ncbi.nlm.nih.gov/32412700/), and Ionescu et al. (2021), [ASPIRE II](https://pubmed.ncbi.nlm.nih.gov/32861217/). Esketamine or placebo added to inpatient standard of care and oral antidepressant therapy; primary endpoint on depressive symptoms (MADRS) at 24 hours, key secondary measure on suicidality severity (CGI-SS-r).
[^ema]: European Medicines Agency, [Spravato: summary of product characteristics](https://www.ema.europa.eu/en/documents/product-information/spravato-epar-product-information_en.pdf). European indications, monitoring, maintenance, and adverse effects.
[^stereo]: Benthuysen et al. (1989), [Comparison of isomers of ketamine on catalepsy in the rat and electrical activity of the brain and behavior in the cat](https://www.sciencedirect.com/science/article/pii/002839088990110X). Identification of the S(+) form and pharmacological comparison between enantiomers in animal models.
[^structure]: Zhang et al. (2021), [Structural basis of ketamine action on human NMDA receptors](https://www.nature.com/articles/s41586-021-03769-9). Structure of the channel binding site and higher NMDA affinity of the S form.
[^euda]: European Union Drugs Agency, [Frequently asked questions: therapeutic use of psychedelic substances](https://www.euda.europa.eu/publications/frequently-asked-questions-faq/faq-therapeutic-use-psychedelic-substances_en). Distinguishes authorized esketamine from off-label clinical use of ketamine in European settings.
[^gaba]: Gerhard et al. (2020), [GABA interneurons are the cellular trigger for ketamine's rapid antidepressant actions](https://pubmed.ncbi.nlm.nih.gov/31743111/), and Ali et al. (2020), [Ketamine disinhibits dendrites and enhances calcium signals in prefrontal dendritic spines](https://www.nature.com/articles/s41467-019-13809-8). Preclinical experiments supporting the disinhibition model.
[^nmda]: [Pharmacology of NMDA Receptors](https://www.ncbi.nlm.nih.gov/books/NBK5282/), in *Biology of the NMDA Receptor*. Channel activation, modulation, and block.
[^mtor]: Abdallah et al. (2020), [Modulation of the antidepressant effects of ketamine by the mTORC1 inhibitor rapamycin](https://pubmed.ncbi.nlm.nih.gov/32092760/). In this small human study, rapamycin pretreatment did not block the antidepressant effect at 24 hours—an example of the difficulty of translating a preclinical cascade into a complete clinical explanation.
[^spines]: Moda-Sava et al. (2019), [Sustained rescue of prefrontal circuit dysfunction by antidepressant-induced spine formation](https://pubmed.ncbi.nlm.nih.gov/30975859/). In mice, newly formed prefrontal spines were required to sustain certain behavioral effects, not to initiate them.
[^cbt]: Wilkinson et al. (2021), [Cognitive Behavioral Therapy to Sustain the Antidepressant Effects of Ketamine in Treatment-Resistant Depression: A Randomized Clinical Trial](https://pubmed.ncbi.nlm.nih.gov/34186531/). Twenty-eight responders randomized; preliminary results without a significant group-by-time interaction on the primary MADRS outcome.
[^network]: Cichon et al. (2023), [Ketamine triggers a switch in excitatory neuronal activity across neocortex](https://www.nature.com/articles/s41593-022-01203-5). Neuronal activity imaging in mice showing suppression of active populations and activation of previously silent ones.
[^safety]: US Food and Drug Administration, [Ketalar: prescribing information (2026)](https://www.accessdata.fda.gov/drugsatfda_docs/label/2026/016812s057lbl.pdf). Risks, interactions, urinary and hepatobiliary complications, and abuse and dependence potential of ketamine. US regulatory indications should not be confused with European ones.
