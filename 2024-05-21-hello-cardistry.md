---
layout: post
title:  "Hello Cardistry: Primo Esperimento"
date:   2024-05-21 10:00:00 +0200
categories: cardistry code
---

Benvenuti nel mio primo post. Oggi testiamo l'integrazione di JavaScript direttamente nel markdown per generare carte casuali.

Clicca il bottone qui sotto per estrarre una carta dal mazzo virtuale:

<div id="card-result" style="font-size: 48px; margin: 20px 0; font-family: monospace;">🂠</div>

<button id="draw-card-btn" style="padding: 10px 20px; font-size: 16px; cursor: pointer; background-color: #333; color: white; border: none; border-radius: 4px;">
  Estrai Carta
</button>

<script>
  document.getElementById('draw-card-btn').addEventListener('click', function() {
    const suits = ['♠️', '♥️', '♣️', '♦️'];
    const values = ['A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K'];
    
    const randomSuit = suits[Math.floor(Math.random() * suits.length)];
    const randomValue = values[Math.floor(Math.random() * values.length)];
    
    const resultDiv = document.getElementById('card-result');
    resultDiv.innerText = randomValue + randomSuit;
    
    // Change color for Hearts and Diamonds
    resultDiv.style.color = (randomSuit === '♥️' || randomSuit === '♦️') ? '#e74c3c' : '#2c3e50';
  });
</script>

Questo snippet dimostra come il "Creative Coding" possa visualizzare concetti di Cardistry in modo semplice.