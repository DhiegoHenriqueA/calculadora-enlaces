<template>
  <div>
    <h3>Cálculo FSLP</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="distance">Distancia (km):</label>
        <input
          type="number"
          id="distance"
          v-model="distance"
          placeholder="Insira a distancia"
        />
      </div>

      <div class="input-container">
        <label for="frequency">Frequencia (MHz):</label>
        <input
          type="number"
          id="frequency"
          v-model="frequency"
          placeholder="Insira a Frequencia"
        />
      </div>

      <div class="button-container">
        <button class="calcular-button" @click="calculateFSLP">
          Calcular FSLP
        </button>
      </div>
    </div>

    <div class="resultado" v-if="fslp !== null">
      <div class="resultado-box">
        <p>
          O valor do FSLP é de
          <span class="result-value">{{ fslp }} dB.</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      distance: null,
      frequency: null,
      fslp: null,
    };
  },
  methods: {
    calculateFSLP() {
      if (this.distance > 0 && this.frequency > 0) {
        const fslp =
          32.4 +
          20 * Math.log10(this.distance) +
          20 * Math.log10(this.frequency);
        this.fslp = fslp.toFixed(2);
      } else {
        this.fslp = null;
      }
    },
  },
};
</script>
