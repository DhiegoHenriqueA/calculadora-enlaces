<template>
  <div>
    <h3>Capacidade Máxima de Canal</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="widthBand">Largura de Banda (Hz):</label>
        <input
          type="number"
          id="widthBand"
          v-model="widthBand"
          placeholder="Insira a largura de banda"
        />
      </div>

      <div class="input-container">
        <label for="signalNoise">Relação Sinal-Ruído (dB):</label>
        <input
          type="number"
          id="signalNoise"
          v-model="signalNoise"
          placeholder="Insira a relação sinal-ruído"
        />
      </div>

      <div class="button-container">
        <button class="calcular-button" @click="calcularCapacidade">
          Calcular Capacidade
        </button>
      </div>
    </div>

    <div class="resultado" v-if="capacity !== null">
      <div class="resultado-box">
        <p>
          A capacidade máxima do canal é
          <span class="result-value">{{ capacity.toFixed(2) }} bps</span>.
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
      signalNoise: null,
      capacity: null,
      error: false,
    };
  },
  methods: {
    // largura de banda (Hz) * log2(1 + Sinal-Ruído)
    calcularCapacidade() {
      this.error = false;
      if (
        this.widthBand === null ||
        this.widthBand === "" ||
        this.signalNoise === null ||
        this.signalNoise === ""
      ) {
        this.error = true;
        this.capacity = null;
        return;
      }
      // Converter a relação sinal-ruído de decibéis para uma relação linear
      const signalNoiseLinear = Math.pow(10, this.signalNoise / 10);

      // Calcular a capacidade máxima do canal em bps
      this.capacity = this.widthBand * Math.log2(1 + signalNoiseLinear);
    },
  },
};
</script>
