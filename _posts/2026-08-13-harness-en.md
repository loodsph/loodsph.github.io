---
layout: post
title: "Melodic techno in Logic Pro: sound design, mixing, and mastering"
display_title: "Harness"
seo_title: "Melodic techno in Logic Pro: sound design, mixing, and mastering"
date: 2026-08-13
categories: [musica, produzione]
tags: [music-production, melodic-techno, sound-design, logic-pro, mixing, mastering]
description: "How I produced Harness in Logic Pro: oscillators, sub and mid bass, sidechain, arrangement, mixing, and mastering a melodic techno track."
lang: en
ref: harness
pixel_icon: "harness.png"
smooth_image: true
image:
  path: /assets/images/harness-social.png
  width: 1200
  height: 630
  alt: "Luminous waveforms cross a dark soundscape in the cover image for Harness"
---

One of my (many) weak spots when it comes to music is **producing a specific sound**. Playing something I hear in my head is a problem I know how to deal with, more or less; building *that* bass, *that* synth, or *that* atmosphere from a waveform is another story. So I decided to put together a techno track.

The direction is **melodic techno**: I want a recognizable melody, but neither the harmony nor the melody needs to be particularly complex. A large part of the game should be in the **sound and how it evolves over time**. The goal, then, is to build a track as much as possible from scratch, trying not to rely on ready-made presets. I’ll use **Logic Pro**; I come from GarageBand, so at least the interface is not completely alien to me.

There is something else I’m interested in. This will probably take long enough for me to pass through several different moods, and I want to see whether — and how much — they end up influencing my musical choices, especially whether I can notice it while it is happening. Nor will I pretend that, however rough it turns out, this track is not in some way **an expression of me**.

I have no intention of taking someone else’s work, remixing it, and then saying I’m going to “play.” It is perfectly legitimate, mind you, nothing wrong with it. It simply **isn’t my thing**: if I’m going to do this, I at least want to try to understand what I’m doing.

You have to start somewhere, so I choose **F minor**. A minor key feels fairly natural for what I have in mind. The overall structure is already more or less clear as well: a few minutes, two drops — the second one deeper — a fairly prominent melody, and very simple harmony.

I don’t want to turn this post into “then at bar 17 I added a hi-hat,” though. I’ll keep mainly the things that struck me as interesting or less than obvious along the way. I can work out that removing the kick in the breakdown makes sense without getting my ears dirty; what I care about is understanding **why certain things work** and, perhaps, ending up with a slightly better idea of what I’m looking for when I open a synth and find fifty knobs in front of me.

[Listen to Harness on SoundCloud](https://soundcloud.com/ludovico-comegna-3641395/harness)<br>
[Listen to Harness on YouTube](https://www.youtube.com/watch?v=J1XlvVr2OA8)

---

# Drums

After experimenting with MIDI for a while, I find the **Step Sequencer** much more convenient than the Piano Roll for programming a classic **four-on-the-floor kick**. The initial idea is a fairly long intro: start without the kick, gradually add elements, introduce a few variations, open things up once, and then reach the main section.

I create two different drum patterns. I like both of them, so I elegantly postpone the problem to my future self. The more urgent problem is another one: **it sounds like shit**.

After quite a few attempts I land on the classic **Roland 808**: raw, simple, with a deep kick and plenty of low end. At first I keep the whole drum kit together; small spoiler from the future: this will be a terrible idea. Later I will end up splitting it into at least **Drum, Kick, Impact Kick, and Filtered Drum**. Separating the kick from everything else will prove particularly useful not only for the mix, but for the sidechain as well.

---

# Bass: one thing is not enough

Almost immediately I decide to split the bass into two elements: **Sub bass** and **Mid bass**. They are not supposed to do the same job: the sub should provide **weight**, while the mid bass should provide **character**. This distinction, which starts out almost as an aesthetic choice, will become one of the most important things I learn while making the track.

## Sub bass

I open **Retro Synth** and decide to build the sound from scratch. I am faced with a fairly indecent number of parameters, so before randomly touching everything I at least try to understand the foundations.

### Oscillators

An oscillator generates the starting signal. In their ideal forms, different waves have different harmonic content: a sine wave contains only the fundamental, while triangle, square, and especially saw waves introduce progressively more harmonics.

Brutally translated: **fewer harmonics = a purer sound; more harmonics = a richer, rougher, more aggressive sound**.

The interesting thing is that a synthesizer does not necessarily force me to choose a single waveform. I can have several oscillators at once and add their signals together. The result is not a “third oscillator”: it is the moment-by-moment sum of the two signals’ amplitudes, which can produce a resulting waveform different from either one.

This is definitely easier to see than to explain.

<div id="ts-wave-mixer" class="tsw-widget">
<style>
#ts-wave-mixer{
  --bg:#111318;
  --panel:#181b21;
  --line:#2b3039;
  --text:#f3f4f6;
  --muted:#9ca3af;
  --accent:#ff6b3d;
  --accent2:#59c3ff;
  font-family:Inter,system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
  background:var(--bg);
  color:var(--text);
  border:1px solid var(--line);
  border-radius:16px;
  padding:18px;
  margin:28px 0;
  box-sizing:border-box;
}
#ts-wave-mixer *{box-sizing:border-box}
#ts-wave-mixer h4{margin:0 0 4px;font-size:18px}
#ts-wave-mixer p{margin:0;color:var(--muted);font-size:14px;line-height:1.45}
#ts-wave-mixer .tsw-controls{
  display:grid;
  grid-template-columns:repeat(2,minmax(0,1fr));
  gap:12px;
  margin:14px 0;
}
#ts-wave-mixer .tsw-osc{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:12px;
  padding:12px;
}
#ts-wave-mixer .tsw-osc strong{display:block;margin-bottom:10px}
#ts-wave-mixer label{
  display:grid;
  grid-template-columns:88px 1fr 58px;
  gap:8px;
  align-items:center;
  font-size:13px;
  margin:8px 0;
  color:var(--muted);
}
#ts-wave-mixer select,
#ts-wave-mixer input[type=range]{width:100%}
#ts-wave-mixer select{
  background:#0f1115;
  color:var(--text);
  border:1px solid var(--line);
  border-radius:8px;
  padding:6px;
}
#ts-wave-mixer output{
  color:var(--text);
  text-align:right;
  font-variant-numeric:tabular-nums;
}
#ts-wave-mixer canvas{
  display:block;
  width:100%;
  height:300px;
  background:#0b0d11;
  border:1px solid var(--line);
  border-radius:12px;
}
#ts-wave-mixer .tsw-bottom{
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:12px;
  margin-top:12px;
}
#ts-wave-mixer .tsw-actions{display:flex;gap:8px;flex-wrap:wrap}
#ts-wave-mixer button{
  border:0;
  border-radius:10px;
  padding:9px 14px;
  background:var(--accent);
  color:white;
  font-weight:700;
  cursor:pointer;
}
#ts-wave-mixer button[data-role=preset]{background:#262b34;color:var(--text);border:1px solid var(--line)}
#ts-wave-mixer button:disabled{cursor:wait;opacity:.65}
#ts-wave-mixer button:focus-visible,
#ts-wave-mixer select:focus-visible,
#ts-wave-mixer input:focus-visible{outline:3px solid var(--accent2);outline-offset:3px}
#ts-wave-mixer .tsw-note{font-size:12px;color:var(--muted)}
#ts-wave-mixer .tsw-status{min-height:1.4em;margin-top:8px;font-size:12px;color:var(--muted)}
@media(max-width:700px){
  #ts-wave-mixer .tsw-controls{grid-template-columns:1fr}
  #ts-wave-mixer label{grid-template-columns:78px 1fr 52px}
  #ts-wave-mixer .tsw-bottom{align-items:flex-start;flex-direction:column}
}
</style>

<div>
  <h4>Adding oscillators</h4>
  <p>Change waveform, frequency, and level. The third graph shows the resulting signal A + B.</p>
</div>

<div class="tsw-controls">

  <div class="tsw-osc">
    <strong>OSC A</strong>

<label>
  Wave
  <select data-role="waveA">
    <option value="sine">Sine</option>
    <option value="triangle" selected>Triangle</option>
    <option value="sawtooth">Saw</option>
    <option value="square">Square</option>
  </select>
  <span></span>
</label>

<label>
  Frequency
  <input data-role="freqA" type="range" min="55" max="440" value="110" step="1">
  <output data-role="freqAOut">110 Hz</output>
</label>

<label>
  Level
  <input data-role="gainA" type="range" min="0" max="1" value="0.70" step="0.01">
  <output data-role="gainAOut">70%</output>
</label>

  </div>

  <div class="tsw-osc">
    <strong>OSC B</strong>

<label>
  Wave
  <select data-role="waveB">
    <option value="sine">Sine</option>
    <option value="triangle">Triangle</option>
    <option value="sawtooth" selected>Saw</option>
    <option value="square">Square</option>
  </select>
  <span></span>
</label>

<label>
  Frequency
  <input data-role="freqB" type="range" min="55" max="440" value="110" step="1">
  <output data-role="freqBOut">110 Hz</output>
</label>

<label>
  Level
  <input data-role="gainB" type="range" min="0" max="1" value="0.45" step="0.01">
  <output data-role="gainBOut">45%</output>
</label>

  </div>

</div>

<canvas data-role="scope" role="img" aria-label="Oscilloscope showing oscillators A, B, and their sum">
  Three graphs show oscillator A, oscillator B, and their moment-by-moment sum.
</canvas>

<div class="tsw-bottom">
  <div class="tsw-actions">
    <button type="button" data-role="play">▶ Listen</button>
    <button type="button" data-role="preset">110/112 Hz beating</button>
  </div>
  <span class="tsw-note" data-role="windowNote">Displayed window: 40 ms.</span>
</div>
<div class="tsw-status" data-role="status" aria-live="polite"></div>

<script>
(() => {
  const root = document.currentScript?.closest('.tsw-widget') || document.getElementById('ts-wave-mixer');
  if (!root || root.dataset.ready) return;
  root.dataset.ready = '1';

  const q = role => root.querySelector(`[data-role="${role}"]`);
  const waveA = q('waveA');
  const waveB = q('waveB');
  const freqA = q('freqA');
  const freqB = q('freqB');
  const gainA = q('gainA');
  const gainB = q('gainB');
  const freqAOut = q('freqAOut');
  const freqBOut = q('freqBOut');
  const gainAOut = q('gainAOut');
  const gainBOut = q('gainBOut');
  const canvas = q('scope');
  const play = q('play');
  const preset = q('preset');
  const status = q('status');
  const windowNote = q('windowNote');

  let audioCtx = null;
  let graph = null;
  let state = 'stopped';
  let canvasSize = {c:null,w:0,h:0,dpr:0};

  function sample(type, phase){
    const twoPi = Math.PI * 2;
    let cycle = (phase / twoPi) % 1;
    if (cycle < 0) cycle += 1;

    if (type === 'sine') return Math.sin(phase);
    if (type === 'square') return Math.sin(phase) >= 0 ? 1 : -1;
    if (type === 'sawtooth') return 2 * cycle - 1;
    if (type === 'triangle') return 1 - 4 * Math.abs(cycle - 0.5);

    return 0;
  }

  function fitCanvas(force=false){
    const dpr = Math.min(2,Math.max(1,window.devicePixelRatio || 1));
    const rect = canvas.getBoundingClientRect();
    const width = Math.max(1,Math.round(rect.width*dpr));
    const height = Math.max(1,Math.round(rect.height*dpr));

    if(force || width !== canvas.width || height !== canvas.height){
      canvas.width = width;
      canvas.height = height;
      canvasSize = {c:canvas.getContext('2d'),w:rect.width,h:rect.height,dpr};
      canvasSize.c.setTransform(dpr,0,0,dpr,0,0);
    }

    return canvasSize;
  }

  function visibleDuration(){
    const delta = Math.abs(+freqA.value-+freqB.value);
    const bothSine = waveA.value === 'sine' && waveB.value === 'sine';
    return bothSine && delta > 0 && delta <= 5 ? Math.min(2,2/delta) : 0.04;
  }

  function draw(){
    const {c,w,h} = fitCanvas();

    c.clearRect(0,0,w,h);
    c.fillStyle = '#0b0d11';
    c.fillRect(0,0,w,h);

    const rows = [h/6,h/2,5*h/6];

    c.strokeStyle = '#252a33';
    c.lineWidth = 1;

    rows.forEach(y => {
      c.beginPath();
      c.moveTo(0,y);
      c.lineTo(w,y);
      c.stroke();
    });

    c.fillStyle = '#9ca3af';
    c.font = '12px system-ui';
    c.fillText('OSC A',12,18);
    c.fillText('OSC B',12,h/3+18);
    c.fillText('A + B',12,2*h/3+18);

    const duration = visibleDuration();
    const fA = +freqA.value;
    const fB = +freqB.value;
    const aGain = +gainA.value;
    const bGain = +gainB.value;

    const colors = ['#59c3ff','#ff6b3d','#f3f4f6'];
    const amplitude = h/14;

    for(let row=0; row<3; row++){
      c.beginPath();
      c.strokeStyle = colors[row];
      c.lineWidth = 2;

      for(let x=0; x<=w; x++){
        const t = (x/w)*duration;

        const a =
          sample(waveA.value,Math.PI*2*fA*t)*aGain;

        const b =
          sample(waveB.value,Math.PI*2*fB*t)*bGain;

        const value =
          row === 0 ? a :
          row === 1 ? b :
          a+b;

        const y =
          rows[row] -
          value*amplitude;

        if(x === 0) c.moveTo(x,y);
        else c.lineTo(x,y);
      }

      c.stroke();
    }

    windowNote.textContent = duration >= 1
      ? `Displayed window: ${duration.toFixed(2)} s. The third graph makes the beating visible.`
      : 'Displayed window: 40 ms.';
  }

  function makeVoice(type,frequency,level,master,now){
    const osc = audioCtx.createOscillator();
    const gain = audioCtx.createGain();
    osc.type = type;
    osc.frequency.setValueAtTime(frequency,now);
    gain.gain.setValueAtTime(level,now);
    osc.connect(gain).connect(master);
    osc.start(now);
    return {osc,gain,type};
  }

  function replaceVoice(key,type,frequency,level){
    if(!graph || graph[key].type === type) return;
    const now = audioCtx.currentTime;
    const oldVoice = graph[key];
    const newVoice = makeVoice(type,frequency,0,graph.master,now);
    newVoice.gain.gain.linearRampToValueAtTime(level,now+0.02);
    oldVoice.gain.gain.cancelScheduledValues(now);
    oldVoice.gain.gain.setTargetAtTime(0,now,0.008);
    graph[key] = newVoice;

    setTimeout(() => {
      try{ oldVoice.osc.stop(); }catch(e){}
      try{ oldVoice.osc.disconnect(); oldVoice.gain.disconnect(); }catch(e){}
    },60);
  }

  function refresh(event){
    freqAOut.value = `${freqA.value} Hz`;
    freqBOut.value = `${freqB.value} Hz`;
    gainAOut.value = `${Math.round(gainA.value*100)}%`;
    gainBOut.value = `${Math.round(gainB.value*100)}%`;

    if(state === 'running' && graph){
      const now = audioCtx.currentTime;
      replaceVoice('a',waveA.value,+freqA.value,+gainA.value);
      replaceVoice('b',waveB.value,+freqB.value,+gainB.value);
      graph.a.osc.frequency.setTargetAtTime(+freqA.value,now,0.01);
      graph.b.osc.frequency.setTargetAtTime(+freqB.value,now,0.01);
      graph.a.gain.gain.setTargetAtTime(+gainA.value,now,0.01);
      graph.b.gain.gain.setTargetAtTime(+gainB.value,now,0.01);
    }

    draw();
  }

  async function start(){
    if(state !== 'stopped') return;
    const AudioContextClass = window.AudioContext || window.webkitAudioContext;
    if(!AudioContextClass){
      status.textContent = 'This browser does not support the Web Audio API.';
      return;
    }

    state = 'starting';
    play.disabled = true;
    status.textContent = 'Starting audio…';

    try{
      audioCtx = audioCtx || new AudioContextClass();
      await audioCtx.resume();
      if(state !== 'starting'){
        await audioCtx.suspend().catch(() => {});
        return;
      }

      const now = audioCtx.currentTime;
      const master = audioCtx.createGain();
      master.gain.setValueAtTime(0,now);
      master.gain.linearRampToValueAtTime(0.09,now+0.025);
      master.connect(audioCtx.destination);

      graph = {
        master,
        a:makeVoice(waveA.value,+freqA.value,+gainA.value,master,now),
        b:makeVoice(waveB.value,+freqB.value,+gainB.value,master,now)
      };

      state = 'running';
      play.textContent = '■ Stop';
      status.textContent = 'Audio playing.';
    }catch(error){
      state = 'stopped';
      status.textContent = 'The audio could not be started.';
    }finally{
      play.disabled = false;
    }
  }

  function stop({announce=true}={}){
    if(state === 'starting'){
      state = 'stopped';
      play.disabled = false;
      play.textContent = '▶ Listen';
      status.textContent = announce ? 'Audio stopped.' : '';
      return;
    }
    if(state !== 'running' || !graph) return;
    state = 'stopping';
    play.disabled = true;

    const stoppedGraph = graph;
    graph = null;
    const now = audioCtx.currentTime;
    stoppedGraph.master.gain.cancelScheduledValues(now);
    stoppedGraph.master.gain.setTargetAtTime(0,now,0.012);

    setTimeout(async () => {
      for(const voice of [stoppedGraph.a,stoppedGraph.b]){
        try{ voice.osc.stop(); }catch(e){}
        try{ voice.osc.disconnect(); voice.gain.disconnect(); }catch(e){}
      }
      try{ stoppedGraph.master.disconnect(); }catch(e){}
      if(audioCtx?.state === 'running') await audioCtx.suspend().catch(() => {});
      if(state === 'stopping') state = 'stopped';
      play.disabled = false;
      play.textContent = '▶ Listen';
      status.textContent = announce ? 'Audio stopped.' : '';
    },80);
  }

  [waveA,waveB,freqA,freqB,gainA,gainB].forEach(el => {
    el.addEventListener('input',refresh);
  });

  preset.addEventListener('click',() => {
    waveA.value = 'sine';
    waveB.value = 'sine';
    freqA.value = '110';
    freqB.value = '112';
    gainA.value = '0.65';
    gainB.value = '0.65';
    refresh();
    status.textContent = 'Beating preset selected: 110 Hz and 112 Hz.';
  });

  play.addEventListener('click',() => state === 'running' ? stop() : start());
  window.addEventListener('resize',() => { fitCanvas(true); draw(); },{passive:true});
  window.addEventListener('pagehide',() => stop({announce:false}),{once:true});

  fitCanvas(true);
  refresh();
})();
</script>

</div>

This also makes it clear why simply describing a wave as “softer” or “more angular” is not enough. I can start from two relatively simple signals and obtain something far more complex simply by changing their shape, level, or frequency.

A particularly interesting experiment is to set two sine waves to **110 Hz**, then move one of them to **112 Hz**. The frequencies are almost the same, but not identical, so they alternate between moments when they reinforce each other and moments when they partially cancel. The result is that periodic movement in volume perceived as **beating**.

For the sub, however, I do not need anything spectacular. What I mainly want is a stable fundamental, so I settle on a **triangle wave with a sine component**. This is one of the first times I realize that a sound does not necessarily have to be interesting when heard in isolation: it has to perform a function when everything else is playing.

### LFO

At first I understood very little here. **LFO means Low Frequency Oscillator**: an oscillator with a frequency low enough to be used mainly to modulate another parameter automatically. It can modulate pitch, volume, panning, filters, and many other things; in my case, the one I care about most is the **cutoff**.

The cutoff sets the point beyond which a filter begins to attenuate certain frequencies. It is not necessarily a hard wall: how quickly the filter attenuates them also depends on its slope, expressed in dB/oct. With the **low-pass** I am using, in much less elegant terms: **low cutoff = closed, dark sound; high cutoff = open, bright sound**.

I decide to do very little to the sub, anyway. I do not need to turn it into a spaceship: it stays mainly on the **F0** fundamental — in Logic’s default naming convention — and its job is to provide weight, not become a second melody.

### Sidechain

This, on the other hand, interests me a great deal. I place a compressor on the sub and tell it to react not to the bass itself, but to the **kick**. Every time the kick hits, the sub level is lowered for a brief moment.

The most immediate explanation would simply be “the kick arrives → the bass goes down,” but the interesting part is something else: I am not merely lowering the bass volume, I am creating **space in time** in the low frequencies. For a few milliseconds the kick can occupy that area without having to fight the sub, which returns immediately afterward.

Without sidechain I get a feeling of confinement, almost of being *overwhelmed*. When the sub pulls back for an instant, instead, there is a kind of relief: the acoustic equivalent of carving out a moment of silence amid the noise of life.

This is one of those things that becomes much more intuitive as soon as you can see and hear it.

<div id="ts-sidechain" class="tss-widget">
<style>
#ts-sidechain{
  --bg:#111318;
  --panel:#181b21;
  --line:#2b3039;
  --text:#f3f4f6;
  --muted:#9ca3af;
  --accent:#ff6b3d;
  --cyan:#59c3ff;
  font-family:Inter,system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
  background:var(--bg);
  color:var(--text);
  border:1px solid var(--line);
  border-radius:16px;
  padding:18px;
  margin:28px 0;
  box-sizing:border-box;
}
#ts-sidechain *{box-sizing:border-box}
#ts-sidechain h4{margin:0 0 4px;font-size:18px}
#ts-sidechain p{margin:0;color:var(--muted);font-size:14px;line-height:1.45}
#ts-sidechain .tss-grid{
  display:grid;
  grid-template-columns:260px 1fr;
  gap:14px;
  align-items:stretch;
}
#ts-sidechain .tss-controls{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:12px;
  padding:12px;
}
#ts-sidechain label{
  display:grid;
  grid-template-columns:72px 1fr 62px;
  gap:8px;
  align-items:center;
  font-size:13px;
  margin:10px 0;
  color:var(--muted);
}
#ts-sidechain output{
  color:var(--text);
  text-align:right;
  font-variant-numeric:tabular-nums;
}
#ts-sidechain input[type=range]{width:100%}
#ts-sidechain .tss-buttons{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-top:12px;
}
#ts-sidechain button{
  border:0;
  border-radius:10px;
  padding:9px 12px;
  font-weight:700;
  cursor:pointer;
}
#ts-sidechain button:disabled{cursor:wait;opacity:.65}
#ts-sidechain button:focus-visible,
#ts-sidechain input:focus-visible{outline:3px solid var(--cyan);outline-offset:3px}
#ts-sidechain [data-role=play]{
  background:var(--accent);
  color:#fff;
}
#ts-sidechain [data-role=toggle]{
  background:#262b34;
  color:var(--text);
  border:1px solid var(--line);
}
#ts-sidechain [data-role=toggle][data-on="1"]{
  background:#123b30;
  border-color:#1e6c57;
  color:#b9ffe8;
}
#ts-sidechain canvas{
  display:block;
  width:100%;
  height:260px;
  background:#0b0d11;
  border:1px solid var(--line);
  border-radius:12px;
}
#ts-sidechain .tss-note{
  margin-top:10px;
  font-size:12px;
  color:var(--muted);
}
#ts-sidechain .tss-status{min-height:1.4em;margin-top:8px;font-size:12px;color:var(--muted)}
@media(max-width:760px){
  #ts-sidechain .tss-grid{grid-template-columns:1fr}
}
</style>

<div>
  <h4>Sidechain: creating space in time</h4>
  <p>The kick stays unchanged. With sidechain active, the sub is lowered for an instant and then rises again.</p>
</div>

<div class="tss-grid">

  <div class="tss-controls">

<label>
  Amount
  <input data-role="amount" type="range" min="0" max="95" value="78" step="1">
  <output data-role="amountOut">78%</output>
</label>

<label>
  Attack
  <input data-role="attack" type="range" min="0" max="60" value="5" step="1">
  <output data-role="attackOut">5 ms</output>
</label>

<label>
  Release
  <input data-role="release" type="range" min="40" max="400" value="180" step="5">
  <output data-role="releaseOut">180 ms</output>
</label>

<div class="tss-buttons">
  <button type="button" data-role="play">▶ Listen</button>
  <button type="button" data-role="toggle" data-on="1" aria-pressed="true">
    Sidechain <span data-role="toggleState" aria-hidden="true">ON</span>
  </button>
</div>

<div class="tss-note">
  Demo at 124 BPM. The sub fundamental is a sine wave on F0 (~43.7 Hz in Logic’s naming convention), with a very subtle octave component to make it audible on small speakers. Headphones work best.
</div>
<div class="tss-status" data-role="status" aria-live="polite"></div>

  </div>

<canvas data-role="scope" role="img" aria-label="Visualization of the kick and sub ducking">
  The graph shows the kick and the temporary reduction in sub gain when sidechain is active.
</canvas>

</div>

<script>
(() => {
  const root = document.currentScript?.closest('.tss-widget') || document.getElementById('ts-sidechain');
  if(!root || root.dataset.ready) return;
  root.dataset.ready = '1';

  const q = role => root.querySelector(`[data-role="${role}"]`);
  const amount = q('amount');
  const attack = q('attack');
  const release = q('release');
  const amountOut = q('amountOut');
  const attackOut = q('attackOut');
  const releaseOut = q('releaseOut');
  const play = q('play');
  const toggle = q('toggle');
  const toggleState = q('toggleState');
  const status = q('status');
  const canvas = q('scope');

  const bpm = 124;
  const beat = 60 / bpm;
  const beatsPerView = 4;
  const scheduleAhead = 0.1;
  const baseSubGain = 1;
  const reducedMotion = window.matchMedia?.('(prefers-reduced-motion: reduce)').matches;

  let sideOn = true;
  let ctx = null;
  let graph = null;
  let timer = null;
  let nextKick = 0;
  let nextDuck = 0;
  let state = 'stopped';
  let startTime = 0;
  let raf = 0;
  let canvasSize = {c:null,w:0,h:0,dpr:0};

  function fitCanvas(force=false){
    const dpr = Math.min(2,Math.max(1,window.devicePixelRatio || 1));
    const rect = canvas.getBoundingClientRect();
    const width = Math.max(1,Math.round(rect.width*dpr));
    const height = Math.max(1,Math.round(rect.height*dpr));

    if(force || width !== canvas.width || height !== canvas.height){
      canvas.width = width;
      canvas.height = height;
      canvasSize = {c:canvas.getContext('2d'),w:rect.width,h:rect.height,dpr};
      canvasSize.c.setTransform(dpr,0,0,dpr,0,0);
    }

    return canvasSize;
  }

  function envelopeAt(timeInBeat){
    if(!sideOn) return 1;

    const a = +attack.value / 1000;
    const r = +release.value / 1000;
    const minimum = 1 - (+amount.value / 100);

    if(a > 0 && timeInBeat < a){
      return 1 - (1-minimum)*(timeInBeat/a);
    }

    const x = timeInBeat-a;

    if(x >= 0 && x < r){
      return minimum + (1-minimum)*(x/r);
    }

    return 1;
  }

  function kickSample(t){
    if(t < 0 || t >= 0.26) return 0;
    const startFrequency = 145;
    const endFrequency = 48;
    const sweepDuration = 0.14;
    const k = Math.log(endFrequency/startFrequency)/sweepDuration;
    const sweptTime = Math.min(t,sweepDuration);
    const sweptPhase = 2*Math.PI*startFrequency*(Math.exp(k*sweptTime)-1)/k;
    const phase = t <= sweepDuration
      ? sweptPhase
      : sweptPhase+2*Math.PI*endFrequency*(t-sweepDuration);
    const gain = t <= 0.24
      ? 0.8*Math.pow(0.001/0.8,t/0.24)
      : 0;
    return Math.sin(phase)*gain/0.8;
  }

  function draw(playhead=null){
    const {c,w,h} = fitCanvas();

    c.clearRect(0,0,w,h);
    c.fillStyle = '#0b0d11';
    c.fillRect(0,0,w,h);

    const top = h*0.34;
    const bottom = h*0.76;

    c.font = '12px system-ui';
    c.fillStyle = '#9ca3af';
    c.fillText('KICK',12,18);
    c.fillText('SUB GAIN',12,h*0.52);

    c.strokeStyle = '#252a33';
    c.lineWidth = 1;

    for(let b=0;b<=beatsPerView;b++){
      const x = (b/beatsPerView)*w;
      c.beginPath();
      c.moveTo(x,0);
      c.lineTo(x,h);
      c.stroke();
    }

    c.beginPath();
    c.strokeStyle = '#ff6b3d';
    c.lineWidth = 2;

    for(let x=0;x<=w;x++){
      const total = (x/w)*(beat*beatsPerView);
      const t = total % beat;
      const kick = kickSample(t);
      const y = top-kick*(h*0.19);

      if(x===0) c.moveTo(x,y);
      else c.lineTo(x,y);
    }

    c.stroke();

    c.beginPath();
    c.strokeStyle = '#59c3ff';
    c.lineWidth = 2.5;

    for(let x=0;x<=w;x++){
      const total = (x/w)*(beat*beatsPerView);
      const t = total % beat;
      const e = envelopeAt(t);
      const y = bottom-e*(h*0.17);

      if(x===0) c.moveTo(x,y);
      else c.lineTo(x,y);
    }

    c.stroke();

    c.fillStyle = '#59c3ff';
    c.fillText(
      sideOn ? 'ducking active' : 'no ducking',
      w-110,
      h-12
    );

    if(playhead !== null){
      const x = Math.max(0,Math.min(1,playhead))*w;

      c.strokeStyle = '#f3f4f6';
      c.globalAlpha = 0.45;
      c.beginPath();
      c.moveTo(x,0);
      c.lineTo(x,h);
      c.stroke();
      c.globalAlpha = 1;
    }
  }

  function nextGridTime(after){
    if(after <= startTime) return startTime;
    return startTime+Math.ceil((after-startTime)/beat)*beat;
  }

  function holdAndReturnToBase(now){
    if(!graph) return;
    const param = graph.subBus.gain;
    if(typeof param.cancelAndHoldAtTime === 'function'){
      param.cancelAndHoldAtTime(now);
    }else{
      param.cancelScheduledValues(now);
      param.setValueAtTime(param.value,now);
    }
    param.linearRampToValueAtTime(baseSubGain,now+0.025);
  }

  function rescheduleDucks(){
    if(state !== 'running' || !graph) return;
    const now = ctx.currentTime;
    holdAndReturnToBase(now);
    nextDuck = nextGridTime(now+0.035);
    scheduler();
  }

  function refresh(){
    amountOut.value = `${amount.value}%`;
    attackOut.value = `${attack.value} ms`;
    releaseOut.value = `${release.value} ms`;
    rescheduleDucks();
    draw();
  }

  function makeKick(t,master){
    const o = ctx.createOscillator();
    const g = ctx.createGain();
    o.type = 'sine';
    o.frequency.setValueAtTime(145,t);
    o.frequency.exponentialRampToValueAtTime(48,t+0.14);
    g.gain.setValueAtTime(0.8,t);
    g.gain.exponentialRampToValueAtTime(0.001,t+0.24);
    o.connect(g).connect(master);
    o.onended = () => {
      try{ o.disconnect(); g.disconnect(); }catch(e){}
    };
    o.start(t);
    o.stop(t+0.26);
  }

  function applyDuck(t,subBus){
    const minimum = baseSubGain*(1-(+amount.value/100));
    const a = +attack.value/1000;
    const r = +release.value/1000;
    const param = subBus.gain;
    param.setValueAtTime(baseSubGain,t);
    if(!sideOn) return;

    if(a > 0){
      param.linearRampToValueAtTime(
        Math.max(0.002,minimum),
        t+a
      );
    }else{
      param.setValueAtTime(
        Math.max(0.002,minimum),
        t
      );
    }
    param.linearRampToValueAtTime(
      baseSubGain,
      t+a+r
    );
  }

  function scheduler(){
    if(state !== 'running' || !graph) return;
    const now = ctx.currentTime;
    const horizon = now+scheduleAhead;

    if(nextKick < now-0.05) nextKick = nextGridTime(now);
    if(nextDuck < now-0.05) nextDuck = nextGridTime(now);

    while(nextKick < horizon){
      makeKick(nextKick,graph.master);
      nextKick += beat;
    }
    while(nextDuck < horizon){
      applyDuck(nextDuck,graph.subBus);
      nextDuck += beat;
    }
  }

  function animate(){
    if(state !== 'running') return;
    const bar = beat*beatsPerView;
    const elapsed = Math.max(0,ctx.currentTime-startTime);
    const position = (elapsed%bar)/bar;
    draw(position);
    raf = requestAnimationFrame(animate);
  }

  async function start(){
    if(state !== 'stopped') return;
    const AudioContextClass = window.AudioContext || window.webkitAudioContext;
    if(!AudioContextClass){
      status.textContent = 'This browser does not support the Web Audio API.';
      return;
    }

    state = 'starting';
    play.disabled = true;
    status.textContent = 'Starting audio…';

    try{
      ctx = ctx || new AudioContextClass();
      await ctx.resume();
      if(state !== 'starting'){
        await ctx.suspend().catch(() => {});
        return;
      }

      const now = ctx.currentTime;
      const master = ctx.createGain();
      const subBus = ctx.createGain();
      const subOsc = ctx.createOscillator();
      const subLevel = ctx.createGain();
      const harmonicOsc = ctx.createOscillator();
      const harmonicLevel = ctx.createGain();

      master.gain.setValueAtTime(0,now);
      master.gain.linearRampToValueAtTime(0.42,now+0.03);
      subBus.gain.setValueAtTime(baseSubGain,now);
      subOsc.type = 'sine';
      subOsc.frequency.setValueAtTime(43.65,now);
      subLevel.gain.setValueAtTime(0.18,now);
      harmonicOsc.type = 'sine';
      harmonicOsc.frequency.setValueAtTime(87.3,now);
      harmonicLevel.gain.setValueAtTime(0.025,now);

      subOsc.connect(subLevel).connect(subBus);
      harmonicOsc.connect(harmonicLevel).connect(subBus);
      subBus.connect(master).connect(ctx.destination);
      subOsc.start(now);
      harmonicOsc.start(now);

      graph = {master,subBus,subOsc,subLevel,harmonicOsc,harmonicLevel};
      startTime = now+0.06;
      nextKick = startTime;
      nextDuck = startTime;
      state = 'running';
      scheduler();
      timer = setInterval(scheduler,25);
      play.textContent = '■ Stop';
      play.disabled = false;
      status.textContent = 'Audio playing.';
      if(reducedMotion) draw();
      else animate();
    }catch(error){
      state = 'stopped';
      play.disabled = false;
      status.textContent = 'The audio could not be started.';
    }
  }

  function stop({announce=true}={}){
    if(state === 'starting'){
      state = 'stopped';
      play.disabled = false;
      status.textContent = announce ? 'Audio stopped.' : '';
      return;
    }
    if(state !== 'running' || !graph) return;
    state = 'stopping';
    play.disabled = true;
    clearInterval(timer);
    cancelAnimationFrame(raf);
    const stoppedGraph = graph;
    graph = null;
    const now = ctx.currentTime;
    stoppedGraph.master.gain.cancelScheduledValues(now);
    stoppedGraph.master.gain.setTargetAtTime(0,now,0.015);

    setTimeout(async () => {
      for(const osc of [stoppedGraph.subOsc,stoppedGraph.harmonicOsc]){
        try{ osc.stop(); }catch(e){}
      }
      try{
        stoppedGraph.subOsc.disconnect();
        stoppedGraph.harmonicOsc.disconnect();
        stoppedGraph.subLevel.disconnect();
        stoppedGraph.harmonicLevel.disconnect();
        stoppedGraph.subBus.disconnect();
        stoppedGraph.master.disconnect();
      }catch(e){}
      if(ctx?.state === 'running') await ctx.suspend().catch(() => {});
      if(state === 'stopping') state = 'stopped';
      play.disabled = false;
      play.textContent = '▶ Listen';
      status.textContent = announce ? 'Audio stopped.' : '';
    },360);
    draw();
  }

  toggle.addEventListener('click',() => {
    sideOn = !sideOn;
    toggle.dataset.on = sideOn ? '1' : '0';
    toggle.setAttribute('aria-pressed',sideOn ? 'true' : 'false');
    toggleState.textContent = sideOn ? 'ON' : 'OFF';
    rescheduleDucks();
    status.textContent = sideOn ? 'Sidechain active.' : 'Sidechain off.';
    draw();
  });

  [amount,attack,release].forEach(el => {
    el.addEventListener('input',refresh);
  });

  play.addEventListener('click',() => state === 'running' ? stop() : start());
  if('ResizeObserver' in window){
    const observer = new ResizeObserver(() => { fitCanvas(true); draw(); });
    observer.observe(canvas);
  }else{
    window.addEventListener('resize',() => { fitCanvas(true); draw(); },{passive:true});
  }
  document.addEventListener('visibilitychange',() => {
    if(document.hidden && (state === 'running' || state === 'starting')){
      stop();
      status.textContent = 'Audio stopped because the page moved to the background.';
    }
  });
  window.addEventListener('pagehide',() => stop({announce:false}),{once:true});

  fitCanvas(true);
  refresh();
})();
</script>

</div>

With sidechain off, the blue line stays flat: kick and sub occupy the same moment. Turn it on and a “hole” appears in the bass gain instead.

The three controls also reveal something I initially tended to dismiss as a technical detail. **Amount** sets how deeply the sub is lowered, **Attack** how quickly the reduction happens, and **Release** how long the bass takes to return to its normal level. With a very short release the sub comes back almost immediately; lengthen it and the classic pumping effect becomes increasingly obvious.

This is probably the first time during the project that I begin to think of the mix not as a collection of volumes, but as the management of **space**.

---

## Mid bass

For the mid bass I go back to Retro Synth, but here I can afford much more dirt: a **saw** as the main oscillator, a second oscillator to add more harmonics, a register above the sub — around **F1** — and a sixteenth-note pattern with very short notes.

### Velocity

Velocity is, to simplify, the “force” of a MIDI note. If I program sixteen perfectly evenly spaced, identical notes with the same velocity, the result quickly tends toward:

**tatatatatatatatata**

which is not exactly the human groove I was looking for.

So I vary the velocities. The grid remains extremely regular, but some notes gain more importance than others and the rhythm begins to breathe a little.

### Filter Envelope

Another discovery. The **Filter Envelope** automatically changes the filter cutoff whenever a note is played. It uses the classic ADSR parameters: **Attack**, how long the envelope takes to reach its maximum; **Decay**, how long it takes to fall after the attack; **Sustain**, the level held while the note remains pressed; and **Release**, how long it takes to return to its starting state after the note is released.

With an almost immediate attack, short decay, and low sustain, I can make the filter open quickly at the beginning of each note and close again straight afterward. The bass becomes much more **percussive**.

### Overdrive

At last I can also ruin the signal productively. **Overdrive** pushes the signal out of the linear region of the circuit or algorithm: the waveform is deformed and **new harmonics** appear. I prefer to avoid it on the sub; on the mid bass, on the other hand, it is exactly what I want.

**Drive** determines how hard I push the signal into distortion: a little means relatively gentle saturation, a lot means obvious distortion. **Tone**, meanwhile, changes the timbral character of that distortion. There are other parameters. Frankly, I do not find them interesting enough to discuss.

I then add EQ to remove some of the space already occupied by the sub from the mid bass, plus a less aggressive sidechain.

### Sub + Mid bass

At this point the split finally begins to make sense: **the sub provides the weight, the mid bass provides the personality**. More importantly, I understand something that, at least in this mix, will keep proving useful: **frequency separation comes even before volume**. If two instruments are constantly trying to occupy the same space, simply turning one down is not necessarily the answer.

### Small harmonic variations

The foundation remains centered on F. In a few places, however, I replace some notes with **Ab, C, and Eb**, all notes belonging to Fm7. I am not actually playing an Fm7 chord with the bass: I am using those notes in sequence to introduce small variations without destroying the pattern.

The idea remains: **change little, but make it count**.

---

# Automation: the sound must not stand still

This is probably one of the parts that fascinates me most. A synth can keep playing the same notes and yet appear to change constantly thanks to **automation**, which lets you alter a parameter along the timeline: cutoff, reverb, volume, send, practically anything. It is a kind of performance written in advance.

Here I finally manage to bring into focus a distinction that initially kept feeling elusive: **volume = how much signal; cutoff = which part of the spectrum**. By gradually opening the cutoff, a sound can even seem louder without me touching the fader, because entire frequency regions that were previously attenuated suddenly return. And this is exactly the kind of evolution I want in the track.

---

# Breakdown: finally splitting the drums

The more I try to build tension in the breakdown, the more obvious it becomes that having all the drums on a single track is holding me back. So I create a **Filtered Drum**, removing the kick and most of the low end and leaving mainly the lighter rhythmic elements. This lets me preserve a sense of pulse while the overall energy falls.

At this point I have **Drum, Kick, Impact Kick** — a kick used mainly to emphasize certain entrances —, **Filtered Drum, Mid bass, and Sub bass**.
I listen.
**Everything is much worse than expected.**

---

# Lead, space, and reverb

At this point I need something that gives the breakdown atmosphere. I do not want another melodically complicated part, so I build a **very simple lead** with Retro Synth: two slightly detuned saw waves — about +6 cents — a relatively slow attack, long release, and long notes in key.

More than a real melody, it should behave like a presence.

## Reverb and the discovery of buses

Here I change approach. I could place ChromaVerb directly on the lead, but instead I use a **Send**. The original signal continues normally to the Stereo Out, while at the same time I send a copy to a **Bus**, which feeds an Aux channel with ChromaVerb.

On the reverb I set Dry to 0%, Wet to 100%, with a long decay, pre-delay, and damping of the lows and highs. In practice I get two separate paths: the **dry lead** and its reverberated component.

This becomes interesting in the pauses, because I can stop the original lead completely while its **reverb tail continues to exist**. The silence is therefore not truly empty, and that is far more interesting than constantly adding something.

---

# The riff: when making things more complicated makes everything worse

I lose an amount of time on the riff that I would rather not quantify. Here too I try to build the sound from scratch, until at some point I open Alchemy and find **Blockhead**.

I like it and I use it.

Not without first covering my head in ashes after declaring at the beginning that I would try to avoid presets. The purism lasted long enough. It was not a good idea.

Now I need a chord progression. I try:

**Fm → C**
then:
**Fm → C7**

The dominant creates a great deal of tension toward Fm, but the E natural takes me toward a color I do not like in this track. I also try adding Bb.

I add things.
I remove things.
I add more things.
I like none of it.

Then I realize something fairly obvious: **I am needlessly complicating something I had decided should be simple**.

I return to the F natural minor scale and the progression becomes:
**Fm → Fm → Ab → Cm**
Fm is home, Ab opens things up, and Cm creates a much softer tension before returning to Fm.
Now we’re there.

---

# Arpeggiator

At first I try repeating the chords manually. It works, but I’m not convinced. While watching a Logic course I find **Arpeggiator**, and a light comes on: instead of writing every single note, I can hold down the chord and let the arpeggiator construct its internal movement.

I play with rate, velocity, note length, direction, and gaps in the Grid. What I want to avoid is the perfectly continuous trance-arpeggio effect, so I intentionally leave some spaces. Silence is part of the groove too.

---

# Inversions and voice leading

Here comes probably the harmonic discovery I enjoyed most. An **inversion** contains the same notes as a chord, but changes which one occupies the lowest position. For example, Ab major can be **Ab–C–Eb**, but also **Eb–Ab–C**: the notes are always the same; only their order changes.

This lets me use:

**Fm:** F – Ab – C<br>
**Ab/Eb:** Eb – Ab – C<br>
**Cm/Eb:** Eb – G – C

Something very elegant happens. From Fm to Ab, practically only one voice changes, **F → Eb**, while Ab and C stay still. Then, from Ab to Cm, **Ab → G**, while Eb and C stay still.

This is **voice leading**: arranging chords so that the individual voices move as little as possible and do so coherently. With the arpeggiator the difference is enormous: the chords stop sounding like three separate blocks and become almost **the same harmonic object slowly transforming**.

I have nothing philosophically interesting to say about the riff’s EQ: I removed whatever was getting on the bass’s nerves. The end.

For the reverb, on the other hand, I use the same system as the lead: **Send → Bus → 100% wet reverb**. I also automate the Send: as the pauses approach, I progressively send more of the riff into the reverb, then stop the MIDI. The sound disappears; the tail remains.

---

# Melody, atmosphere, and arrangement

I group several things together here because, taken separately, they do not have a particularly interesting story. The **melody** remains deliberately simple and entirely consistent with the key. The riff is already very active, so I do not need a second machine gun of notes on top: I prefer a recognizable phrase that can return throughout the track with relatively small variations. I change a few endings and note lengths, and consider the upper octave in the most intense moments (spoiler: it might have worked, but it did not convince me), but the rule remains the same: **better to recognize a melody than to hear a new one constantly**.
Still, an interesting experiment. I have always been used to finding melodies with a guitar in my hands, and something different happens there: it is a mixture of thought, muscle memory, and flow. You often pull out a phrase before you have truly thought it through and, when it works, you can almost surprise yourself.

Much less so here. In the piano roll you do not have fingers going somewhere out of habit, you do not have a fingering suggesting the next passage, and you do not have the same kind of physical improvisation. You have to imagine the phrase much more clearly before building it. I am not saying it is necessarily worse, but it is a little worse.

I also add a kind of drone on the F tonic, a note that remains essentially still while the chords change above it. The idea is to create a sort of atmosphere **without any real harmonic resolution**. I realize this sounds like pseudo-intellectual bullshit, but I did not know how else to put it. I want the saw to grow all the way to the drop and last “longer than you would expect.” The fall that follows (I lower both pitch and cents) has to be a punch in the gut. I am not entirely satisfied with the result, but this is it.

More precisely, F keeps reinforcing the tonal center without introducing a new progression. I build the sound with Retro Synth, very scratchy, almost like interference, and leave it in the background for much of the track, gradually increasing it toward the second drop.

As for the arrangement, same old story. The structure practically built itself while I was working on the sounds. The most obvious choice is to favor **relatively long builds and shorter drops**, but above all I begin to use emptiness deliberately. Before a drop, half a beat or a nearly empty beat can do more than three risers, two crashes, and a nuclear explosion.

The interesting thing is that, as the project moves forward, I notice myself adding less and less and begin asking instead: **what can I remove?**

---

# Mixing: adding one track at a time

I thought mixing would consist of adjusting a few faders. Obviously not.

First I remove any mastering from the master bus and leave the **Stereo Out at 0 dB**. I start from the fullest section of the track, the final drop, and build the mix by adding one element at a time.

I begin with **Kick + Sub** and first look for the right relationship between them. The kick has to provide the attack; the sub has to extend its weight. When I like the balance, I lower both by the same amount: their relative balance does not change, but I create **headroom**, meaning room before 0 dBFS.

I then add the mid bass and keep switching it on and off. The question becomes very simple: *when it comes in, does the bass gain personality or does it merely get bigger?* When the answer is “personality,” I stop.

Then I add the drums and suddenly the level on the Stereo Out rises much more than I expected. In my head I begin preparing EQs, compressors, and extremely complicated explanations.

Then I notice that I had left the kick in the old Drum track as well.

So:

**Dedicated kick + kick inside Drum.**

Two kicks at the same time.

I remove the duplicate.

Problem solved.

Probably one of the most educationally useful moments in the entire project: **before trying to solve a problem with a plugin, check that it is not simply a routing or arrangement mistake**.

I continue by adding **Riff → Melody → Lead → effects**, always one element at a time. At the end I listen to the entire song: no clipping, Stereo Out still at 0 dB, and a maximum premaster peak around **−3.7 dBFS**.

I am not interested in religiously reaching −6, −3, or any other number. I simply want to leave some room and avoid arriving at the next stage already crushed.

---

# Mastering

I am very tempted to use **Logic’s Mastering Assistant** directly. It might even have been easier. But after already giving in on the riff preset, I decide to at least try this part manually.

So I export the premaster at **24 bit, normalization off, and with no mastering**, then open it in a new project containing a single stereo track.

## Measure first, touch later

I insert **Loudness Meter**. The full premaster sits around **−20 LUFS Integrated**, with a very wide Loudness Range; measuring the final drop separately, however, the value rises considerably.

And here is another obvious thing I understand better after seeing it: **the loudness of the whole song is not the loudness of the drop**. If the track contains long breakdowns, pauses, and sparse sections, the overall Integrated value will inevitably fall. So there is little sense in looking at one number and deciding that I must reach X LUFS at any cost.

## Adaptive Limiter

I insert **Adaptive Limiter**. A compressor and a limiter are related, but they do not perform exactly the same job: a compressor reduces the level above a certain threshold according to a given ratio, while a limiter is used mainly as a final barrier to prevent peaks from exceeding a certain ceiling.

I set the **Out Ceiling to −1 dB** and turn **True Peak Detection ON**, then start increasing Gain. The more I raise it, the louder the track becomes, but the more the limiter also has to alter the transients.

I try **+5 dB** first and it sounds good.
I try **+7 dB**, and it sounds better.
At this point I have nothing left to go on — no more parameters or theoretical knowledge — except my own taste. I have to make do. Perhaps that is for the best.

Not simply because it is louder: to compare the two versions properly, I compensate the output level so perceived loudness does not make the decision for me. In the A/B, the drop feels more convincing without any obvious loss of kick impact. So I choose **+7 dB** and stop there. In the drop I end up roughly around **−10 LUFS Short-Term**.

I could probably push it further, but at that point the question is no longer “can I?” It is **“why?”**.

---

# Transparent betrays me

Out of curiosity, I try **Mastering Assistant → Transparent** anyway.

And I like it.
Annoyingly.

Looking at what it is doing, however, I realize that this is not simply a matter of loudness. Its Auto EQ roughly suggests reducing part of the low end, gently reinforcing the mids, and slightly attenuating the brightest frequencies.

So I decide to use Mastering Assistant not as the final solution, but as a **diagnostic tool**. I take the idea and apply it much more lightly with Channel EQ: roughly **71 Hz → −1.1 dB**, **670 Hz → +1.1 dB** with a very wide curve, and **7.1 kHz → −1 dB**.

About one dB. No surgery.

I compare the EQ on and off, prefer it on, and stop. The final chain is simply:

**Channel EQ → Adaptive Limiter → Loudness Meter**

Before exporting I make one final pass from beginning to end: I check that True Peak does not exceed the **−1 dBTP** ceiling, look at the whole track’s Integrated value without confusing it with the drop’s Short-Term figure, and keep an eye on the limiter’s maximum gain reduction — how much it is lowering the peaks. I did not write down a final Integrated value reliable enough to turn into a number worth displaying, so I will not invent one: what matters to me is that the drop remains around −10 LUFS Short-Term and that the rest of the dynamics still makes sense.

For the final bounce I stay with **24-bit WAV, normalization off**. I do not add dithering because I am not reducing the file to 16 bit; any compressed versions come afterward, starting from this master.

No multiband compressor, no saturator on the master, no eight plugins lined up because a YouTube thumbnail told me that is the secret to professional mastering. If a processor is not solving a problem, I probably do not need it.

---

# The most important part

I started by saying that one of my weak spots is **building a specific sound**. I cannot claim that I can now take anything in my head and recreate it perfectly with a synth. If only.

But something has changed. At first I saw a synthesizer mainly as a panel full of controls to move until something interesting happened; now I can at least break the problem down. I can ask where the sound begins, how harmonically rich it is, how it behaves over time, which frequencies I want to let through, how I want it to move, and where it should sit in relation to everything else.

Oscillator, waveform, and saturation therefore begin to look like different ways of answering the question *“what is this sound made of?”* Envelope, LFO, and automation instead answer *“how does it change over time?”* EQ, sidechain, and volume help determine *“where should it sit in relation to the others?”* Reverbs, buses, and pauses finally become a question of *“how much space do I want to leave around it?”*

It does not mean that I now know how to do sound design. It means that at least **I know which questions to ask**, and perhaps that is already quite a lot.

Then there is the other question I asked at the beginning: how much would my state of mind influence the decisions made during a fairly long process? The answer is almost certainly “a lot,” although I do not know how much I managed to notice while it was happening.

Listening back, I can clearly recognize choices I probably would not have made at other times: very long builds, pauses, a deliberately more aggressive second drop, a melody that does not try to resolve everything. I do not know how much of this was conscious and how much simply emerged while I was working.

This is probably also why I wanted to start from scratch. The result may be rough, derivative, technically questionable, or all three, but at least when I hear something I do not like, **it is my mistake**.

And strangely enough, I like that.

## What I am taking away from this

* A track does not become interesting by constantly increasing the number of tracks: pauses are arrangement tools too.
* Sub and mid bass have different roles; sidechain is mainly about managing space in time.
* Inversions and voice leading can make different chords feel like parts of the same movement.
* Automation can create evolution without constantly adding new notes.
* Buses make it possible to separate the direct sound from its effects.
* When mixing, it helps to start from the fundamental elements and, before adding a plugin, check whether the problem is simply a stupid mistake.
* Loudness is not a score, and mastering does not necessarily require fifteen processors.
* A preset that works is better than three hours spent defending your honor.
* **Knowing when the track is finished is part of the creative process.**

So that’s enough.
