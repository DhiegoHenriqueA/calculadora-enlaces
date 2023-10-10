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
  </div>
</template>

<script>
export default {
  data() {
    return {
      powerMw: null,
      resultDbm: null,
    };
  },
  methods: {
    conversionToDbm() {
      if (this.powerMw !== null) {
        this.resultDbm = 10 * Math.log10(this.powerMw);
      }
    },
  },
};
</script>
