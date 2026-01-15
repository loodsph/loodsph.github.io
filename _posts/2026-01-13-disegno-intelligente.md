---
layout: post
title: Il disegno intelligente
date: 2026-01-13 10:00:00 +0100
categories: [complexity, filosofia, math]
tags: [gray-scott, turing, emergenza, chaos-theory]
---

Ho disegnato un esperimento che si può fare in pochi minuti su uno schermo.

Prendi due sostanze virtuali, chiamale **U** e **V**. Dai loro due regole semplicissime:

1.  **V** consuma **U** per riprodursi.
2.  Entrambe si diffondono nello spazio, ma **U** più velocemente di **V**.

Premi play. Aspetta qualche migliaio di iterazioni (è veloce).

<script src="https://cdn.tailwindcss.com"></script>

<div id="gs-wrapper" class="not-prose my-10 bg-gray-900 text-gray-200 rounded-xl shadow-2xl overflow-hidden font-sans border border-gray-700">
    <div class="p-4 bg-gray-800 border-b border-gray-700 flex justify-between items-center flex-wrap gap-4">
        <div>
            <h3 class="font-bold text-white text-lg m-0 p-0">Gray-Scott Lab</h3>
            <p class="text-xs text-gray-400 m-0 p-0">Reazione-Diffusione in tempo reale</p>
        </div>
        <div class="flex gap-2">
             <button id="btn-play" class="bg-green-600 hover:bg-green-500 text-white px-4 py-1 rounded text-sm font-bold transition">▶ Play</button>
             <button id="btn-reset" class="bg-red-600 hover:bg-red-500 text-white px-4 py-1 rounded text-sm font-bold transition">Reset</button>
        </div>
    </div>
    <div class="flex flex-col md:flex-row">
        <div class="flex-1 p-4 bg-black flex justify-center items-center relative">
            <canvas id="gs-canvas" width="200" height="200" class="border border-gray-800 rounded shadow-lg cursor-crosshair touch-none w-full max-w-[400px] h-auto" style="image-rendering: pixelated;"></canvas>
            <div id="loading-msg" class="absolute text-gray-500 text-xs">Caricamento...</div>
        </div>
        <div class="w-full md:w-64 bg-gray-800 p-4 border-l border-gray-700 flex flex-col gap-4">
            <div>
                <label class="block text-xs uppercase text-gray-500 font-bold mb-2">Preset</label>
                <div class="grid grid-cols-2 gap-2">
                    <button onclick="window.setGSPreset('mitosis')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Mitosi</button>
                    <button onclick="window.setGSPreset('coral')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Corallo</button>
                    <button onclick="window.setGSPreset('maze')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Labirinto</button>
                    <button onclick="window.setGSPreset('holes')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Buchi</button>
                </div>
            </div>
            <div class="bg-gray-900 p-3 rounded border border-gray-700">
                <p class="text-xs text-gray-400 font-mono">Feed (f): <span id="val-f" class="text-blue-400">0.055</span></p>
                <p class="text-xs text-gray-400 font-mono">Kill (k): <span id="val-k" class="text-red-400">0.062</span></p>
            </div>
            <p class="text-xs text-gray-500 italic mt-auto">Clicca sul canvas per interagire.</p>
        </div>
    </div>
</div>

{% raw %}
<script>
document.addEventListener("DOMContentLoaded", function() {
    // Verifichiamo che il canvas esista
    const canvas = document.getElementById('gs-canvas');
    if (!canvas) { console.error("Canvas Gray-Scott non trovato!"); return; }

    const ctx = canvas.getContext('2d', { alpha: false });
    const loadingMsg = document.getElementById('loading-msg');
    
    // Configurazione
    const w = 200;
    const h = 200;
    
    let u = new Float32Array(w * h);
    let v = new Float32Array(w * h);
    let nextU = new Float32Array(w * h);
    let nextV = new Float32Array(w * h);
    
    let params = { f: 0.055, k: 0.062, da: 1.0, db: 0.5, dt: 1.0 };
    let isPlaying = false;
    let animationId;

    function init() {
        for(let i=0; i<w*h; i++) {
            u[i] = 1.0;
            v[i] = 0.0;
        }
        perturb(w/2, h/2, 10);
        draw();
        if(loadingMsg) loadingMsg.style.display = 'none';
    }

    function perturb(cx, cy, r) {
        const r2 = r*r;
        const startY = Math.max(0, cy - r);
        const endY = Math.min(h, cy + r);
        const startX = Math.max(0, cx - r);
        const endX = Math.min(w, cx + r);

        for(let y=startY; y<endY; y++) {
            for(let x=startX; x<endX; x++) {
                if( (x-cx)*(x-cx) + (y-cy)*(y-cy) < r2 ) {
                    let i = y*w + x;
                    u[i] = 0.5;
                    v[i] = 0.25;
                }
            }
        }
    }

    function step() {
        for(let y=1; y<h-1; y++) {
            for(let x=1; x<w-1; x++) {
                const i = y*w + x;
                const lapU = (u[i-1] + u[i+1] + u[i-w] + u[i+w] - 4*u[i]);
                const lapV = (v[i-1] + v[i+1] + v[i-w] + v[i+w] - 4*v[i]);
                const uvv = u[i] * v[i] * v[i];
                let du = params.da * lapU - uvv + params.f * (1 - u[i]);
                let dv = params.db * lapV + uvv - (params.k + params.f) * v[i];
                nextU[i] = u[i] + du * params.dt;
                nextV[i] = v[i] + dv * params.dt;
                if(nextU[i] < 0) nextU[i] = 0; else if(nextU[i] > 1) nextU[i] = 1;
                if(nextV[i] < 0) nextV[i] = 0; else if(nextV[i] > 1) nextV[i] = 1;
            }
        }
        let temp = u; u = nextU; nextU = temp;
        temp = v; v = nextV; nextV = temp;
    }

    const imgData = ctx.createImageData(w, h);
    const buf32 = new Uint32Array(imgData.data.buffer);

    function draw() {
        for(let i=0; i<w*h; i++) {
            const val = v[i];
            const t = Math.min(1, val * 3.5); 
            const r = Math.min(255, t * 255 * 2); 
            const g = Math.min(255, t * 255 * 0.8);
            const b = Math.min(255, t * 255 * 0.2 + (val > 0.4 ? (val-0.4)*200 : 0));
            buf32[i] = (255 << 24) | (b << 16) | (g << 8) | r;
        }
        ctx.putImageData(imgData, 0, 0);
    }

    function loop() {
        if(!isPlaying) return;
        for(let k=0; k<12; k++) step(); 
        draw();
        animationId = requestAnimationFrame(loop);
    }

    const btnPlay = document.getElementById('btn-play');
    if(btnPlay) {
        btnPlay.onclick = () => {
            isPlaying = !isPlaying;
            btnPlay.innerText = isPlaying ? "⏸ Pausa" : "▶ Play";
            btnPlay.classList.toggle('bg-green-600');
            btnPlay.classList.toggle('bg-yellow-600');
            if(isPlaying) loop();
        };
    }

    const btnReset = document.getElementById('btn-reset');
    if(btnReset) {
        btnReset.onclick = () => {
            isPlaying = false;
            btnPlay.innerText = "▶ Play";
            btnPlay.classList.remove('bg-yellow-600');
            btnPlay.classList.add('bg-green-600');
            init();
        };
    }

    window.setGSPreset = function(name) {
        if(name === 'mitosis') { params.f = 0.055; params.k = 0.062; }
        if(name === 'coral')   { params.f = 0.0545; params.k = 0.062; }
        if(name === 'maze')    { params.f = 0.029; params.k = 0.057; }
        if(name === 'holes')   { params.f = 0.039; params.k = 0.058; }
        
        const elF = document.getElementById('val-f');
        const elK = document.getElementById('val-k');
        if(elF) elF.innerText = params.f.toFixed(3);
        if(elK) elK.innerText = params.k.toFixed(3);
        
        init(); // Resetta la griglia
        // Piccolo trucco: facciamo avanzare un po' la simulazione per mostrare subito il pattern
        for(let i=0; i<50; i++) step(); 
        draw();
        
        // Auto start
        if(!isPlaying && btnPlay) btnPlay.click();
    };

    function handleInput(e) {
        const rect = canvas.getBoundingClientRect();
        const scaleX = w / rect.width;
        const scaleY = h / rect.height;
        let clientX = e.touches ? e.touches[0].clientX : e.clientX;
        let clientY = e.touches ? e.touches[0].clientY : e.clientY;
        const x = Math.floor((clientX - rect.left) * scaleX);
        const y = Math.floor((clientY - rect.top) * scaleY);
        perturb(x, y, 8);
        if(!isPlaying) draw();
    }

    let isDrawing = false;
    canvas.addEventListener('mousedown', (e) => { isDrawing = true; handleInput(e); });
    canvas.addEventListener('mousemove', (e) => { if(isDrawing) handleInput(e); });
    window.addEventListener('mouseup', () => isDrawing = false);
    canvas.addEventListener('touchstart', (e) => { e.preventDefault(); isDrawing = true; handleInput(e); }, {passive: false});
    canvas.addEventListener('touchmove', (e) => { e.preventDefault(); if(isDrawing) handleInput(e); }, {passive: false});

    init();
});
</script>
{% endraw %}

Dal nulla emergono macchie, strisce, labirinti, strutture che si dividono come cellule. Pattern che sembrano progettati da un artista, o copiati dalla pelle di un leopardo, dalle conchiglie marine, dalle impronte digitali.

Chi li ha disegnati? **Nessuno.**

Nessuno li ha programmati. Sono *emersi*.

## Il sistema Gray-Scott

Il modello si chiama Gray-Scott, dal nome dei chimici che lo formalizzarono. Le equazioni sono quasi banali. I fattori coinvolti sono veramente pochissimi:

* Due sostanze ($U$ e $V$)
* Diffusione
* Una reazione (semplice)
* Quattro parametri
<br>
<br>

$\dfrac{\partial u}{\partial t} = D_u \nabla^2 u - uv^2 + F(1-u)$

$\dfrac{\partial v}{\partial t} = D_v \nabla^2 v + uv^2 - (F + k)v$ 

<details>
<summary>Variabili</summary>

1. Variabili e Operatori
Questi simboli descrivono lo stato del sistema e come cambia nello spazio e nel tempo.
$u$: Concentrazione della prima sostanza chimica (spesso chiamata "substrato" o cibo).
$v$: Concentrazione della seconda sostanza chimica (spesso chiamata "attivatore" o predatore).
$t$: Tempo.
$\dfrac{\partial}{\partial t}$: Derivata parziale rispetto al tempo. Indica la velocità con cui le concentrazioni $u$ e $v$ cambiano in un dato istante.
$\nabla^2$: Operatore di Laplace (Laplaciano). Rappresenta la diffusione spaziale, ovvero come le sostanze si espandono o si disperdono nello spazio (2D o 3D).

2. Parametri (Costanti)
Questi valori determinano il comportamento del sistema e il tipo di pattern che emergerà.
$D_u$: Coefficiente di diffusione di $u$. Indica quanto velocemente la sostanza $u$ si diffonde nell'ambiente.
$D_v$: Coefficiente di diffusione di $v$. Indica quanto velocemente la sostanza $v$ si diffonde.
Nota: In questo modello, solitamente $D_u$ deve essere molto più grande di $D_v$ (ad es. $u$ diffonde due volte più velocemente di $v$) affinché si formino dei pattern.
$F$: Tasso di alimentazione (Feed rate). Controlla quanto "cibo" ($u$) viene aggiunto al sistema dall'esterno.
$k$: Tasso di rimozione (Kill rate). Controlla quanto velocemente la sostanza $v$ viene eliminata o decade dal sistema.


</details>
<br>
<br>
Eppure, da questo sistema minimale nascono pattern di una varietà stupefacente. Cambiando leggermente i parametri $f$ (feed) e $k$ (kill), ottieni strutture completamente diverse: punti che si moltiplicano come batteri, onde che pulsano, labirinti che si intrecciano, coralli che crescono.

La domanda sorge spontanea: **chi ha progettato questi pattern?**

La risposta è: nessuno. O meglio: la matematica stessa, le proprietà intrinseche dello spazio e del tempo, le conseguenze inevitabili di regole semplici applicate ripetutamente.

## L’argomento del “disegno intelligente”

I sostenitori del disegno intelligente (*Intelligent Design*) partono da un’osservazione corretta: la natura è piena di strutture incredibilmente complesse. L’occhio umano, il flagello batterico, i pattern sulle ali delle farfalle.

Da questa osservazione traggono una conclusione: tale complessità non può essere emersa spontaneamente. Deve esserci stato un progettista, un’intelligenza che ha disegnato queste strutture.

L’argomento ha un nome tecnico: **“complessità irriducibile”**. L’idea è che certi sistemi siano così intricati, così finemente calibrati, che rimuovendo un singolo componente smetterebbero di funzionare. E quindi, sostengono, non possono essere emersi gradualmente: devono essere stati creati tutti insieme, in un atto di progettazione consapevole.

È un argomento seducente. Ha l’eleganza della semplicità: vedo complessità, quindi deduco un creatore.

Ma c’è un problema fondamentale.

L’argomento del disegno intelligente si basa sulla assunzione implicita che esistano solo due possibilità:
1.  **Caso puro** (caos, rumore, disordine)
2.  **Progettazione intelligente** (un creatore con un piano)

Se la complessità non può nascere dal caso, deve esserci un progettista.

Ma questa è una falsa dicotomia. Esiste una terza via, e il sistema Gray-Scott ce la mostra con chiarezza cristallina: **l’emergenza**.

## La Terza Via

L’emergenza è quel fenomeno per cui sistemi con regole semplici, iterati nel tempo, producono comportamenti complessi che non erano “contenuti” nelle regole stesse. Nessuno, guardando le due equazioni di Gray-Scott, potrebbe prevedere i pattern che ne emergono. Eppure quei pattern sono conseguenze necessarie delle equazioni.

Certo, se i parametri fossero variati di pochissimo, ad esempio, il Carbonio non avrebbe potuto esistere. Ma questo non vuol dire che non si sarebbe creata una struttura altrettanto complessa. Ci sono molte combinazioni di $f$ e $k$ che portano comunque ad un pattern.

Magari non assomiglia a una cellula, magari assomiglia a un labirinto o a un corallo. L’errore sta nel pensare che l’universo sia stato calibrato per produrre *esattamente* noi (o il carbonio).

La verità che ci insegna il sistema Gray-Scott è che **la complessità è robusta**: non serve "centrare" un parametro miracoloso per ottenere struttura. L’ordine emerge in molteplici regioni dello spazio delle possibilità. Noi siamo semplicemente i figli della regione in cui siamo capitati, non i destinatari predestinati di un piano.

Come scriveva Douglas Adams (l’autore della più bella trilogia in cinque parti mai prodotta):

> «Immaginate una pozzanghera che si sveglia una mattina e pensa: “Che mondo interessante è questo in cui mi trovo, non è vero? Un buco interessante, vero? Mi si adatta piuttosto bene, non vi pare? In effetti, mi si adatta in modo talmente perfetto che deve essere stato fatto su misura per me!”»

Non c’è caso. Non c’è progetto. **C’è matematica.**

## Turing e la morfogenesi

Nel 1952, Alan Turing — sì, lo stesso Turing della macchina di Turing e della decifrazione di Enigma — pubblicò un paper rivoluzionario intitolato *“The Chemical Basis of Morphogenesis”*.

Turing dimostrò matematicamente che se hai due sostanze (un “attivatore” e un “inibitore”) che diffondono a velocità diverse, l’equilibrio uniforme diventa instabile. Piccole fluttuazioni casuali vengono amplificate invece che smorzate. E il sistema “precipita” spontaneamente in configurazioni strutturate.

Sessant’anni dopo, i biologi hanno trovato esattamente questi meccanismi in azione: nelle strisce delle zebre, nelle dita delle mani, nella disposizione dei follicoli piliferi.

La natura usa lo stesso trucco del nostro modello Gray-Scott. Non perché qualcuno l’abbia programmata così, ma perché è una conseguenza matematica inevitabile di come funzionano reazione e diffusione.

## Diventare adulti

C’è qualcosa di profondamente umiliante — e al tempo stesso liberatorio — in questa prospettiva.

**Umiliante**, perché dissolve l’illusione che la complessità richieda un creatore superiore, che tutto sa e tutto può, sostanzialmente quello che pensano i bambini di 5 anni del loro padre. I pattern che vediamo in natura non sono “per” qualcosa, non sono stati pensati da nessuno. Sono semplicemente ciò che accade quando certe condizioni sono soddisfatte.

**Liberatorio**, perché ci mostra che l’universo è più ricco di quanto la dicotomia caso/progetto suggerisca. Non siamo costretti a scegliere tra il nichilismo del caos e il comfort di un progettista benevolo. Esiste una terza opzione: un universo dove la struttura emerge spontaneamente, dove la complessità è una proprietà naturale della materia organizzata.

E, a mio parere, questa opzione è più meravigliosa di entrambe le alternative.

### Cosa significa tutto questo?

Non sto dicendo che la scienza abbia “dimostrato” l’inesistenza di un creatore. Questa non è una questione scientifica, ma filosofica e personale.

Quello che sto dicendo è più modesto: l’argomento della complessità irriducibile non regge. Non è vero che la complessità richieda necessariamente un progettista. Esistono meccanismi ben compresi — reazione-diffusione, selezione naturale, auto-organizzazione — che producono complessità a partire da regole semplici.
