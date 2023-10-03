<template>
    <div>
      <h3>Taxa de Nyquist</h3>

      <div class="form-container">
        <div class="input-container">
            <label for="larguraBanda">Largura de Banda do Sinal (Hz):</label>
            <input type="number" id="larguraBanda" v-model="larguraBanda" placeholder="Insira a largura de banda do sinal">
        </div>
    
        <div class="input-container">
            <label for="modulacaoMultinivel">Modulação Multinível:</label>
            <input type="number" id="modulacaoMultinivel" v-model="modulacaoMultinivel" placeholder="Insira a modulação multinível">
        </div>
    
        <div class="button-container">
            <button class="calcular-button" @click="calcularTaxaNyquist">Calcular Taxa de Nyquist</button>
        </div>
      </div>
  
      <div class="resultado" v-if="taxaNyquist !== null">
        <div class="resultado-box">
            <p>A Taxa de Nyquist é de <span class="result-value">{{ taxaNyquist }} bps.</span></p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        larguraBanda: null,
        modulacaoMultinivel: null,
        taxaNyquist: null,
      };
    },
    methods: {
      calcularTaxaNyquist() {
        if (this.larguraBanda !== null && this.modulacaoMultinivel !== null) {
          // Calcular a Taxa de Nyquist
          this.taxaNyquist = 2 * this.larguraBanda * this.modulacaoMultinivel;
        } else {
          // Caso algum dos campos esteja vazio
          this.taxaNyquist = null;
        }
      },
    },
  };
  </script>
  
  <style scoped>
  /* Seu estilo CSS personalizado aqui */
  </style>
  