<template>
  <div>
    <h3>Conversão de mW para dBm</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="powerMw">Potência em mW:</label>
        <input
          type="number"
          id="powerMw"
          v-model="powerMw"
          placeholder="Insira a Potência em mW:"
        />
      </div>
      <div class="button-container">
        <button class="calcular-button" @click="conversionToDbm">
          Converter para dBm
        </button>
      </div>
    </div>

    <div class="resultado" v-if="resultDbm !== null">
      <div class="resultado-box">
        <p>
          O resultado da conversão é
          <span class="result-value">{{ resultDbm }} dBm.</span>
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
      powerMw: null,
      resultDbm: null,
      error: false,
    };
  },
  methods: {
    conversionToDbm() {
      this.error = false;
      if (this.powerMw === null || this.powerMw === "") {
        this.error = true;
        this.resultDbm = null;
        return;
      }

      // 10 * log10(Potência em mW).
      this.resultDbm = (10 * Math.log10(this.powerMw)).toFixed(2);
    },
  },
};
</script>
