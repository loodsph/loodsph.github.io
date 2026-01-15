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
            <p class="text-xs text-gray-400 m-0 p-0">Simulazione Identica all'originale</p>
        </div>
        <div class="flex gap-2">
             <button id="gs-btn-play" class="bg-green-600 hover:bg-green-500 text-white px-4 py-1 rounded text-sm font-bold transition">▶ Play</button>
             <button id="gs-btn-reset" class="bg-red-600 hover:bg-red-500 text-white px-4 py-1 rounded text-sm font-bold transition">Reset</button>
        </div>
    </div>

    <div class="flex flex-col md:flex-row">
        <div class="flex-1 p-4 bg-black flex justify-center items-center">
            <canvas id="gs-canvas" width="200" height="200" class="border border-gray-800 rounded shadow-lg cursor-crosshair touch-none w-full max-w-[400px] aspect-square" style="image-rendering: pixelated;"></canvas>
        </div>

        <div class="w-full md:w-64 bg-gray-800 p-4 border-l border-gray-700 flex flex-col gap-4">
            
            <div>
                <label class="block text-xs uppercase text-gray-500 font-bold mb-2">Preset</label>
                <div class="grid grid-cols-2 gap-2">
                    <button onclick="window.setGSPreset('mitosis')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Mitosi</button>
                    <button onclick="window.setGSPreset('coral')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Corallo</button>
                    <button onclick="window.setGSPreset('fingerprint')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Impronte</button>
                    <button onclick="window.setGSPreset('waves')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Onde</button>
                    <button onclick="window.setGSPreset('maze')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Labirinto</button>
                    <button onclick="window.setGSPreset('holes')" class="bg-gray-700 hover:bg-gray-600 px-2 py-1 rounded text-xs transition">Buchi</button>
                </div>
            </div>

            <div class="bg-gray-900 p-3 rounded border border-gray-700">
                <p class="text-xs text-gray-400 font-mono">F: <span id="gs-val-f" class="text-blue-400">0.055</span></p>
                <p class="text-xs text-gray-400 font-mono">K: <span id="gs-val-k" class="text-red-400">0.062</span></p>
            </div>
            
             <div class="bg-gray-800 p-3 rounded">
                <p class="text-xs font-semibold mb-2 text-gray-400">Legenda Colori:</p>
                <div class="h-4 rounded w-full" style="background: linear-gradient(to right, #000004, #280b54, #65156e, #9f2a63, #d44842, #f57d15, #fac127, #fcffa4);"></div>
            </div>

            <p class="text-xs text-gray-500 italic mt-auto">Clicca per perturbare.</p>
        </div>
    </div>
</div>

{% raw %}
<script>
(function() {
    // --- 1. CONFIGURAZIONE & VARIABILI ---
    const canvas = document.getElementById('gs-canvas');
    if (!canvas) return;
    const ctx = canvas.getContext('2d', { alpha: false });
    
    const width = 200;
    const height = 200;
    const stepsPerFrame = 8; // Velocità simulazione (come nell'originale)

    // Palette "Inferno" (Copiata esattamente dal codice React)
    const infernoColors = [
      [0, 0, 4], [40, 11, 84], [101, 21, 110], [159, 42, 99],
      [212, 72, 66], [245, 125, 21], [250, 193, 39], [252, 255, 164]
    ];

    // Stato Simulazione
    let f = 0.055;
    let k = 0.062;
    let Da = 1.0;
    let Db = 0.3; // Nota: nel codice react era 0.3, nel mio precedente avevo messo 0.5. Corretto.
    let dt = 0.2; // Nota: nel codice react era 0.2. Corretto.
    
    let isPlaying = false;
    let animationId;

    // Buffer (Typed Arrays per performance, identici a React)
    let U = new Float32Array(width * height);
    let V = new Float32Array(width * height);
    let nextU = new Float32Array(width * height);
    let nextV = new Float32Array(width * height);

    // --- 2. FUNZIONI UTILI (Copia esatta React) ---
    
    function interpolateColor(t) {
      t = Math.max(0, Math.min(1, t));
      const idx = t * (infernoColors.length - 1);
      const i = Math.floor(idx);
      const frac = idx - i;
      if (i >= infernoColors.length - 1) return infernoColors[infernoColors.length - 1];
      const c1 = infernoColors[i];
      const c2 = infernoColors[i + 1];
      return [
        Math.round(c1[0] + frac * (c2[0] - c1[0])),
        Math.round(c1[1] + frac * (c2[1] - c1[1])),
        Math.round(c1[2] + frac * (c2[2] - c1[2]))
      ];
    }

    // --- 3. CORE SIMULATION ---

    function reset(withPerturbation = true) {
        for (let i = 0; i < width * height; i++) {
            U[i] = 1.0;
            V[i] = 0.0;
        }
        if (withPerturbation) {
            const cx = Math.floor(width / 2);
            const cy = Math.floor(height / 2);
            const r = 20;
            for (let y = cy - r; y < cy + r; y++) {
                for (let x = cx - r; x < cx + r; x++) {
                    if (x >= 0 && x < width && y >= 0 && y < height) {
                        const idx = y * width + x;
                        U[idx] = 0.5;
                        V[idx] = 0.25;
                    }
                }
            }
            // Rumore casuale (importante per rompere la simmetria)
            for (let i = 0; i < width * height; i++) {
                V[i] += Math.random() * 0.05;
            }
        }
        nextU.set(U);
        nextV.set(V);
        draw();
    }

    function addPerturbation(x, y, radius = 5) {
        for (let dy = -radius; dy <= radius; dy++) {
            for (let dx = -radius; dx <= radius; dx++) {
                const px = x + dx;
                const py = y + dy;
                if (px >= 0 && px < width && py >= 0 && py < height) {
                    if (dx * dx + dy * dy <= radius * radius) {
                        const idx = py * width + px;
                        U[idx] = 0.5;
                        V[idx] = 0.25;
                    }
                }
            }
        }
    }

    function step() {
        // Implementazione esatta del loop React
        for (let y = 1; y < height - 1; y++) {
            for (let x = 1; x < width - 1; x++) {
                const idx = y * width + x;
                const idxUp = (y - 1) * width + x;
                const idxDown = (y + 1) * width + x;
                const idxLeft = y * width + (x - 1);
                const idxRight = y * width + (x + 1);

                const lapU = U[idxUp] + U[idxDown] + U[idxLeft] + U[idxRight] - 4 * U[idx];
                const lapV = V[idxUp] + V[idxDown] + V[idxLeft] + V[idxRight] - 4 * V[idx];
                
                const uvv = U[idx] * V[idx] * V[idx];
                
                const dU = Da * lapU - uvv + f * (1 - U[idx]);
                const dV = Db * lapV + uvv - (k + f) * V[idx];

                nextU[idx] = U[idx] + dU * dt;
                nextV[idx] = V[idx] + dV * dt;

                // Clamp
                if (nextU[idx] < 0) nextU[idx] = 0; else if (nextU[idx] > 1) nextU[idx] = 1;
                if (nextV[idx] < 0) nextV[idx] = 0; else if (nextV[idx] > 1) nextV[idx] = 1;
            }
        }
        // Swap
        let tempU = U; U = nextU; nextU = tempU;
        let tempV = V; V = nextV; nextV = tempV;
    }

    // --- 4. RENDERING (Canvas API Standard) ---
    // Usiamo putImageData classico per essere fedeli ai colori, non la hack buffer 32bit
    
    function draw() {
        const imageData = ctx.createImageData(width, height);
        const data = imageData.data;
        
        for (let i = 0; i < width * height; i++) {
            const vVal = V[i];
            // Usa esattamente la funzione colore originale
            const color = interpolateColor(vVal * 2.5); 
            
            data[i * 4] = color[0];     // R
            data[i * 4 + 1] = color[1]; // G
            data[i * 4 + 2] = color[2]; // B
            data[i * 4 + 3] = 255;      // A
        }
        
        // Disegna su un canvas temporaneo e poi scala (o disegna diretto)
        // Disegno diretto per semplicità e pixel-perfect look
        ctx.putImageData(imageData, 0, 0);
    }

    function loop() {
        if (!isPlaying) return;
        // Esegui N step matematici per ogni frame video
        for (let i = 0; i < stepsPerFrame; i++) {
            step();
        }
        draw();
        animationId = requestAnimationFrame(loop);
    }

    // --- 5. INTERAZIONE UI ---

    const btnPlay = document.getElementById('gs-btn-play');
    const btnReset = document.getElementById('gs-btn-reset');
    
    btnPlay.onclick = () => {
        isPlaying = !isPlaying;
        btnPlay.innerText = isPlaying ? "⏸ Pausa" : "▶ Play";
        btnPlay.classList.toggle('bg-green-600');
        btnPlay.classList.toggle('bg-yellow-600');
        if (isPlaying) loop();
    };

    btnReset.onclick = () => {
        isPlaying = false;
        btnPlay.innerText = "▶ Play";
        btnPlay.classList.remove('bg-yellow-600');
        btnPlay.classList.add('bg-green-600');
        reset(true);
    };

    // Gestione Mouse/Touch sul Canvas
    function handleInput(e) {
        const rect = canvas.getBoundingClientRect();
        // Fattore di scala tra CSS pixel e Canvas pixel interni (200x200)
        const scaleX = width / rect.width;
        const scaleY = height / rect.height;
        
        let clientX = e.touches ? e.touches[0].clientX : e.clientX;
        let clientY = e.touches ? e.touches[0].clientY : e.clientY;

        const x = Math.floor((clientX - rect.left) * scaleX);
        const y = Math.floor((clientY - rect.top) * scaleY);
        
        addPerturbation(x, y, 8);
        draw(); // Ridisegna subito per feedback visivo
    }

    let isDrawing = false;
    canvas.addEventListener('mousedown', (e) => { isDrawing = true; handleInput(e); });
    canvas.addEventListener('mousemove', (e) => { if(isDrawing) handleInput(e); });
    window.addEventListener('mouseup', () => isDrawing = false);
    canvas.addEventListener('touchstart', (e) => { e.preventDefault(); isDrawing = true; handleInput(e); }, {passive: false});
    canvas.addEventListener('touchmove', (e) => { e.preventDefault(); if(isDrawing) handleInput(e); }, {passive: false});

    // --- 6. PRESETS ---
    window.setGSPreset = function(name) {
        // Valori presi dal codice React originale
        if (name === 'mitosis')     { f = 0.055; k = 0.062; }
        if (name === 'coral')       { f = 0.062; k = 0.063; } // Era diverso nel mio codice precedente
        if (name === 'fingerprint') { f = 0.037; k = 0.06; }
        if (name === 'spots')       { f = 0.03;  k = 0.062; }
        if (name === 'waves')       { f = 0.014; k = 0.054; }
        if (name === 'maze')        { f = 0.029; k = 0.057; }
        if (name === 'holes')       { f = 0.039; k = 0.058; }

        document.getElementById('gs-val-f').innerText = f.toFixed(3);
        document.getElementById('gs-val-k').innerText = k.toFixed(3);

        reset(true);
        // Start automatico
        if (!isPlaying) btnPlay.click();
    };

    // Avvio Iniziale
    reset(true);

})();
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
