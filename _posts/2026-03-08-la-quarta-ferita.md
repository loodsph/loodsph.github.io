---
title: "La quarta ferita narcisistica"
date: 2026-03-08
layout: post
tags: [AI, reti neurali, filosofia, complessità]
description: "Da Galileo all'AI"
pixel_icon: "neural_network.png"
smooth_image: true
---

In principio fu Galileo, a spiegarci che l'universo non ruota intorno a noi. Poi venne Darwin, a spiegarci che non siamo creature speciali, a immagine e somiglianza di un essere superiore — abbiamo solo casualmente preso un ramo evolutivo diverso. Poi toccò a Freud spiegarci che abbiamo un inconscio molto ingombrante e che non siamo padroni a casa nostra.

Ora tocca all'AI spiegarci che la capacità di pensare non ha nulla di mistico, di speciale, di insondabile. L'idea che avanzate capacità cognitive si possano raggiungere solo tramite una struttura imperscrutabile e incredibilmente complessa appare ormai datata. Una rudimentale e parziale riproduzione del cervello umano ha già superato il test di Turing. Non solo non siamo più in grado di capire se chi abbiamo di fronte sia un umano o una macchina, ma questa è più in grado di noi di risolvere il 98% dei problemi.

Tre ferite narcisistiche — cosmologica, biologica, psicologica — e ora una quarta: **quella cognitiva**.

---
<br>
Ma se dico "una rete neurale impara", cosa sta succedendo davvero? Per rispondere dovremmo prima definire cosa significhi imparare o pensare. Un compito decisamente oltre la mia portata.
Però vorrei almeno capire che cosa ci sia a livello base, pratico, di una AI.
Da quanto ho capito nient'altro che moltiplicazioni, somme, e una regola per aggiustarsi. Questa semplicità è incredibilmente affascinante alla luce di tutto quello che abbiamo visto prima e dei risultati prodotti.

## Simulazione

Una rete neurale che impara a sparare un proiettile verso un bersaglio.

<style>
    #nn-sim {
        font-family: 'Inter', 'Segoe UI', sans-serif;
        background-color: #121212;
        color: #e0e0e0;
        display: flex;
        flex-direction: column;
        align-items: center;
        padding: 30px 0;
        border-radius: 12px;
        margin: 30px 0;
    }
    #nn-sim * { box-sizing: border-box; }

    #nn-sim .nn-main-container {
        display: flex;
        background: #1e1e1e;
        border-radius: 12px;
        box-shadow: 0 20px 50px rgba(0,0,0,0.5);
        overflow: hidden;
        margin-bottom: 25px;
        border: 1px solid #333;
    }
    #nn-sim .nn-panel {
        position: relative;
        width: 400px;
        height: 400px;
        background-color: #1e1e1e;
        background-image:
            linear-gradient(#2a2a2a 1px, transparent 1px),
            linear-gradient(90deg, #2a2a2a 1px, transparent 1px);
        background-size: 10px 10px;
    }
    #nn-sim .nn-panel-left {
        border-right: 1px solid #333;
        background-color: #181818;
    }
    #nn-sim canvas { display: block; width: 100%; height: 100%; }

    #nn-sim .nn-loss-display {
        position: absolute; top: 20px; right: 20px;
        font-family: 'Consolas', 'Monaco', monospace;
        font-size: 16px; font-weight: 600; color: #4fc3f7;
        background: rgba(30,30,30,0.9); padding: 4px 8px;
        border-radius: 4px; border: 1px solid #444;
        box-shadow: 0 2px 5px rgba(0,0,0,0.3); line-height: 1.5;
    }
    #nn-sim .nn-epoch-display {
        position: absolute; top: 20px; left: 20px;
        font-family: 'Consolas', 'Monaco', monospace;
        font-size: 14px; font-weight: 600; color: #aaa;
        background: rgba(30,30,30,0.9); padding: 4px 8px;
        border-radius: 4px; border: 1px solid #444;
    }
    #nn-sim .nn-status-indicator {
        position: absolute; bottom: 15px; right: 15px;
        font-size: 13px; font-weight: 600; text-transform: uppercase;
        letter-spacing: 0.5px; padding: 4px 10px; border-radius: 20px;
        background: rgba(30,30,30,0.95); color: #eee;
        box-shadow: 0 2px 8px rgba(0,0,0,0.4); border: 1px solid #333;
    }
    #nn-sim .nn-method-badge {
        position: absolute; top: 15px; left: 15px;
        font-size: 10px; font-weight: 700; text-transform: uppercase;
        letter-spacing: 1px; padding: 3px 8px; border-radius: 4px;
        transition: all 0.3s; z-index: 2;
    }
    #nn-sim .nn-method-badge.backprop {
        background: rgba(76,175,80,0.15); color: #66bb6a; border: 1px solid #66bb6a;
    }
    #nn-sim .nn-method-badge.evolution {
        background: rgba(255,152,0,0.15); color: #ffa726; border: 1px solid #ffa726;
    }

    #nn-sim .nn-controls {
        background: #1e1e1e; padding: 25px; border-radius: 12px;
        box-shadow: 0 4px 20px rgba(0,0,0,0.2);
        display: flex; flex-direction: column; gap: 20px;
        align-items: center; max-width: 850px; width: 90%;
        border: 1px solid #333;
    }
    #nn-sim .nn-toggle-row {
        display: flex; align-items: center; gap: 14px;
        padding-bottom: 18px; border-bottom: 1px solid #333;
        width: 100%; justify-content: center; flex-wrap: wrap;
    }
    #nn-sim .nn-toggle-group { display: flex; align-items: center; gap: 10px; }
    #nn-sim .nn-toggle-separator { width: 1px; height: 28px; background: #444; margin: 0 10px; }

    #nn-sim .nn-toggle-label {
        font-size: 13px; font-weight: 600; text-transform: uppercase;
        letter-spacing: 0.5px; transition: color 0.3s; cursor: pointer; user-select: none;
    }
    #nn-sim .nn-toggle-label.active-evo { color: #ffa726; }
    #nn-sim .nn-toggle-label.active-bp { color: #66bb6a; }
    #nn-sim .nn-toggle-label.active-batch { color: #ce93d8; }
    #nn-sim .nn-toggle-label.inactive { color: #555; }

    #nn-sim .nn-toggle-switch {
        position: relative; width: 52px; height: 28px; cursor: pointer; display: inline-block;
    }
    #nn-sim .nn-toggle-switch input { opacity: 0; width: 0; height: 0; position: absolute; }
    #nn-sim .nn-toggle-track {
        position: absolute; inset: 0; border-radius: 14px;
        background: #333; transition: background 0.3s; border: 1px solid #555;
    }
    #nn-sim .nn-toggle-switch input:checked + .nn-toggle-track {
        background: rgba(76,175,80,0.3); border-color: #66bb6a;
    }
    #nn-sim .nn-toggle-switch input:not(:checked) + .nn-toggle-track {
        background: rgba(255,152,0,0.2); border-color: #ffa726;
    }
    #nn-sim .nn-toggle-switch.batch-toggle input:checked + .nn-toggle-track {
        background: rgba(206,147,216,0.25); border-color: #ce93d8;
    }
    #nn-sim .nn-toggle-switch.batch-toggle input:not(:checked) + .nn-toggle-track {
        background: #2a2a2a; border-color: #555;
    }
    #nn-sim .nn-toggle-thumb {
        position: absolute; top: 3px; left: 3px; width: 22px; height: 22px;
        border-radius: 50%; background: #ffa726; transition: all 0.3s;
        box-shadow: 0 0 8px rgba(255,152,0,0.4);
    }
    #nn-sim .nn-toggle-switch input:checked ~ .nn-toggle-thumb {
        left: 27px; background: #66bb6a; box-shadow: 0 0 8px rgba(76,175,80,0.5);
    }
    #nn-sim .nn-toggle-switch.batch-toggle .nn-toggle-thumb { background: #555; box-shadow: none; }
    #nn-sim .nn-toggle-switch.batch-toggle input:checked ~ .nn-toggle-thumb {
        left: 27px; background: #ce93d8; box-shadow: 0 0 8px rgba(206,147,216,0.5);
    }

    #nn-sim .nn-sliders-row {
        display: flex; gap: 30px; width: 100%; justify-content: center;
        padding-bottom: 20px; border-bottom: 1px solid #333; flex-wrap: wrap;
    }
    #nn-sim .nn-speed-control {
        display: flex; flex-direction: column; align-items: center;
        gap: 8px; flex: 1; max-width: 250px; min-width: 150px;
    }
    #nn-sim .nn-speed-label {
        font-size: 11px; font-weight: 600; color: #aaa;
        text-transform: uppercase; letter-spacing: 1px;
    }
    #nn-sim input[type="range"] {
        -webkit-appearance: none; width: 100%; height: 6px;
        border-radius: 5px; background: #333; outline: none;
    }
    #nn-sim input[type="range"]::-webkit-slider-thumb {
        -webkit-appearance: none; width: 20px; height: 20px; border-radius: 50%;
        background: #4fc3f7; cursor: pointer;
        box-shadow: 0 0 10px rgba(79,195,247,0.4); transition: transform 0.1s;
    }
    #nn-sim input[type="range"]::-webkit-slider-thumb:hover { transform: scale(1.1); }
    #nn-sim .nn-hideable { transition: opacity 0.3s; }
    #nn-sim .nn-hideable.hidden { opacity: 0.25; pointer-events: none; }

    #nn-sim .nn-structure-editor {
        display: flex; align-items: flex-start; gap: 12px;
        overflow-x: auto; padding: 10px 5px; width: 100%; justify-content: center;
    }
    #nn-sim .nn-layer-column {
        display: flex; flex-direction: column; align-items: center;
        background: #252525; border: 1px solid #333; border-radius: 8px;
        padding: 12px; min-width: 65px; box-shadow: 0 2px 8px rgba(0,0,0,0.2);
        transition: transform 0.2s;
    }
    #nn-sim .nn-layer-column:hover { transform: translateY(-2px); box-shadow: 0 5px 15px rgba(0,0,0,0.3); border-color: #555; }
    #nn-sim .nn-layer-column.input-layer { border-top: 4px solid #32CD32; }
    #nn-sim .nn-layer-column.hidden-layer { border-top: 4px solid #FFD700; }
    #nn-sim .nn-layer-column.output-layer { border-top: 4px solid #a0a0a0; }
    #nn-sim .nn-layer-title {
        font-size: 9px; text-transform: uppercase; font-weight: 700;
        margin-bottom: 8px; color: #888; letter-spacing: 0.5px;
    }
    #nn-sim .nn-neuron-count { font-size: 22px; font-weight: 800; color: #eee; margin: 8px 0; }
    #nn-sim .nn-btn-circle {
        width: 26px; height: 26px; border-radius: 50%; border: none;
        background: #333; color: #ccc; font-weight: bold; cursor: pointer;
        display: flex; align-items: center; justify-content: center;
        margin: 3px 0; transition: all 0.2s; font-size: 14px; line-height: 1;
    }
    #nn-sim .nn-btn-circle:hover { background: #eee; color: #111; }
    #nn-sim .nn-btn-circle:disabled { opacity: 0.3; cursor: not-allowed; background: #222; color: #555; }
    #nn-sim .nn-btn-remove-layer {
        margin-top: 10px; background: transparent; color: #ff6b6b;
        font-size: 14px; padding: 4px; border-radius: 4px;
        border: 1px solid transparent; cursor: pointer; transition: all 0.2s;
    }
    #nn-sim .nn-btn-remove-layer:hover { background: rgba(255,107,107,0.1); border-color: #ff6b6b; }
    #nn-sim .nn-btn-add-layer {
        height: 110px; width: 45px; border: 2px dashed #444;
        background: transparent; color: #444; font-size: 28px;
        cursor: pointer; border-radius: 8px; margin-top: 12px;
        display: flex; align-items: center; justify-content: center;
        transition: all 0.2s;
    }
    #nn-sim .nn-btn-add-layer:hover { border-color: #666; color: #666; background: #252525; transform: scale(1.02); }
    #nn-sim .nn-btn-reset {
        padding: 8px 20px; border: 1px solid #ff6b6b; background: transparent;
        color: #ff6b6b; font-size: 13px; font-weight: 600; letter-spacing: 0.5px;
        text-transform: uppercase; border-radius: 6px; cursor: pointer; transition: all 0.2s;
    }
    #nn-sim .nn-btn-reset:hover { background: rgba(255,107,107,0.15); transform: scale(1.03); }

    @media (max-width: 860px) {
        #nn-sim .nn-main-container { flex-direction: column; width: 100%; }
        #nn-sim .nn-panel { width: 100%; height: auto; aspect-ratio: 1; }
        #nn-sim .nn-panel-left { border-right: none; border-bottom: 1px solid #333; }
        #nn-sim canvas { width: 100%; height: 100%; }
        #nn-sim .nn-controls { width: 100%; }
    }
</style>
<div id="nn-sim">
    <div class="nn-main-container">
        <div class="nn-panel nn-panel-left">
            <div id="nnMethodBadge" class="nn-method-badge backprop">Backprop</div>
            <canvas id="nnNetworkCanvas" width="400" height="400"></canvas>
        </div>
        <div class="nn-panel">
            <div id="nnLossText" class="nn-loss-display">ERROR: ...</div>
            <div id="nnEpochText" class="nn-epoch-display">epoch: 0</div>
            <div id="nnStatusText" class="nn-status-indicator">In Apprendimento...</div>
            <canvas id="nnSimCanvas" width="400" height="400"></canvas>
        </div>
    </div>
    <div class="nn-controls">
        <div class="nn-toggle-row">
            <div class="nn-toggle-group">
                <span id="nnLabelEvo" class="nn-toggle-label inactive">Evoluzione</span>
                <label class="nn-toggle-switch">
                    <input type="checkbox" id="nnMethodToggle" checked>
                    <div class="nn-toggle-track"></div>
                    <div class="nn-toggle-thumb"></div>
                </label>
                <span id="nnLabelBp" class="nn-toggle-label active-bp">Backprop</span>
            </div>
            <div class="nn-toggle-separator"></div>
            <div class="nn-toggle-group">
                <span id="nnLabelSingle" class="nn-toggle-label inactive">Single</span>
                <label class="nn-toggle-switch batch-toggle">
                    <input type="checkbox" id="nnBatchToggle">
                    <div class="nn-toggle-track"></div>
                    <div class="nn-toggle-thumb"></div>
                </label>
                <span id="nnLabelBatch" class="nn-toggle-label inactive">Mini-Batch</span>
            </div>
        </div>
        <div class="nn-sliders-row">
            <div class="nn-speed-control">
                <span class="nn-speed-label">Velocità: <span id="nnSpeedVal" style="color:#4fc3f7">5</span>x</span>
                <input type="range" id="nnSpeedRange" min="0.25" max="200" step="0.25" value="5">
            </div>
            <div class="nn-speed-control nn-hideable" id="nnLrControlBox">
                <span class="nn-speed-label">Learning Rate: <span id="nnLrVal" style="color:#4fc3f7">0.005</span></span>
                <input type="range" id="nnLrRange" min="-4" max="-0.5" step="0.1" value="-2.3">
            </div>
            <div class="nn-speed-control nn-hideable hidden" id="nnBatchSizeBox">
                <span class="nn-speed-label">Batch Size: <span id="nnBatchVal" style="color:#ce93d8">16</span></span>
                <input type="range" id="nnBatchRange" min="4" max="64" step="4" value="16">
            </div>
        </div>
        <div id="nnStructureEditor" class="nn-structure-editor"></div>
        <button class="nn-btn-reset" id="nnResetBtn">&#x27F2; Reset</button>
    </div>
</div>
<script>
(function() {
    const WIDTH = 400, HEIGHT = 400;
    const CANNON_X = 30, CANNON_Y = HEIGHT - 30;
    const LOSS_THRESHOLD = 5.0, GRAD_CLIP = 5.0, EPS = 1e-4;
    const BATCH_X_MIN = 80, BATCH_X_MAX = 380, BATCH_Y_MIN = 30, BATCH_Y_MAX = 320;

    class NeuralNetwork {
        constructor(layerSizes) {
            this.layerSizes = layerSizes;
            this.weights = []; this.biases = [];
            this.nodeValues = []; this.activations = []; this.preActivations = [];
            for (let i = 0; i < layerSizes.length - 1; i++) {
                const fi = layerSizes[i], fo = layerSizes[i+1];
                const s = Math.sqrt(2.0 / (fi + fo));
                this.weights.push(new Array(fi*fo).fill(0).map(() => (Math.random()*2-1)*s));
                this.biases.push(new Array(fo).fill(0));
            }
        }
        predict(inputs) {
            this.activations = [[...inputs]]; this.preActivations = [null];
            let current = [...inputs];
            for (let i = 0; i < this.weights.length; i++) {
                const inS = this.layerSizes[i], outS = this.layerSizes[i+1];
                const W = this.weights[i], B = this.biases[i];
                const pre = new Array(outS), post = new Array(outS);
                for (let o = 0; o < outS; o++) {
                    let sum = B[o];
                    for (let n = 0; n < inS; n++) sum += current[n] * W[n*outS+o];
                    pre[o] = sum;
                    post[o] = (i === this.weights.length-1) ? sum : Math.tanh(sum);
                }
                this.preActivations.push(pre); this.activations.push(post); current = post;
            }
            this.nodeValues = this.activations; return current;
        }
        backward(outputGradients, lr) {
            let delta = [...outputGradients];
            for (let i = this.weights.length-1; i >= 0; i--) {
                const inS = this.layerSizes[i], outS = this.layerSizes[i+1];
                const prevAct = this.activations[i], W = this.weights[i];
                const nextDelta = new Array(inS).fill(0);
                for (let n = 0; n < inS; n++) {
                    for (let o = 0; o < outS; o++) nextDelta[n] += delta[o] * W[n*outS+o];
                    if (i > 0) { const a = this.activations[i][n]; nextDelta[n] *= (1-a*a); }
                }
                for (let o = 0; o < outS; o++) {
                    this.biases[i][o] -= lr * delta[o];
                    for (let n = 0; n < inS; n++) this.weights[i][n*outS+o] -= lr * delta[o] * prevAct[n];
                }
                delta = nextDelta;
            }
        }
        clone() {
            const c = new NeuralNetwork(this.layerSizes);
            c.weights = this.weights.map(l => [...l]); c.biases = this.biases.map(l => [...l]); return c;
        }
        mutate(rate) {
            for (let i = 0; i < this.weights.length; i++) {
                for (let j = 0; j < this.weights[i].length; j++) if (Math.random()<0.1) this.weights[i][j] += (Math.random()*2-1)*rate;
                for (let j = 0; j < this.biases[i].length; j++) if (Math.random()<0.1) this.biases[i][j] += (Math.random()*2-1)*rate;
            }
        }
    }

    function sigmoid(x) { return 1.0/(1.0+Math.exp(-x)); }
    function mapOutputsToPhysics(raw) {
        return { angle: sigmoid(raw[0]||0)*1.45+0.05, force: sigmoid(raw[1]||0)*40+5 };
    }
    function getInputs(tx, ty, size) {
        const inp = new Array(size).fill(0);
        if (size>0) inp[0]=(tx-CANNON_X)/200; if (size>1) inp[1]=-(ty-CANNON_Y)/200; return inp;
    }
    function calcTraj(angle, force, tx, ty) {
        let sx=CANNON_X,sy=CANNON_Y,vx=Math.cos(angle)*force,vy=-Math.sin(angle)*force,minD=Infinity;
        const path=[];
        for (let t=0;t<180;t++) { sx+=vx;sy+=vy;vy+=0.5; path.push({x:sx,y:sy}); const d=Math.hypot(sx-tx,sy-ty); if(d<minD)minD=d; if(sy>HEIGHT+50||sx>WIDTH+50)break; }
        return {path,minDist:minD};
    }
    function lossFor(raw,tx,ty) { const p=mapOutputsToPhysics(raw); return calcTraj(p.angle,p.force,tx,ty).minDist**2; }
    function outGrads(raw,tx,ty) {
        const g=[];
        for (let i=0;i<raw.length;i++) { const pl=[...raw],mn=[...raw]; pl[i]+=EPS;mn[i]-=EPS; g.push(Math.max(-GRAD_CLIP,Math.min(GRAD_CLIP,(lossFor(pl,tx,ty)-lossFor(mn,tx,ty))/(2*EPS)))); }
        return g;
    }
    function genBatch(n) {
        const t=[]; for(let i=0;i<n;i++) t.push({x:BATCH_X_MIN+Math.random()*(BATCH_X_MAX-BATCH_X_MIN),y:BATCH_Y_MIN+Math.random()*(BATCH_Y_MAX-BATCH_Y_MIN)}); return t;
    }

    const netCanvas=document.getElementById('nnNetworkCanvas'), netCtx=netCanvas.getContext('2d');
    const simCanvas=document.getElementById('nnSimCanvas'), simCtx=simCanvas.getContext('2d');
    const lossText=document.getElementById('nnLossText'), epochText=document.getElementById('nnEpochText');
    const statusText=document.getElementById('nnStatusText'), methodBadge=document.getElementById('nnMethodBadge');
    const speedInput=document.getElementById('nnSpeedRange'), speedValD=document.getElementById('nnSpeedVal');
    const lrInput=document.getElementById('nnLrRange'), lrValD=document.getElementById('nnLrVal');
    const lrBox=document.getElementById('nnLrControlBox');
    const bsInput=document.getElementById('nnBatchRange'), bsValD=document.getElementById('nnBatchVal');
    const bsBox=document.getElementById('nnBatchSizeBox');
    const mToggle=document.getElementById('nnMethodToggle'), bToggle=document.getElementById('nnBatchToggle');
    const lEvo=document.getElementById('nnLabelEvo'), lBp=document.getElementById('nnLabelBp');
    const lSingle=document.getElementById('nnLabelSingle'), lBatch=document.getElementById('nnLabelBatch');
    const sEditor=document.getElementById('nnStructureEditor');

    let brain,bestBrain,bestError,target={x:300,y:150};
    let curLoss=Infinity,batchLoss=Infinity,isTraining=true;
    let speed=5,spdAcc=0,lr=0.005,epoch=0;
    let useBP=true,useBatch=false,batchSize=16,batchTargets=[];
    let topo=[2,4,4,2];

    speedInput.addEventListener('input',e=>{speed=parseFloat(e.target.value);speedValD.innerText=speed;});
    lrInput.addEventListener('input',e=>{lr=Math.pow(10,parseFloat(e.target.value));lrValD.innerText=lr.toPrecision(3);});
    bsInput.addEventListener('input',e=>{batchSize=parseInt(e.target.value);bsValD.innerText=batchSize;});
    mToggle.addEventListener('change',e=>{useBP=e.target.checked;updateUI();resetSim();});
    bToggle.addEventListener('change',e=>{useBatch=e.target.checked;updateUI();resetSim();});
    document.getElementById('nnResetBtn').addEventListener('click',()=>resetSim());

    function updateUI() {
        if(useBP){lBp.className='nn-toggle-label active-bp';lEvo.className='nn-toggle-label inactive';methodBadge.className='nn-method-badge backprop';methodBadge.innerText=useBatch?'Backprop Batch':'Backprop';lrBox.classList.remove('hidden');}
        else{lBp.className='nn-toggle-label inactive';lEvo.className='nn-toggle-label active-evo';methodBadge.className='nn-method-badge evolution';methodBadge.innerText=useBatch?'Evoluzione Batch':'Evoluzione';lrBox.classList.add('hidden');}
        if(useBatch){lBatch.className='nn-toggle-label active-batch';lSingle.className='nn-toggle-label inactive';bsBox.classList.remove('hidden');}
        else{lBatch.className='nn-toggle-label inactive';lSingle.className='nn-toggle-label inactive';bsBox.classList.add('hidden');}
    }

    function renderEditor() {
        sEditor.innerHTML='';
        topo.forEach((cnt,idx)=>{
            const isIn=idx===0,isOut=idx===topo.length-1,isHid=!isIn&&!isOut;
            const col=document.createElement('div');
            col.className=`nn-layer-column ${isIn?'input-layer':isHid?'hidden-layer':'output-layer'}`;
            const t=document.createElement('div');t.className='nn-layer-title';
            t.innerText=isIn?'Input':isOut?'Output':'Hidden '+idx; col.appendChild(t);
            const bp=document.createElement('button');bp.className='nn-btn-circle';bp.innerText='+';
            bp.onclick=()=>updTopo('inc',idx); col.appendChild(bp);
            const cd=document.createElement('div');cd.className='nn-neuron-count';cd.innerText=cnt; col.appendChild(cd);
            const bm=document.createElement('button');bm.className='nn-btn-circle';bm.innerText='-';
            bm.onclick=()=>updTopo('dec',idx); if(cnt<=1)bm.disabled=true; col.appendChild(bm);
            if(isHid){const bd=document.createElement('button');bd.className='nn-btn-remove-layer';bd.innerHTML='&times;';bd.onclick=()=>updTopo('del',idx);col.appendChild(bd);}
            sEditor.appendChild(col);
        });
        const ba=document.createElement('button');ba.className='nn-btn-add-layer';ba.innerText='+';
        ba.onclick=()=>updTopo('add'); sEditor.insertBefore(ba,sEditor.lastChild);
    }

    function updTopo(a,i){
        if(a==='inc')topo[i]++;else if(a==='dec'&&topo[i]>1)topo[i]--;
        else if(a==='add')topo.splice(topo.length-1,0,3);else if(a==='del')topo.splice(i,1);
        initBrain();renderEditor();
    }
    function initBrain(){brain=new NeuralNetwork(topo);bestBrain=brain.clone();bestError=Infinity;curLoss=Infinity;batchLoss=Infinity;isTraining=true;epoch=0;spdAcc=0;batchTargets=[];}
    function resetSim(){initBrain();}

    function trainSingleBP(n){const inp=getInputs(target.x,target.y,brain.layerSizes[0]);for(let k=0;k<n;k++){const r=brain.predict(inp);brain.backward(outGrads(r,target.x,target.y),lr);epoch++;}if(n>0){const o=brain.predict(inp),p=mapOutputsToPhysics(o);curLoss=calcTraj(p.angle,p.force,target.x,target.y).minDist;}}
    function trainSingleEvo(n){const inp=getInputs(target.x,target.y,brain.layerSizes[0]);for(let k=0;k<n;k++){const m=bestBrain.clone();m.mutate(0.2);const r=m.predict(inp),p=mapOutputsToPhysics(r),d=calcTraj(p.angle,p.force,target.x,target.y).minDist;if(d<bestError){bestBrain=m;bestError=d;}epoch++;}brain=bestBrain;curLoss=bestError;}
    function trainBatchBP(n){const inS=brain.layerSizes[0];for(let k=0;k<n;k++){const batch=genBatch(batchSize);if(k===n-1)batchTargets=batch;const sLr=lr/batchSize;for(const bt of batch){const inp=getInputs(bt.x,bt.y,inS),r=brain.predict(inp);brain.backward(outGrads(r,bt.x,bt.y),sLr);}epoch++;}if(n>0){let tl=0;const tb=batchTargets.length?batchTargets:genBatch(batchSize);for(const bt of tb){const inp=getInputs(bt.x,bt.y,inS),r=brain.predict(inp),p=mapOutputsToPhysics(r);tl+=calcTraj(p.angle,p.force,bt.x,bt.y).minDist;}batchLoss=tl/tb.length;const pi=getInputs(target.x,target.y,inS),po=brain.predict(pi),pp=mapOutputsToPhysics(po);curLoss=calcTraj(pp.angle,pp.force,target.x,target.y).minDist;}}
    function trainBatchEvo(n){const inS=brain.layerSizes[0];for(let k=0;k<n;k++){const batch=genBatch(batchSize);if(k===n-1)batchTargets=batch;const m=bestBrain.clone();m.mutate(0.2);let td=0;for(const bt of batch){const inp=getInputs(bt.x,bt.y,inS),r=m.predict(inp),p=mapOutputsToPhysics(r);td+=calcTraj(p.angle,p.force,bt.x,bt.y).minDist;}if(td<bestError){bestBrain=m;bestError=td;}epoch++;}brain=bestBrain;batchLoss=bestError/batchSize;const pi=getInputs(target.x,target.y,brain.layerSizes[0]),po=brain.predict(pi),pp=mapOutputsToPhysics(po);curLoss=calcTraj(pp.angle,pp.force,target.x,target.y).minDist;}

    function drawNet(nn){
        netCtx.clearRect(0,0,WIDTH,HEIGHT);netCtx.font="bold 12px 'Segoe UI',sans-serif";netCtx.textAlign="center";netCtx.textBaseline="middle";
        netCtx.fillStyle="#aaa";if(nn.layerSizes[0]>0)netCtx.fillText("X",80,25);if(nn.layerSizes[0]>1)netCtx.fillText("Y",320,25);netCtx.fillText("INPUT",200,25);
        const lc=nn.layerSizes.length,gap=(HEIGHT-80)/(lc-1),nc=[];
        for(let l=0;l<lc;l++){const ln=[],cnt=nn.layerSizes[l],xg=WIDTH/(cnt+1),y=50+l*gap;for(let n=0;n<cnt;n++)ln.push({x:xg*(n+1),y});nc.push(ln);}
        for(let l=0;l<lc-1;l++){const cu=nc[l],nx=nc[l+1],W=nn.weights[l];for(let i=0;i<cu.length;i++)for(let j=0;j<nx.length;j++){const w=W[i*nx.length+j],aw=Math.abs(w);if(aw<0.05)continue;netCtx.beginPath();netCtx.moveTo(cu[i].x,cu[i].y);netCtx.lineTo(nx[j].x,nx[j].y);netCtx.strokeStyle=w>0?`rgba(60,160,255,${Math.min(aw,0.85)})`:`rgba(255,100,100,${Math.min(aw,0.85)})`;netCtx.lineWidth=aw*2.5;netCtx.stroke();}}
        const cls=['#32CD32','#FFD700','#D3D3D3'];
        for(let l=0;l<lc;l++){const co=(l===0)?cls[0]:(l===lc-1)?"#b0b0b0":cls[1],sc=(l===0)?"rgba(50,205,50,0.6)":(l===lc-1)?"rgba(255,255,255,0.2)":"rgba(255,215,0,0.6)";for(let n=0;n<nc[l].length;n++){const p=nc[l][n];let v=0;if(nn.nodeValues[l]&&nn.nodeValues[l][n]!==undefined)v=nn.nodeValues[l][n];netCtx.shadowBlur=Math.abs(v)*15;netCtx.shadowColor=sc;netCtx.beginPath();netCtx.arc(p.x,p.y,15,0,Math.PI*2);netCtx.fillStyle=co;netCtx.fill();netCtx.shadowBlur=0;netCtx.strokeStyle="#fff";netCtx.lineWidth=2;netCtx.stroke();netCtx.fillStyle="#111";netCtx.font="bold 10px monospace";netCtx.fillText(v.toFixed(1),p.x,p.y+1);}}
        netCtx.fillStyle="#aaa";netCtx.font="bold 12px 'Segoe UI',sans-serif";if(nn.layerSizes[lc-1]>0)netCtx.fillText("ANG",80,385);if(nn.layerSizes[lc-1]>1)netCtx.fillText("FORZA",320,385);netCtx.fillText("OUTPUT",200,385);
    }

    function drawScene(path,angle){
        simCtx.clearRect(0,0,WIDTH,HEIGHT);
        if(useBatch&&batchTargets.length>0)for(const bt of batchTargets){simCtx.beginPath();simCtx.arc(bt.x,bt.y,3,0,Math.PI*2);simCtx.fillStyle="rgba(206,147,216,0.35)";simCtx.fill();}
        for(const[r,c]of[[20,"#fff"],[16,"#111"],[12,"#00bcd4"],[8,"#f44336"],[4,"#ffeb3b"]]){simCtx.beginPath();simCtx.arc(target.x,target.y,r,0,Math.PI*2);simCtx.fillStyle=c;simCtx.fill();}
        simCtx.save();simCtx.translate(CANNON_X,CANNON_Y);simCtx.beginPath();simCtx.arc(0,0,12,Math.PI,0);simCtx.fillStyle="#ccc";simCtx.fill();simCtx.rotate(-angle);simCtx.beginPath();simCtx.moveTo(0,-4);simCtx.lineTo(24,-4);simCtx.lineTo(24,-8);simCtx.lineTo(34,0);simCtx.lineTo(24,8);simCtx.lineTo(24,4);simCtx.lineTo(0,4);simCtx.closePath();simCtx.fillStyle="#eee";simCtx.fill();simCtx.strokeStyle="#111";simCtx.lineWidth=1;simCtx.stroke();simCtx.restore();
        if(path&&path.length>1){simCtx.beginPath();simCtx.moveTo(path[0].x,path[0].y);for(let i=1;i<path.length;i++)simCtx.lineTo(path[i].x,path[i].y);const gr=simCtx.createLinearGradient(CANNON_X,CANNON_Y,target.x,target.y);gr.addColorStop(0,"rgba(200,240,255,0.9)");gr.addColorStop(1,"rgba(200,240,255,0.1)");simCtx.strokeStyle=gr;simCtx.lineWidth=3;simCtx.lineCap="round";simCtx.lineJoin="round";simCtx.shadowColor="#4fc3f7";simCtx.shadowBlur=10;simCtx.stroke();simCtx.shadowBlur=0;}
    }

    function loop(){
        if(isTraining){
            spdAcc+=speed;const it=Math.floor(spdAcc);spdAcc-=it;
            if(useBatch){statusText.innerText=useBP?"BATCH BP...":"BATCH EVO...";statusText.style.color="#ce93d8";statusText.style.background="rgba(40,0,40,0.8)";statusText.style.border="1px solid #ce93d8";if(useBP)trainBatchBP(it);else trainBatchEvo(it);}
            else{if(useBP){statusText.innerText="BACKPROP...";statusText.style.color="#66bb6a";statusText.style.background="rgba(0,40,0,0.8)";statusText.style.border="1px solid #66bb6a";trainSingleBP(it);}else{statusText.innerText="EVOLUZIONE...";statusText.style.color="#ffa726";statusText.style.background="rgba(40,25,0,0.8)";statusText.style.border="1px solid #ffa726";trainSingleEvo(it);}if(curLoss<LOSS_THRESHOLD)isTraining=false;}
        }else{statusText.innerText="LOCKED";statusText.style.color="#4fc3f7";statusText.style.background="rgba(0,40,40,0.8)";statusText.style.border="1px solid #4fc3f7";}
        const pi=getInputs(target.x,target.y,brain.layerSizes[0]),fo=brain.predict(pi),fp=mapOutputsToPhysics(fo);
        const res=calcTraj(fp.angle,fp.force,target.x,target.y);
        drawNet(brain);drawScene(res.path,fp.angle);
        lossText.innerHTML=useBatch?`PROBE: ${curLoss.toFixed(1)}<br>BATCH: ${batchLoss.toFixed(1)}`:`ERROR: ${curLoss.toFixed(1)}`;
        epochText.innerText=useBatch?`step: ${epoch}`:`epoch: ${epoch}`;
        requestAnimationFrame(loop);
    }

    simCanvas.addEventListener('mousedown',e=>{const r=simCanvas.getBoundingClientRect();target.x=e.clientX-r.left;target.y=e.clientY-r.top;if(!useBatch){curLoss=Infinity;bestError=Infinity;isTraining=true;epoch=0;}});

    initBrain();updateUI();renderEditor();loop();
})();
</script>

*Clicca sul pannello destro per spostare il bersaglio. In modalità mini-batch, il click diventa un "test" — la rete continua ad allenarsi su target casuali e puoi testare in tempo reale quanto ha generalizzato.*

*Rallenta la velocità a 0.25x per vedere come cambiano i pesi e lo spessore delle linee nel corso della simulazione. Lo trovo affascinante.*

## Balistica

Immaginate un cannone piazzato nell'angolo in basso a sinistra di uno schermo. Da qualche parte sul canvas c'è un bersaglio. La rete neurale deve scoprire due numeri — un angolo e una forza — tali che il proiettile, seguendo una banale parabola gravitazionale, passi il più vicino possibile al centro del target.

L'input è semplice: le coordinate (x, y) del bersaglio normalizzate. L'output sono due valori grezzi che, passati attraverso una funzione sigmoide, diventano un angolo (tra 3° e 86°) e una forza (tra 5 e 45 unità). Nessuna formula balistica è codificata nella rete. Nessuno le dice come funziona la gravità. **Deve capirlo da sola**.

## Anatomia di un neurone artificiale

Un neurone artificiale fa esattamente tre cose:

1. Prende tutti i suoi input e li moltiplica per i rispettivi **pesi** — numeri che rappresentano "quanto mi interessa questo segnale".
2. Somma tutto e aggiunge un **bias** — un offset che sposta il punto di lavoro del neurone, determinando quanto facilmente si attiva anche in assenza di segnale forte.
3. Passa il risultato attraverso una **funzione di attivazione** (nel nostro caso, la tangente iperbolica) che schiaccia il valore tra -1 e +1.

Ecco cosa fa concretamente un singolo neurone del primo livello nascosto della nostra rete:

>output = tanh(x × peso_x + y × peso_y + bias)

Tre moltiplicazioni, due somme, una funzione. Non c'è un "ragionamento" qui, non c'è "comprensione". Eppure, quando colleghi abbastanza di questi nodi e trovi i pesi giusti, il sistema *funziona*.

## Due strategie per imparare

La simulazione implementa due approcci radicalmente diversi per trovare i pesi giusti, ed è confrontandoli che emerge qualcosa di interessante.

### L'evoluzione: tentativi alla cieca

Il primo metodo è ispirato all'evoluzione biologica. Funziona così: prendi la rete attuale, creane una copia, cambia casualmente qualche peso (mutazione), e vedi se la copia fa meglio dell'originale. Se sì, la copia diventa il nuovo campione. Se no, scartala e riprova.

Nessun calcolo, nessuna direzione. Solo generazione casuale e selezione. È esattamente il meccanismo darwiniano: variazione cieca e selezione non-cieca. Non sa *perché* un cambiamento ha funzionato — sa solo che ha funzionato.

### La backpropagation: seguire il gradiente

Il secondo metodo è la vera backpropagation, l'algoritmo che ha reso possibile il deep learning moderno. L'idea è concettualmente elegante: invece di andare alla cieca, **calcola in che direzione aggiustare ogni peso per ridurre l'errore**.

C'è un dettaglio tecnico significativo nella nostra simulazione. La rete neurale in sé è differenziabile — possiamo calcolare analiticamente come una piccola variazione di un peso influenzi l'output. Ma la simulazione fisica (il proiettile che vola, rimbalza, e la cui distanza minima dal target viene misurata) non lo è. È un sistema discreto con un `min()` dentro.

La soluzione è un approccio ibrido: usiamo **differenze numeriche** per capire come i due output della rete (angolo e forza grezzi) influenzano la distanza dal bersaglio — perturbiamo ogni output di una quantità microscopica ε e misuriamo come cambia l'errore. Una volta ottenuti questi gradienti "esterni", li propaghiamo all'indietro **analiticamente** attraverso la rete usando la regola della catena e la derivata della tangente iperbolica: `tanh'(z) = 1 - tanh²(z)`.

Il risultato è che ogni singolo peso riceve un'istruzione precisa: "spostati di tanto in questa direzione". Non è un tentativo — è una discesa calcolata lungo la superficie dell'errore.

## Dal singolo al generale: il mini-batch

C'è un problema fondamentale con l'approccio "un bersaglio alla volta". La rete non sta veramente *imparando* — sta *memorizzando*. Trova i pesi che risolvono un singolo esercizio, e quando cambi target quei pesi non servono più.

Il mini-batch risolve questo in modo elegante. Ad ogni iterazione, invece di allenare la rete su un solo punto, le presentiamo un gruppo di bersagli casuali sparsi per tutto il canvas — 16, 32, 64 alla volta. I gradienti di ogni bersaglio vengono mediati in un unico aggiornamento dei pesi.

Il punto chiave: quel singolo aggiornamento deve accontentare *tutti* i bersagli contemporaneamente. La rete non può memorizzare la risposta per un punto perché verrebbe penalizzata sugli altri. È costretta a trovare la **regola sottostante** — la relazione fisica tra posizione e parametri di tiro.

È la differenza tra imparare a memoria le risposte di un singolo esercizio e capire il metodo generale.

---

## La quarta ferita

Torniamo al punto di partenza. Cosa c'è dentro questa rete che "impara a sparare"? Moltiplicazioni di numeri decimali, somme, tangenti iperboliche, e una regola ricorsiva per aggiustare i coefficienti. Niente di più. Eppure il sistema *generalizza*: impara la balistica senza che nessuno gli abbia spiegato la gravità.

Da quanto ho capito, i vari modelli AI hanno alla base la stessa cosa — solo che invece di 20 pesi ne hanno miliardi, invece di due input ne hanno migliaia, e invece della balistica hanno imparato a predire la prossima parola in un testo.

E quando quel meccanismo, scalato, produce qualcosa che non sappiamo più distinguere dal pensiero umano, la domanda non è "come è possibile che una macchina pensi?" ma piuttosto: "cos'è davvero il pensiero, se bastano moltiplicazioni e somme?"

La quarta ferita narcisistica non è che le macchine ci superano. È che ci mostrano la meccanica di ciò che credevamo fosse magia.
