<template>
  <div>
    <h3>Taxa de Nyquist</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="widthBand">Largura de Banda do Sinal (Hz):</label>
        <input
          type="number"
          id="widthBand"
          v-model="widthBand"
          placeholder="Insira a largura de banda do sinal"
        />
      </div>

      <div class="input-container">
        <label for="modulationMultilevel">Modulação Multinível:</label>
        <input
          type="number"
          id="modulationMultilevel"
          v-model="modulationMultilevel"
          placeholder="Insira a modulação multinível"
        />
      </div>

      <div class="button-container">
        <button class="calcular-button" @click="calculateRateNyquist">
          Calcular Taxa de Nyquist
        </button>
      </div>
    </div>

    <div class="resultado" v-if="rateNyquist !== null">
      <div class="resultado-box">
        <p>
          A Taxa de Nyquist é de
          <span class="result-value">{{ rateNyquist }} bps.</span>
        </p>
      </div>
    </div>
    <div class="resultado" v-if="error">
      <div class="error-box">
        <p>Valor de entrada é inválido.</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      widthBand: null,
      modulationMultilevel: null,
      rateNyquist: null,
      error: false,
    };
  },
  methods: {
    calculateRateNyquist() {
      this.error = false;
      if (
        this.widthBand === null ||
        this.widthBand === "" ||
        this.modulationMultilevel === null ||
        this.modulationMultilevel === ""
      ) {
        this.error = true;
        this.rateNyquist = null;
        return;
      }
      // 2 * largura de banda do sinal (Hz) * Mdodulação multinível .
      this.rateNyquist = 2 * this.widthBand * this.modulationMultilevel;
    },
  },
};
</script>
