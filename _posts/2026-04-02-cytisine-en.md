---
layout: post
title: "Cytisine"
seo_title: "Cytisine to quit smoking: how it works, efficacy and NHS reimbursement 2026"
date: 2026-03-31
categories: [farmacologia]
tags: [citisina, farmacologia, tabagismo, recettori, dipendenza]
description: "How smoking cessation drugs (really) work, with visual simulations and the latest data on reimbursement."
pixel_icon: "cytisine.png"
smooth_image: true
lang: en
ref: cytisine
---

## Premise
I'm not a psychologist, but speaking of addictions, I'd like to say a few things.

Smoking is often thought of as just a "bad habit," but from a medical and psychiatric point of view, we are talking about a true addiction, classified as such even in the diagnostic manual (the DSM-5).

But what exactly happens in our brain when we light a cigarette?

### Speed
Nicotine takes less than 10 seconds to travel from the lungs directly to the brain. It's an insanely fast delivery speed, even faster than many drugs injected intravenously.

Once it arrives in the brain, nicotine binds to specific receptors called nicotinic acetylcholine receptors. And here is where the real neurobiological trap is sprung.

The activation of these receptors causes the release of various neurotransmitters, but the real star of this story is dopamine. Nicotine stimulates the release of dopamine in the nucleus accumbens, the area of our brain that manages the pleasure and reward circuitry.

This unnatural release of dopamine makes us feel temporarily more focused, more relaxed, or simply "good." The brain registers this action (smoking) as something vital, something extremely positive, and pushes us to repeat it.

### Tolerance and Withdrawal: the snake biting its tail
If we smoke regularly, our brain defends itself against this continuous stimulation by implementing a neuroadaptation. It increases the number of receptors and reduces their sensitivity (the phenomenon of tolerance). This means we'll need more and more nicotine to get the same effect.

But the real problem arises when the nicotine level in the blood starts to drop (and it drops very quickly, within an hour or two). At that point, the brain goes into alarm mode and the withdrawal syndrome kicks in:
Irritability, anxiety, difficulty concentrating, an obsessive and uncontrollable desire to smoke (craving).

## Don't have willpower?
How much I hate this Americanized rhetoric of "if you want it, you can do it", damn you Tony Robbins.
**Willpower alone is overrated**. In fact, it often turns into a real trap. It's not that you lack willpower: nicotine has literally **hijacked** your mesolimbic system, making the brain believe that smoking is an action linked to survival.

From a neurobiological point of view, what we call "willpower" (inhibitory control and the ability to delay gratification) resides mainly in our prefrontal cortex. It's the most evolved part of our brain, responsible for reasoning, long-term planning, and impulse control.

The problem is that this cognitive function consumes a ton of metabolic energy. You can think of it as your smartphone's battery: in the morning, after a good night's sleep, it's 100% charged. But throughout the day, every time we make a decision, suppress a negative emotion at work, or resist a temptation, we consume "bars" of battery.

Although Baumeister's ego depletion model has been downsized by the replication crisis in psychology, the clinical observation that relapses occur mostly at the end of the day or under stress remains solid and well-documented, regardless of the theoretical framework used to explain it. By evening, the battery is dead. Our prefrontal cortex "shuts down" and the older areas of the brain (like the limbic system) inevitably take over, guided by habit, emotion, and the immediate search for pleasure or relief. This is why food binges or "slips" into addictions almost always happen at the end of the day or during periods of high stress.

At a certain point in a smoker's life, you no longer smoke to experience pleasure, but to turn off the withdrawal. You simply smoke to feel "normal" again, the way a non-smoker feels all day long.

## How (almost) everything that acts on the brain works

Let's start by saying that most molecules acting on the Central Nervous System (very, very roughly: what in common parlance is the Brain) bind ("activate") at least one receptor.

Obviously "they bind to a receptor" means *a type* of receptor. Like in a field of flowers, there are various types of flowers — the Daisy (*Leucanthemum vulgare*), the Cornflower (*Centaurea cyanus*) — and there are many Daisies and many Cornflowers. If a parasite (in our analogy: the agonist molecule) attacks the daisy (the receptor), it doesn't attack just one daisy, it attacks them all. It "binds" to all flowers of the same type.

Generally, upon the activation of this receptor, other molecules are released which activate other complex cascading mechanisms, often also in other regions of the brain.

### How a receptor works, in short

*aka the part I'm most proud of and which legitimately nobody cares about*

Remember the classic "Home Alone"? All the booby traps Kevin sets up to protect himself from the burglars? Every time one of the two unfortunate thieves opens a door, a complicated system of pulleys triggers the trap. Now imagine there's not just one trap connected to a door, but multiple traps. The wider the door opens, the more traps spring.

Well, translated into pharmacology:

1. An **agonist** molecule is like a key: it serves to open the door. Traps galore.
2. An **antagonist**, on the other hand, is a key that manages to fit into the lock but doesn't open it and gets stuck, preventing the right key from entering. No traps.
3. A **partial agonist** is the interesting one: it manages to open the lock, but not the chain attached behind the door — it springs some traps, but not all of them. Those few are such that they are *not* "enough".

*For the pedantic ones: it seems that receptors oscillate between an active and an inactive state, and the partial agonist binds to the receptors locking them in that instant. Those that are active at that moment remain locked in active mode, the others remain locked in inactive mode.*

<div id="ligand-receptor-sim" style="max-width: 700px; margin: 2rem auto;">
<style>
  :root {
    --blog-bg: transparent;
    --blog-card-bg: var(--card-bg, #ffffff);
    --blog-text: var(--text-color, #222222);
    --blog-text-muted: var(--text-muted, #6b7280);
    --blog-border: var(--border-color, #e5e5e5);
    --blog-btn-bg: var(--card-bg, #ffffff);
    --blog-btn-hover: var(--bg-color, #f3f4f6);
    --c-nicotina: #D85A30;
    --bg-nicotina: #FAECE7;
    --c-antagonista: #5F5E5A;
    --bg-antagonista: #F1EFE8;
    --c-citisina: #EF9F27;
    --bg-citisina: #FAEEDA;
    --c-dopamina: #7F77DD;
    --c-ion: #3b82f6;
    --c-recettore: #f9fafb;
    --c-membrana: #B4B2A9;
    --shadow-color: rgba(0,0,0,0.08);
  }
  @media (prefers-color-scheme: dark) {
    :root:not([data-theme="light"]) {
      --c-recettore: #374151;
      --bg-nicotina: #4c1d0f;
      --bg-antagonista: #374151;
      --bg-citisina: #452403;
      --c-ion: #60a5fa;
      --shadow-color: rgba(0,0,0,0.3);
    }
  }
  :root[data-theme="dark"] {
    --c-recettore: #374151;
    --bg-nicotina: #4c1d0f;
    --bg-antagonista: #374151;
    --bg-citisina: #452403;
    --c-ion: #60a5fa;
    --shadow-color: rgba(0,0,0,0.3);
  }

  #ligand-receptor-sim { 
    color: var(--blog-text); 
    background: var(--blog-card-bg);
    border-radius: 16px;
    padding: 24px 16px;
    box-shadow: 0 10px 40px -10px var(--shadow-color);
    border: 1px solid var(--blog-border);
    box-sizing: border-box;
  }
  
  #ligand-receptor-sim .lr2-buttons { display: flex; flex-wrap: wrap; gap: 10px; justify-content: center; margin-bottom: 20px; }
  
  #ligand-receptor-sim .lr2-btn { 
    padding: 9px 16px; 
    border: 1px solid var(--blog-border); 
    border-radius: 8px; 
    background: var(--blog-btn-bg); 
    color: var(--blog-text); 
    cursor: pointer; 
    font-size: 13.5px; 
    font-family: inherit; 
    font-weight: 500; 
    transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1); 
    box-shadow: 0 2px 4px var(--shadow-color); 
  }
  #ligand-receptor-sim .lr2-btn:hover { background: var(--blog-btn-hover); transform: translateY(-1.5px); box-shadow: 0 4px 8px var(--shadow-color); }
  #ligand-receptor-sim .lr2-btn.sel-ag { background: var(--bg-nicotina); border-color: var(--c-nicotina); color: var(--c-nicotina); }
  #ligand-receptor-sim .lr2-btn.sel-an { background: var(--bg-antagonista); border-color: var(--c-antagonista); color: var(--c-antagonista); }
  #ligand-receptor-sim .lr2-btn.sel-pa { background: var(--bg-citisina); border-color: var(--c-citisina); color: var(--c-citisina); }
  #ligand-receptor-sim .lr2-btn.sel-no { background: var(--blog-btn-hover); border-color: var(--blog-text-muted); }
  
  #ligand-receptor-sim .lr2-desc { 
    text-align: center; 
    font-size: 14px; 
    color: var(--blog-text-muted); 
    min-height: 52px; 
    line-height: 1.6; 
    max-width: 620px; 
    margin: 16px auto 0; 
    padding: 12px; 
    background: var(--blog-btn-bg); 
    border-radius: 8px; 
    border: 1px dashed var(--blog-border); 
  }
  #ligand-receptor-sim .lr2-desc strong { color: var(--blog-text); font-weight: 600; }
  
  @keyframes lr2float { 0%{transform:translateY(0);opacity:.75} 100%{transform:translateY(-22px);opacity:0} }
  @keyframes lr2ion { 0%{transform:translateY(0);opacity:0} 10%{opacity:1} 85%{opacity:1} 100%{transform:translateY(180px);opacity:0} }
  @keyframes lr2ion-bounce-l { 0% { transform: translate(0,0); opacity: 0; } 20% { opacity: 1; } 50% { transform: translate(0, 75px); opacity: 1; } 100% { transform: translate(-35px, 30px); opacity: 0; } }
  @keyframes lr2ion-bounce-r { 0% { transform: translate(0,0); opacity: 0; } 20% { opacity: 1; } 50% { transform: translate(0, 75px); opacity: 1; } 100% { transform: translate(35px, 30px); opacity: 0; } }
  @keyframes lr2dopa-pulse { 0%, 100% { opacity: .65; } 50% { opacity: .95; } }
  @media (prefers-reduced-motion:reduce) { #ligand-receptor-sim .lr2-dopa, #ligand-receptor-sim circle { animation:none!important; } }
  
  #ligand-receptor-sim .lr2-label {
    fill: var(--blog-text);
    font-weight: 600;
    paint-order: stroke fill;
    stroke: var(--blog-card-bg);
    stroke-width: 2px;
    stroke-linecap: round;
    stroke-linejoin: round;
  }
  #ligand-receptor-sim .lr2-label-bold { font-weight: 800; fill: var(--blog-text); }
</style>

<div class="lr2-buttons" role="group" aria-label="Seleziona il ligando da simulare">
  <button class="lr2-btn sel-no" onclick="lr2Set('none')" id="lr2b-none" aria-controls="lr2-desc">No ligand</button>
  <button class="lr2-btn" onclick="lr2Set('agonist')" id="lr2b-agonist" aria-controls="lr2-desc">Agonist (Nicotine)</button>
  <button class="lr2-btn" onclick="lr2Set('antagonist')" id="lr2b-antagonist" aria-controls="lr2-desc">Antagonist</button>
  <button class="lr2-btn" onclick="lr2Set('partial')" id="lr2b-partial" aria-controls="lr2-desc">Partial agonist (Cytisine)</button>
</div>

<svg id="lr2svg" width="100%" viewBox="0 0 680 440" role="img" aria-label="Simulazione visiva interattiva dei recettori nicotinici sulla membrana cellulare. Mostra i canali recettoriali che si aprono o rimangono chiusi a seconda del ligando.">
  <g aria-hidden="true">
    <defs>
      <filter id="lr2-shadow" x="-20%" y="-20%" width="140%" height="140%">
        <feDropShadow dx="0" dy="4" stdDeviation="4" flood-color="#000" flood-opacity="0.12"/>
      </filter>
      <filter id="lr2-mol-shadow" x="-30%" y="-30%" width="160%" height="160%">
        <feDropShadow dx="0" dy="2" stdDeviation="1.5" flood-color="#000" flood-opacity="0.2"/>
      </filter>

      <linearGradient id="lr2mem-bg" x1="0" y1="0" x2="0" y2="1">
        <stop offset="0%" style="stop-color:var(--c-membrana); stop-opacity:.3"/>
        <stop offset="20%" style="stop-color:var(--c-membrana); stop-opacity:.05"/>
        <stop offset="80%" style="stop-color:var(--c-membrana); stop-opacity:.05"/>
        <stop offset="100%" style="stop-color:var(--c-membrana); stop-opacity:.3"/>
      </linearGradient>

      <pattern id="lipid" x="0" y="0" width="14" height="80" patternUnits="userSpaceOnUse" patternTransform="translate(0, 180)">
        <circle cx="7" cy="6" r="4.5" fill="var(--c-membrana)" opacity="0.85"/>
        <path d="M 5,10 Q 2,22 6,37 M 9,10 Q 12,22 8,37" fill="none" stroke="var(--c-membrana)" stroke-width="1.2" opacity="0.6" stroke-linecap="round"/>
        <circle cx="7" cy="74" r="4.5" fill="var(--c-membrana)" opacity="0.85"/>
        <path d="M 5,70 Q 2,58 6,43 M 9,70 Q 12,58 8,43" fill="none" stroke="var(--c-membrana)" stroke-width="1.2" opacity="0.6" stroke-linecap="round"/>
      </pattern>

      <g id="rec-body" filter="url(#lr2-shadow)">
        <path d="M-48,158 C-52,158 -56,162 -56,168 L-56,260 C-56,266 -52,270 -48,270 L-24,270 L-24,240 C-24,232 -20,226 -14,224 L-14,198 C-20,196 -24,190 -24,182 L-24,158 Z" style="fill:var(--c-recettore); stroke:var(--blog-border); stroke-width:1.2"/>
        <path d="M48,158 C52,158 56,162 56,168 L56,260 C56,266 52,270 48,270 L24,270 L24,240 C24,232 20,226 14,224 L14,198 C20,196 24,190 24,182 L24,158 Z" style="fill:var(--c-recettore); stroke:var(--blog-border); stroke-width:1.2"/>
        <path d="M-24,158 L-24,182 C-24,190 -18,196 -12,196 L-10,196 C-8,196 -7,194 -7,192 L-7,178 C-7,172 -4,168 0,168 C4,168 7,172 7,178 L7,192 C7,194 8,196 10,196 L12,196 C18,196 24,190 24,182 L24,158 Z" fill="none" style="stroke:var(--blog-border)" stroke-width="1" stroke-dasharray="3 2"/>
      </g>
    </defs>

    <text x="340" y="20" text-anchor="middle" class="lr2-label" style="font-size:10px;letter-spacing:1px;font-weight:600;">EXTRACELLULAR SPACE</text>
    <rect x="0" y="180" width="680" height="80" fill="url(#lr2mem-bg)"/>
    <rect x="0" y="180" width="680" height="80" fill="url(#lipid)"/>
    <line x1="0" y1="180" x2="680" y2="180" style="stroke:var(--c-membrana); stroke-opacity:0.4; stroke-width:1"/>
    <line x1="0" y1="260" x2="680" y2="260" style="stroke:var(--c-membrana); stroke-opacity:0.4; stroke-width:1"/>
    
    <text x="35" y="224" text-anchor="middle" class="lr2-label" style="font-size:11px;">Membrane</text>
    <text x="340" y="426" text-anchor="middle" class="lr2-label" style="font-size:10px;letter-spacing:1px;font-weight:600;">INTRACELLULAR SPACE</text>

    <g id="lr2-ion-pool"></g> 

    <g id="receptors">
      <g id="rec0" transform="translate(120,0)">
        <use href="#rec-body" />
        <rect id="gate0-l" x="-14" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <rect id="gate0-r" x="2" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <g id="bound0" opacity="0"></g>
      </g>
      <g id="rec1" transform="translate(255,0)">
        <use href="#rec-body" />
        <rect id="gate1-l" x="-14" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <rect id="gate1-r" x="2" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <g id="bound1" opacity="0"></g>
      </g>
      <g id="rec2" transform="translate(390,0)">
        <use href="#rec-body" />
        <rect id="gate2-l" x="-14" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <rect id="gate2-r" x="2" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <g id="bound2" opacity="0"></g>
      </g>
      <g id="rec3" transform="translate(525,0)">
        <use href="#rec-body" />
        <rect id="gate3-l" x="-14" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <rect id="gate3-r" x="2" y="204" width="12" height="46" rx="3" style="fill:var(--blog-border); stroke:var(--blog-text-muted)" stroke-width=".5"/>
        <g id="bound3" opacity="0"></g>
      </g>
    </g>

    <g id="lr2-nic-pool"></g>
    <g id="lr2-dopa-pool"></g>

    <text x="600" y="178" class="lr2-label" style="font-size:11px;">Binding</text>
    <text x="600" y="192" class="lr2-label" style="font-size:11px;">pocket</text>
    <line x1="550" y1="175" x2="595" y2="175" style="stroke:var(--blog-border)" stroke-width=".5" stroke-dasharray="3 3"/>
    <circle cx="550" cy="175" r="1.5" style="fill:var(--blog-text-muted)"/>

    <text x="600" y="230" class="lr2-label" style="font-size:11px;">Channel state</text>
    <text id="lr2-gate-label" x="600" y="244" class="lr2-label lr2-label-bold" style="font-size:11px;">Closed</text>
    <line x1="535" y1="227" x2="595" y2="227" style="stroke:var(--blog-border)" stroke-width=".5" stroke-dasharray="3 3"/>
    <circle cx="535" cy="227" r="1.5" style="fill:var(--blog-text-muted)"/>

    <g transform="translate(15,300)">
      <rect x="-8" y="-15" width="185" height="135" rx="6" fill="var(--blog-card-bg)" opacity="0.85" />
      <text x="0" y="0" class="lr2-label" style="font-size:11px;">Molecular forms legend:</text>
      <path d="M10,18 L22,12 L30,18 L26,26 L14,26 Z" style="fill:var(--c-nicotina); stroke:var(--blog-border)" opacity=".7" stroke-width=".5"/>
      <text x="38" y="23" class="lr2-label" style="font-size:11px;">Nicotine</text>
      <rect x="8" y="34" width="24" height="16" rx="2" style="fill:var(--c-antagonista); stroke:var(--blog-border)" opacity=".7" stroke-width=".5"/>
      <text x="38" y="47" class="lr2-label" style="font-size:11px;">Antagonist</text>
      <path d="M10,58 C10,54 14,52 20,52 C26,52 30,54 30,58 L28,66 C28,68 26,70 20,70 C14,70 12,68 12,66 Z" style="fill:var(--c-citisina); stroke:var(--blog-border)" opacity=".7" stroke-width=".5"/>
      <text x="38" y="67" class="lr2-label" style="font-size:11px;">Cytisine</text>
      <circle cx="20" cy="85" r="3.5" style="fill:var(--c-ion)"/>
      <text x="38" y="88" class="lr2-label" style="font-size:11px;">Ions / Charges (Na+ / Ca2+)</text>
      <circle cx="20" cy="105" r="3.5" style="fill:var(--c-dopamina)"/>
      <text x="38" y="108" class="lr2-label" style="font-size:11px;">Released dopamine</text>
    </g>
  </g>
</svg>

<div class="lr2-desc" id="lr2-desc" aria-live="polite">Select a ligand to observe the dynamics on the receptor population.</div>
</div>

<script>
(function(){
  var S = 'none';
  var timers = [];
  var NS = 'http://www.w3.org/2000/svg';
  var tickRAF = null;
  var lastTick = 0;
  var TICK_INTERVAL = 160;
  
  var centers = [120, 255, 390, 525];
  var recStates = [0, 0, 0, 0];

  var DESC = {
    none: 'Receptors are at rest. No ligand bound, channels are <strong>closed</strong> (no ions pass), no dopamine released.',
    agonist: '<strong>Nicotine</strong> molecules dynamically bind to the 4 receptors. Channels open: <strong>charges flow inward</strong> causing a massive release of dopamine.',
    antagonist: 'The <strong>antagonist</strong> stably blocks all 4 receptors. Nicotine bounces off and channels remain closed: <strong>no ion passage</strong>.',
    partial: '<strong>Cytisine</strong> binds to all receptors, but lacks the strength to open them all. <strong>3 open weakly, 1 remains closed</strong> despite being occupied. Fewer ions pass = less dopamine.'
  };

  function nicPath(cx,cy,s){s=s||1;return'M'+(cx-10*s)+','+cy+' L'+(cx-2*s)+','+(cy-8*s)+' L'+(cx+8*s)+','+(cy-2*s)+' L'+(cx+10*s)+','+(cy+4*s)+' L'+(cx+2*s)+','+(cy+10*s)+' L'+(cx-6*s)+','+(cy+8*s)+' Z';}
  function antPath(cx,cy,s){s=s||1;var w=14*s,h=10*s,r=2*s;return'M'+(cx-w/2+r)+','+(cy-h/2)+' L'+(cx+w/2-r)+','+(cy-h/2)+' Q'+(cx+w/2)+','+(cy-h/2)+' '+(cx+w/2)+','+(cy-h/2+r)+' L'+(cx+w/2)+','+(cy+h/2-r)+' Q'+(cx+w/2)+','+(cy+h/2)+' '+(cx+w/2-r)+','+(cy+h/2)+' L'+(cx-w/2+r)+','+(cy+h/2)+' Q'+(cx-w/2)+','+(cy+h/2)+' '+(cx-w/2)+','+(cy+h/2-r)+' L'+(cx-w/2)+','+(cy-h/2+r)+' Q'+(cx-w/2)+','+(cy-h/2)+' '+(cx-w/2+r)+','+(cy-h/2)+' Z';}
  function cytPath(cx,cy,s){s=s||1;return'M'+(cx-10*s)+','+(cy-2*s)+' C'+(cx-10*s)+','+(cy-8*s)+' '+(cx-4*s)+','+(cy-10*s)+' '+cx+','+(cy-10*s)+' C'+(cx+4*s)+','+(cy-10*s)+' '+(cx+10*s)+','+(cy-8*s)+' '+(cx+10*s)+','+(cy-2*s)+' L'+(cx+8*s)+','+(cy+6*s)+' C'+(cx+7*s)+','+(cy+9*s)+' '+(cx+4*s)+','+(cy+10*s)+' '+cx+','+(cy+10*s)+' C'+(cx-4*s)+','+(cy+10*s)+' '+(cx-7*s)+','+(cy+9*s)+' '+(cx-8*s)+','+(cy+6*s)+' Z';}

  function makeMol(type,cx,cy,s){
    var p=document.createElementNS(NS,'path');
    if(type==='agonist'){p.setAttribute('d',nicPath(cx,cy,s||1));p.style.fill='var(--c-nicotina)';p.style.stroke='var(--c-nicotina)';}
    else if(type==='antagonist'){p.setAttribute('d',antPath(cx,cy,s||1));p.style.fill='var(--c-antagonista)';p.style.stroke='var(--c-antagonista)';}
    else{p.setAttribute('d',cytPath(cx,cy,s||1));p.style.fill='var(--c-citisina)';p.style.stroke='var(--c-citisina)';}
    p.setAttribute('stroke-width','0.8');
    p.setAttribute('filter','url(#lr2-mol-shadow)');
    return p;
  }

  function clearAll(){
    timers.forEach(function(t){clearTimeout(t);});
    timers=[];
    if (tickRAF) { cancelAnimationFrame(tickRAF); tickRAF = null; }
    document.getElementById('lr2-nic-pool').innerHTML='';
    document.getElementById('lr2-dopa-pool').innerHTML='';
    document.getElementById('lr2-ion-pool').innerHTML='';
    for(var i=0; i<4; i++){
      document.getElementById('bound'+i).innerHTML='';
      document.getElementById('bound'+i).setAttribute('opacity','0');
      setRecGate(i, 0);
    }
  }

  function setRecGate(i, state) {
    recStates[i] = state;
    var gl = document.getElementById('gate'+i+'-l');
    var gr = document.getElementById('gate'+i+'-r');
    if (state === 1) {
      gl.setAttribute('x', '-24'); gr.setAttribute('x', '16');
      gl.setAttribute('width', '8'); gr.setAttribute('width', '8');
    } else if (state === 2) {
      gl.setAttribute('x', '-17'); gr.setAttribute('x', '9');
      gl.setAttribute('width', '8'); gr.setAttribute('width', '8');
    } else {
      gl.setAttribute('x', '-14'); gr.setAttribute('x', '2');
      gl.setAttribute('width', '12'); gr.setAttribute('width', '12');
    }
    updateGateLabel();
  }

  function updateGateLabel() {
    var lbl = document.getElementById('lr2-gate-label');
    if (S === 'agonist') lbl.textContent = 'All open';
    else if (S === 'partial') lbl.textContent = '3 open, 1 closed';
    else lbl.textContent = 'All closed';
  }

  function animMove(el, startX, startY, endX, endY, dur, cb){
    var start=null;
    function step(ts){
      if(!start)start=ts;
      var p=Math.min((ts-start)/dur,1);
      var ease=1-Math.pow(1-p,2);
      var cx=startX + (endX-startX)*ease;
      var cy=startY + (endY-startY)*ease;
      el.setAttribute('transform','translate('+(cx-startX)+','+(cy-startY)+')');
      if(p<1)requestAnimationFrame(step);else if(cb)cb();
    }
    requestAnimationFrame(step);
  }

  function startIonDopaLoop() {
    lastTick = 0;
    function tick(now) {
      if (S === 'none') { tickRAF = null; return; }
      if (now - lastTick < TICK_INTERVAL) { tickRAF = requestAnimationFrame(tick); return; }
      lastTick = now;

      for(var i=0; i<4; i++) {
        if (recStates[i] > 0) {
          var ionThreshold = recStates[i] === 1 ? 0.3 : 0.7;
          if (Math.random() > ionThreshold) {
             var ion = document.createElementNS(NS, 'circle');
             ion.setAttribute('cx', centers[i] + (Math.random()*6-3));
             ion.setAttribute('cy', 80 + Math.random()*30);
             ion.setAttribute('r', 2);
             ion.style.fill = 'var(--c-ion)';
             ion.style.animation = 'lr2ion 1.1s linear forwards';
             document.getElementById('lr2-ion-pool').appendChild(ion);
             ion.addEventListener('animationend', function() { if(ion.parentNode) ion.parentNode.removeChild(ion); });
          }
          var dopaThreshold = recStates[i] === 1 ? 0.6 : 0.94;
          if (Math.random() > dopaThreshold) {
             var dopa = document.createElementNS(NS, 'circle');
             dopa.setAttribute('cx', centers[i] + (Math.random()*40-20));
             dopa.setAttribute('cy', 280 + Math.random()*20);
             dopa.setAttribute('r', 3.5 + Math.random()*2.5);
             dopa.style.fill = 'var(--c-dopamina)';
             dopa.setAttribute('opacity', '.7');
             var dur = 1.4+Math.random();
             if (S === 'agonist') {
               var pulseSpeed = 0.4 + Math.random() * 0.3;
               dopa.style.animation = 'lr2float ' + dur + 's ease-out forwards, lr2dopa-pulse ' + pulseSpeed + 's ease-in-out infinite alternate';
             } else {
               dopa.style.animation = 'lr2float ' + dur + 's ease-out forwards';
             }
             document.getElementById('lr2-dopa-pool').appendChild(dopa);
             dopa.addEventListener('animationend', function(e) { if(e.animationName === 'lr2float' && dopa.parentNode) dopa.parentNode.removeChild(dopa); });
          }
        } else if (S === 'antagonist' || S === 'partial') {
          if (Math.random() > 0.85) {
             var ion2 = document.createElementNS(NS, 'circle');
             ion2.setAttribute('cx', centers[i] + (Math.random()*20-10));
             ion2.setAttribute('cy', 70 + Math.random()*15);
             ion2.setAttribute('r', 2);
             ion2.style.fill = 'var(--c-ion)';
             var anim = Math.random() > 0.5 ? 'lr2ion-bounce-l' : 'lr2ion-bounce-r';
             ion2.style.animation = anim + ' 0.8s ease-out forwards';
             document.getElementById('lr2-ion-pool').appendChild(ion2);
             ion2.addEventListener('animationend', function() { if(ion2.parentNode) ion2.parentNode.removeChild(ion2); });
          }
        }
      }
      tickRAF = requestAnimationFrame(tick);
    }
    tickRAF = requestAnimationFrame(tick);
  }

  function spawnBouncingNic(){
    var pool=document.getElementById('lr2-nic-pool');
    function go(){
      if(S!=='antagonist'&&S!=='partial')return;
      var count = 1 + Math.floor(Math.random()*3);
      for(var j=0; j<count; j++) {
        (function(){
          var sx=50+Math.random()*580, g=document.createElementNS(NS,'g');
          var sy=10+Math.random()*30;
          g.appendChild(makeMol('agonist',sx,sy,0.9));
          pool.appendChild(g);
          animMove(g, sx, sy, sx + (Math.random()*40-20), 145 + Math.random()*10, 400+Math.random()*200, function(){
            var bx=sx+(Math.random()>.5?1:-1)*(40+Math.random()*80),by=40+Math.random()*60,st=null;
            function bounce(ts){
              if(!st)st=ts;
              var p=Math.min((ts-st)/500,1);
              var cx2=sx+(bx-sx)*p,cy2=145+(by-145)*p-40*Math.sin(Math.PI*p);
              g.setAttribute('transform','translate('+(cx2-sx)+','+(cy2-sy)+')');
              g.firstChild.setAttribute('opacity',String(1-p));
              if(p<1)requestAnimationFrame(bounce);else{if(g.parentNode)g.parentNode.removeChild(g);}
            }
            requestAnimationFrame(bounce);
          });
        })();
      }
      timers.push(setTimeout(go,300+Math.random()*300));
    }
    timers.push(setTimeout(go,200));
  }

  function spawnAmbient(allowedStates) {
     function go() {
         if(!allowedStates.includes(S)) return;
         var x=50+Math.random()*580, y=20+Math.random()*80;
         var amb=document.createElementNS(NS,'g');
         amb.appendChild(makeMol('agonist', x, y, 0.9));
         document.getElementById('lr2-nic-pool').appendChild(amb);
         amb.setAttribute('opacity', '0');
         
         var ex=x+(Math.random()>.5?1:-1)*60, ey=y+(Math.random()>.5?1:-1)*30, st=null;
         function drift(ts) {
             if(!st) st=ts;
             var p=Math.min((ts-st)/2000, 1);
             amb.setAttribute('transform', 'translate('+((ex-x)*p)+','+((ey-y)*p)+')');
             var op = p<0.2 ? p/0.2 : (p>0.8 ? (1-p)/0.2 : 1);
             amb.setAttribute('opacity', String(op*0.5));
             if(p<1) requestAnimationFrame(drift);
             else if(amb.parentNode) amb.parentNode.removeChild(amb);
         }
         requestAnimationFrame(drift);
         timers.push(setTimeout(go, 500+Math.random()*500));
     }
     go();
     timers.push(setTimeout(go, 200));
  }

  function cycleAgonist(i){
    if(S!=='agonist')return;
    var cx = centers[i];
    var sx = cx + (Math.random()*120 - 60); 
    var sy = 10 + Math.random()*40;
    var g = document.createElementNS(NS,'g');
    g.appendChild(makeMol('agonist', sx, sy, 1.1));
    document.getElementById('lr2-nic-pool').appendChild(g);
    
    animMove(g, sx, sy, cx, 155, 450 + Math.random()*200, function(){
      if(S!=='agonist'){if(g.parentNode)g.parentNode.removeChild(g);return;}
      if(g.parentNode)g.parentNode.removeChild(g);
      
      var bound = document.getElementById('bound'+i);
      bound.innerHTML='';
      bound.appendChild(makeMol('agonist', 0, 172, 1.1));
      bound.setAttribute('opacity','1');
      setRecGate(i, 1);
      
      timers.push(setTimeout(function(){
        if(S!=='agonist')return;
        bound.innerHTML='';
        setRecGate(i, 0);
        
        var floatAway=document.createElementNS(NS,'g');
        floatAway.appendChild(makeMol('agonist', cx, 172, 1.1));
        document.getElementById('lr2-nic-pool').appendChild(floatAway);
        
        var ex=cx+(Math.random()>.5?1:-1)*(40+Math.random()*80), ey=20+Math.random()*60, st=null;
        function floatOut(ts) {
            if(!st) st=ts;
            var p=Math.min((ts-st)/400, 1);
            floatAway.setAttribute('transform', 'translate('+((ex-cx)*p)+','+((ey-172)*p)+')');
            floatAway.firstChild.setAttribute('opacity', String(1-p));
            if(p<1) requestAnimationFrame(floatOut);
            else if(floatAway.parentNode) floatAway.parentNode.removeChild(floatAway);
        }
        requestAnimationFrame(floatOut);
        
        timers.push(setTimeout(function(){ cycleAgonist(i); }, 150 + Math.random()*300));
      }, 600 + Math.random()*400));
    });
  }

  function runAgonist(){
    spawnAmbient(['agonist']);
    for(var i=0; i<4; i++){
       (function(idx){ timers.push(setTimeout(function(){ cycleAgonist(idx); }, Math.random()*600)); })(i);
    }
    startIonDopaLoop();
  }

  function runAntagonist(){
    spawnAmbient(['antagonist']); 
    spawnBouncingNic();
    for(var i=0; i<4; i++){
      (function(idx){
        var g = document.createElementNS(NS,'g');
        g.appendChild(makeMol('antagonist', centers[idx], 40, 1.2));
        document.getElementById('lr2-nic-pool').appendChild(g);
        animMove(g, centers[idx], 40, centers[idx], 155, 550 + Math.random()*150, function(){
          if(g.parentNode) g.parentNode.removeChild(g);
          var bound = document.getElementById('bound'+idx);
          bound.innerHTML='';
          bound.appendChild(makeMol('antagonist', 0, 172, 1.2));
          bound.setAttribute('opacity','1');
          setRecGate(idx, 0);
        });
      })(i);
    }
    startIonDopaLoop();
  }

  function runPartial(){
    spawnAmbient(['partial']); 
    spawnBouncingNic();
    for(var i=0; i<4; i++){
      (function(idx){
        var g = document.createElementNS(NS,'g');
        g.appendChild(makeMol('partial', centers[idx], 40, 1.1));
        document.getElementById('lr2-nic-pool').appendChild(g);
        animMove(g, centers[idx], 40, centers[idx], 155, 550 + Math.random()*150, function(){
          if(g.parentNode) g.parentNode.removeChild(g);
          var bound = document.getElementById('bound'+idx);
          bound.innerHTML='';
          bound.appendChild(makeMol('partial', 0, 172, 1.1));
          bound.setAttribute('opacity','1');
          if (idx === 1) setRecGate(idx, 0); 
          else setRecGate(idx, 2);
        });
      })(i);
    }
    startIonDopaLoop();
  }

  window.lr2Set=function(type){
    S=type;
    clearAll();
    document.querySelectorAll('#ligand-receptor-sim .lr2-btn').forEach(function(b){b.className='lr2-btn';});
    var cls={none:'sel-no',agonist:'sel-ag',antagonist:'sel-an',partial:'sel-pa'};
    document.getElementById('lr2b-'+type).classList.add(cls[type]);
    document.getElementById('lr2-desc').innerHTML=DESC[type];
    
    if(type==='agonist')runAgonist();
    else if(type==='antagonist')runAntagonist();
    else if(type==='partial')runPartial();
  };
})();
</script>

In the simulation, you can see that not all receptors respond in the same way when cytisine is bound — this is what makes its agonism "partial": on the receptor population, the overall activation is reduced.

## The mechanism of nicotine addiction

Nicotine does the same thing: it binds to nicotinic acetylcholine receptors (nAChR, subtype α4β2 bla bla) and releases, among other things, **dopamine**. In the script you can see well how nicotine has a "dynamic" bond with the receptor. It is exactly this attach-detach action that is the main problem. Simplifying greatly, this is what generates addiction: the constant search for dopamine's well-being.

If you think this "well-being" is desirable, it's because we confuse hedonistic pleasure with happiness. But that's another story.

## How to 'hack' addiction

To break this vicious circle, various methods are used:

1. **Nicotine Replacement Therapy (NRT)** — the most famous. Slow-release patches, nasal sprays, inhalers, gums. The idea is simple: a characteristic of addictions is the *rapid* release of dopamine. If you provide nicotine slowly, you reduce the reinforcement effect without sending the patient into total withdrawal. ~~It's like methadone, but socially acceptable.~~

2. **Bupropion** — an antidepressant that works both by increasing the presence of dopamine on its own and by inhibiting the release of dopamine stimulated by nicotine (plus some other things on muscarinic receptors, but let's not overcomplicate it). It has the flaw of bringing along the side effect profile of antidepressants, which is not exactly a plus. In Italy, Zyban (the only formulation with a specific indication for smoking cessation) is no longer on the market, although the active ingredient is sometimes prescribed *off-label* via other brands born as antidepressants (e.g., Wellbutrin).

3. **Partial agonists: Varenicline and Cytisine** — and here is where things get interesting.

## Cytisine: the partial agonist from the laburnum tree

We've arrived: cytisine is a natural alkaloid extracted from *Cytisus laburnum* (the golden chain tree — the one with beautiful yellow clusters of flowers you've probably seen a thousand times without knowing what it was). It has been used in Eastern Europe for over sixty years. Sixty years. And we are only discovering it now. Why? Honestly, I don't know.

Varenicline and cytisine work as **partial agonists** of the α4β2 nicotinic receptors — the same locks nicotine acts upon. The result is a twofold mechanism:

- **Agonist effect** (calming): they partially stimulate the receptors, relieving craving and withdrawal symptoms. Some of Kevin's traps spring, enough to keep you from going crazy.
- **Antagonist effect** (blocking): they occupy the receptors preventing nicotine from binding. If you smoke a cigarette during treatment, the pleasant effect is reduced or even unpleasant. The door is already "occupied".

The two molecules are similar enough to bind the same receptor, but different enough to bind it in a different way. (see script above)

### Therapeutic regimen and side effects

Everything is already explained much better than I ever could in the <a href="https://medicinali.aifa.gov.it/it/#/it/dettaglio/0000059172" aria-label="Technical data sheet of Cytisine on the Italian Medicines Agency (AIFA) website">AIFA technical data sheet for Cytisine</a>. 

Moreover, a fundamental element, it has no known pharmacological interactions.

### The numbers

The data are quite solid. The West et al. study (NEJM 2011) showed that cytisine more than tripled the chances of success compared to placebo at 12 months:

<div style="max-width: 500px; margin: 2rem auto;">
  <svg viewBox="0 0 400 240" width="100%" style="font-family: inherit;" role="img" aria-label="Bar chart showing the success rate for quitting smoking at 12 months: Placebo 2.4%, Cytisine 8.4%">
    <g aria-hidden="true">
      <line x1="80" y1="20" x2="80" y2="190" stroke="var(--blog-border, #d1d5db)" stroke-width="0.5"/>
      <text x="72" y="190" text-anchor="end" style="font-size:11px; fill:var(--blog-text-muted, #6b7280)">0</text>
      <line x1="78" y1="170" x2="80" y2="170" stroke="var(--blog-border, #d1d5db)" stroke-width="0.5"/>
      <text x="72" y="173" text-anchor="end" style="font-size:11px; fill:var(--blog-text-muted, #6b7280)">2</text>
      <line x1="78" y1="150" x2="80" y2="150" stroke="var(--blog-border, #d1d5db)" stroke-width="0.5"/>
      <text x="72" y="153" text-anchor="end" style="font-size:11px; fill:var(--blog-text-muted, #6b7280)">4</text>
      <line x1="78" y1="130" x2="80" y2="130" stroke="var(--blog-border, #d1d5db)" stroke-width="0.5"/>
      <text x="72" y="133" text-anchor="end" style="font-size:11px; fill:var(--blog-text-muted, #6b7280)">6</text>
      <line x1="78" y1="110" x2="80" y2="110" stroke="var(--blog-border, #d1d5db)" stroke-width="0.5"/>
      <text x="72" y="113" text-anchor="end" style="font-size:11px; fill:var(--blog-text-muted, #6b7280)">8</text>
      <line x1="78" y1="90" x2="80" y2="90" stroke="var(--blog-border, #d1d5db)" stroke-width="0.5"/>
      <text x="72" y="93" text-anchor="end" style="font-size:11px; fill:var(--blog-text-muted, #6b7280)">10</text>
      <line x1="80" y1="170" x2="350" y2="170" stroke="var(--blog-border, #d1d5db)" stroke-width="0.3" stroke-dasharray="3 3"/>
      <line x1="80" y1="150" x2="350" y2="150" stroke="var(--blog-border, #d1d5db)" stroke-width="0.3" stroke-dasharray="3 3"/>
      <line x1="80" y1="130" x2="350" y2="130" stroke="var(--blog-border, #d1d5db)" stroke-width="0.3" stroke-dasharray="3 3"/>
      <line x1="80" y1="110" x2="350" y2="110" stroke="var(--blog-border, #d1d5db)" stroke-width="0.3" stroke-dasharray="3 3"/>
      <line x1="80" y1="90" x2="350" y2="90" stroke="var(--blog-border, #d1d5db)" stroke-width="0.3" stroke-dasharray="3 3"/>
      <line x1="80" y1="190" x2="350" y2="190" stroke="var(--blog-border, #d1d5db)" stroke-width="0.5"/>
      <rect x="120" y="166" width="70" height="24" rx="3" fill="rgba(255, 99, 132, 0.6)" stroke="rgba(255, 99, 132, 1)" stroke-width="0.8"/>
      <text x="155" y="160" text-anchor="middle" style="font-size:12px; font-weight:600; fill:var(--blog-text, #3d3d3a)">2.4%</text>
      <text x="155" y="208" text-anchor="middle" style="font-size:12px; fill:var(--blog-text, #3d3d3a)">Placebo</text>
      <rect x="230" y="106" width="70" height="84" rx="3" fill="rgba(90, 125, 124, 0.6)" stroke="rgba(90, 125, 124, 1)" stroke-width="0.8"/>
      <text x="265" y="100" text-anchor="middle" style="font-size:12px; font-weight:600; fill:var(--blog-text, #3d3d3a)">8.4%</text>
      <text x="265" y="208" text-anchor="middle" style="font-size:12px; fill:var(--blog-text, #3d3d3a)">Cytisine</text>
      <text x="15" y="120" text-anchor="middle" transform="rotate(-90, 15, 120)" style="font-size:10px; fill:var(--blog-text-muted, #6b7280)">Success Rate (%)</text>
    </g>
  </svg>
</div>

## Interactive therapy comparison

Select two drugs to compare their efficacy, duration, and cost:

<div id="cmp-widget" style="max-width: 750px; margin: 1.5rem auto; padding: 1.5rem; background: var(--card-bg, #ffffff); border: 1px solid var(--border-color, #e5e5e5); border-radius: 8px; box-shadow: var(--card-shadow, 0 2px 8px rgba(0,0,0,0.04)); color: var(--text-color, #222222);">
  <div style="display: flex; justify-content: center; align-items: center; gap: 1rem; flex-wrap: wrap; margin-bottom: 1.5rem;">
    <select id="drug1" onchange="cmpUpdate()" aria-label="Select the first drug to compare" style="padding: 0.5rem 1rem; border: 1px solid var(--border-color, #e5e5e5); border-radius: 6px; background: var(--bg-color, #fafafa); color: var(--text-color, #222222); font-family: inherit;">
      <option value="citisina">Cytisine</option>
      <option value="vareniclina">Varenicline</option>
      <option value="nrt">Combined NRT</option>
      <option value="bupropione">Bupropion</option>
    </select>
    <strong style="font-size: 1.2rem;" aria-hidden="true">VS</strong>
    <select id="drug2" onchange="cmpUpdate()" aria-label="Select the second drug to compare" style="padding: 0.5rem 1rem; border: 1px solid var(--border-color, #e5e5e5); border-radius: 6px; background: var(--bg-color, #fafafa); color: var(--text-color, #222222); font-family: inherit;">
      <option value="citisina">Cytisine</option>
      <option value="vareniclina">Varenicline</option>
      <option value="nrt" selected>Combined NRT</option>
      <option value="bupropione">Bupropion</option>
    </select>
  </div>
  <div style="max-width: 620px; margin: 0 auto;">
    <svg id="cmp-svg" viewBox="0 0 580 310" width="100%" style="font-family: inherit;" role="img" aria-label="Dynamic comparison bar chart between the two selected therapies, showing: Efficacy, Duration, Cost, and Dropout rate."></svg>
  </div>
  <div style="display:flex; flex-wrap:wrap; justify-content:center; gap:16px; margin-top:10px; font-size:12px;" aria-hidden="true">
    <span><span style="display:inline-block;width:12px;height:12px;border-radius:2px;background:rgba(90,125,124,0.7);vertical-align:middle;margin-right:4px;"></span>Efficacy (%)</span>
    <span><span style="display:inline-block;width:12px;height:12px;border-radius:2px;background:rgba(23,107,135,0.7);vertical-align:middle;margin-right:4px;"></span>Duration (days)</span>
    <span><span style="display:inline-block;width:12px;height:12px;border-radius:2px;background:rgba(244,162,97,0.7);vertical-align:middle;margin-right:4px;"></span>Cost (€)</span>
    <span><span style="display:inline-block;width:12px;height:12px;border-radius:2px;background:rgba(227,62,62,0.7);vertical-align:middle;margin-right:4px;"></span>Drop-out side eff. (%)</span>
  </div>
  <div id="cmp-text" aria-live="polite" style="margin-top: 1rem; color: var(--text-muted, #6b6b6b); font-size: 0.95rem; line-height: 1.6;"></div>
</div>

<script>
(function(){
  var DD = {
    citisina:    { name:"Cytisine",      efficacy:16, duration:25, cost:50,  dropout:5,  desc:"<strong>Cytisine:</strong> High efficacy, very short treatment (25 days) and extremely low cost. Excellent tolerability profile: very few dropouts." },
    vareniclina: { name:"Varenicline",   efficacy:18, duration:84, cost:300, dropout:14, desc:"<strong>Varenicline:</strong> Very high efficacy (theoretical gold standard), but long treatment and higher cost. High dropout rate due to nausea and vivid dreams." },
    nrt:         { name:"Combined NRT", efficacy:12, duration:70, cost:250, dropout:6,  desc:"<strong>Combined NRT:</strong> Patch + gums/spray. Moderate efficacy, lower than cytisine. Good tolerability but long treatment and high cost." },
    bupropione:  { name:"Bupropion",    efficacy:9,  duration:63, cost:100, dropout:11, desc:"<strong>Bupropion:</strong> Lower efficacy. Significant dropout rate due to systemic side effects and specific contraindications (seizure risk)." }
  };
  var COLORS  = ['rgba(90,125,124,0.7)', 'rgba(23,107,135,0.7)', 'rgba(244,162,97,0.7)', 'rgba(227,62,62,0.7)'];
  var STROKES = ['rgba(90,125,124,1)',   'rgba(23,107,135,1)',   'rgba(244,162,97,1)',   'rgba(227,62,62,1)'];
  var LABELS  = ['Efficacy', 'Duration', 'Cost', 'Drop-out'];
  var NS = 'http://www.w3.org/2000/svg';

  function el(tag, attrs) {
    var e = document.createElementNS(NS, tag);
    for (var k in attrs) e.setAttribute(k, attrs[k]);
    return e;
  }

  function txt(x, y, content, extra) {
    var t = el('text', Object.assign({x:x, y:y, 'text-anchor':'middle'}, extra || {}));
    t.textContent = content;
    t.style.fontFamily = 'inherit';
    return t;
  }

  window.cmpUpdate = function() {
    var d1 = DD[document.getElementById('drug1').value];
    var d2 = DD[document.getElementById('drug2').value];
    var svg = document.getElementById('cmp-svg');
    svg.innerHTML = '<g aria-hidden="true"></g>';
    var group = svg.firstChild;

    var vals1 = [d1.efficacy, d1.duration, d1.cost, d1.dropout];
    var vals2 = [d2.efficacy, d2.duration, d2.cost, d2.dropout];
    var maxVal = Math.max.apply(null, vals1.concat(vals2));
    var ceil = Math.ceil(maxVal / 50) * 50;
    if (ceil < 20) ceil = 20;
    var chartH = 200, chartY = 30, axisX = 60, chartW = 480;

    for (var g = 0; g <= 4; g++) {
      var gy = chartY + chartH - (chartH * g / 4);
      var gv = Math.round(ceil * g / 4);
      group.appendChild(el('line', {x1:axisX, y1:gy, x2:axisX+chartW, y2:gy, stroke:'var(--blog-border, #d1d5db)', 'stroke-width':'0.3', 'stroke-dasharray': g===0?'':'3 3'}));
      group.appendChild(txt(axisX - 8, gy + 4, gv, {style:'font-size:10px;fill:var(--blog-text-muted,#6b7280);font-family:inherit', 'text-anchor':'end'}));
    }

    var groupW = chartW / 4;
    var barW = 26;
    var gap = 5;

    for (var m = 0; m < 4; m++) {
      var gx = axisX + m * groupW + groupW / 2;
      var v1 = vals1[m], v2 = vals2[m];
      var h1 = (v1 / ceil) * chartH;
      var h2 = (v2 / ceil) * chartH;

      var bx1 = gx - barW - gap/2;
      group.appendChild(el('rect', {x:bx1, y:chartY+chartH-h1, width:barW, height:Math.max(h1,1), rx:'3', fill:COLORS[m], stroke:STROKES[m], 'stroke-width':'0.8'}));
      var label1 = (m===0||m===3) ? v1+'%' : m===2 ? '\u20AC'+v1 : String(v1);
      group.appendChild(txt(bx1 + barW/2, chartY+chartH-h1-6, label1, {style:'font-size:10px;font-weight:600;fill:var(--blog-text,#3d3d3a);font-family:inherit'}));

      var bx2 = gx + gap/2;
      group.appendChild(el('rect', {x:bx2, y:chartY+chartH-h2, width:barW, height:Math.max(h2,1), rx:'3', fill:COLORS[m], stroke:STROKES[m], 'stroke-width':'0.8', opacity:'0.55'}));
      var label2 = (m===0||m===3) ? v2+'%' : m===2 ? '\u20AC'+v2 : String(v2);
      group.appendChild(txt(bx2 + barW/2, chartY+chartH-h2-6, label2, {style:'font-size:10px;font-weight:600;fill:var(--blog-text,#3d3d3a);font-family:inherit'}));

      group.appendChild(txt(gx, chartY+chartH+16, LABELS[m], {style:'font-size:11px;fill:var(--blog-text-muted,#6b7280);font-family:inherit'}));
    }

    var legY = chartY + chartH + 38;
    group.appendChild(el('rect', {x:axisX+60, y:legY-8, width:10, height:10, rx:'2', fill:'var(--blog-text,#3d3d3a)', opacity:'1'}));
    group.appendChild(txt(axisX+76, legY, d1.name, {style:'font-size:11px;fill:var(--blog-text,#3d3d3a);font-family:inherit', 'text-anchor':'start'}));
    group.appendChild(el('rect', {x:axisX+260, y:legY-8, width:10, height:10, rx:'2', fill:'var(--blog-text,#3d3d3a)', opacity:'0.55'}));
    group.appendChild(txt(axisX+276, legY, d2.name, {style:'font-size:11px;fill:var(--blog-text,#3d3d3a);font-family:inherit', 'text-anchor':'start'}));

    document.getElementById('cmp-text').innerHTML = '<p>' + d1.desc + '</p><p style="margin-top:0.5rem;">' + d2.desc + '</p>';
  };

  document.addEventListener('DOMContentLoaded', cmpUpdate);
})();
</script>

*By playing with the script, you can notice the difference in timing between Varenicline and Cytisine. Cytisine has a short half-life and a less "invasive" receptor binding, allowing rapid desensitization of nicotinic receptors without saturating the central nervous system.*

## The situation in Italy (2026 update)

In December 2025, the <a href="https://www.aifa.gov.it/" aria-label="Official Website of the Italian Medicines Agency">AIFA approved the reimbursement</a> of Recigar® (industrial cytisine) by the NHS (SSN). From March 2026, the first cycle is free for those undergoing a structured program at an anti-smoking center, complete with a therapeutic plan and behavioral support. For everyone else, a cycle costs about €90 — still a tenth of the price of varenicline.

Cytisine is also available as a **compounded preparation** (prepared by the pharmacist in the pharmacy's lab) at about half the price — something I know quite well for obvious reasons — or as Defucitan®, another industrial cytisine-based drug available since 2023.

## Non-pharmacological things that make a difference

Suggested by the NHS. They might seem trivial, but they shouldn't be underestimated and must be done exactly as prescribed (yes, even taking pen and paper and writing things down):

1. Make a list of the reasons why you are quitting smoking.
2. Tell people you are quitting.
3. If you have already managed to quit for some time before, remember what worked.
4. Use smoking cessation aids.
5. Have a plan for what to do when you are tempted.
6. Make a list of what makes you want to smoke, and avoid it.
7. Keep the addiction in check by keeping yourself busy.
8. Exercise to ward off cravings.

All the drugs mentioned are available by medical prescription only. Your doctor will indicate how to use them in your case and give you all the necessary instructions.

Addiction, whatever it may be, whether to Nicotine, Cannabis, Cocaine, Heroin or even emotional addiction, is a nasty beast. Seeking all the help possible is not a sign of weakness but, imho, a great demonstration of strength and intelligence.

*I have been preparing cytisine in my compounding lab for years — it's one of those things you talk about with the patient and realize they've never heard of it. Now maybe something changes.*

## Sources

- West, R., et al. (2011). <a href="https://www.nejm.org/doi/full/10.1056/NEJMoa1102035" aria-label="External study from the New England Journal of Medicine on Cytisine efficacy">Placebo-Controlled Trial of Cytisine for Smoking Cessation.</a> *New England Journal of Medicine*, 365(13), 1193–1200.
- Cahill, K., et al. (2013). <a href="https://www.cochranelibrary.com/cdsr/doi/10.1002/14651858.CD009329.pub2/full" aria-label="Cochrane Library study on pharmacological interventions for smoking cessation">Pharmacological interventions for smoking cessation.</a> *Cochrane Database of Systematic Reviews*, (5).
- Public Health England. (2015). <a href="https://www.gov.uk/government/publications/e-cigarettes-an-evidence-update" aria-label="Public Health England document on e-cigarettes">E-cigarettes: an evidence update.</a>
- <a href="https://www.iss.it/fumo" aria-label="Official guidelines on smoking by the Italian National Institute of Health">ISS guidelines on smoking.</a>