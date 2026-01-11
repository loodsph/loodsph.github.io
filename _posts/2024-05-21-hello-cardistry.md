---
layout: post
title:  "Hello World: Inizia il viaggio"
date:   2024-05-21 21:00:00 +0100
categories: [intro, pensieri]
tags: [cardistry, setup]
---

Benvenuti nel mio *Second Brain*.
Qui raccoglierò i miei progressi nel Cardistry e nel coding.

## Perché questo blog?

Scrivere mi aiuta a chiarire le idee. A differenza di Medium o Instagram, qui ho il controllo totale del codice.

### Test Interattivo

Ecco un esempio di script che vive direttamente dentro questo articolo:

<div id="demo-box" style="padding: 15px; background: #eef; border-radius: 5px; margin: 20px 0;">
    <p>Clicca il pulsante per calcolare un numero random:</p>
    <button onclick="calcolaRandom()">Genera Numero</button>
    <p id="risultato" style="font-weight: bold; font-size: 20px; margin-top: 10px;">-</p>
</div>

<script>
    function calcolaRandom() {
        let num = Math.floor(Math.random() * 100);
        document.getElementById('risultato').innerText = "Numero: " + num;
        console.log("Funzione eseguita dal post!");
    }
</script>

Come vedi, posso mescolare **Markdown** (per il testo) e **HTML/JS** (per l'interazione).