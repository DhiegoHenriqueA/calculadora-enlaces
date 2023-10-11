<template>
  <div>
    <h3>Conversão de dBm para mW</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="powerDbm">Potência em dBm:</label>
        <input
          type="number"
          id="powerDbm"
          v-model="powerDbm"
          placeholder="Insira a Potência em dBm:"
        />
      </div>
      <div class="button-container">
        <button class="calcular-button" @click="conversionToMw">
          Converter para mW
        </button>
      </div>
    </div>

    <div class="resultado" v-if="resultMW !== null">
      <div class="resultado-box">
        <p>
          O resultado da conversão é
          <span class="result-value">{{ resultMW }} mW.</span>
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
      powerDbm: null,
      resultMW: null,
      error: false,
    };
  },
  methods: {
    conversionToMw() {
      this.error = false;
      if (this.powerDbm === null || this.powerDbm === "") {
        this.error = true;
        this.resultMW = null;
        return;
      }

      // 10 (Potência em dBm / 10).
      this.resultMW = Math.pow(10, this.powerDbm / 10).toFixed(2);
    },
  },
};
</script>
