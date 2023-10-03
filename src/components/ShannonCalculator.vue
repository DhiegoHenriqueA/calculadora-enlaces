<template>
    <div >
      <h3>Capacidade Máxima de Canal</h3>
  
      <div class="form-container">
        <div class="input-container">
            <label for="larguraBanda">Largura de Banda (Hz):</label>
          <input type="number" id="larguraBanda" v-model="larguraBanda" placeholder="Insira a largura de banda">
        </div>
  
        <div class="input-container">
          <label for="sinalRuido">Relação Sinal-Ruído (dB):</label>
          <input type="number" id="sinalRuido" v-model="sinalRuido" placeholder="Insira a relação sinal-ruído">
        </div>
  
        <div class="button-container">
          <button class="calcular-button" @click="calcularCapacidade">Calcular Capacidade</button>
        </div>
      </div>
  
      <div class="resultado" v-if="capacidade !== null">
        <div class="resultado-box">
          <p>A capacidade máxima do canal é <span class="result-value">{{ capacidade.toFixed(2) }} bps</span>.</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        larguraBanda: null,
        sinalRuido: null,
        capacidade: null
      };
    },
    methods: {
      calcularCapacidade() {
        // Converter a relação sinal-ruído de decibéis para uma relação linear
        const sinalRuidoLinear = Math.pow(10, this.sinalRuido / 10);
        
        // Calcular a capacidade máxima do canal em bps
        this.capacidade = this.larguraBanda * Math.log2(1 + sinalRuidoLinear);
      }
    }
  };
  </script>
  
  <style >

  </style>
  