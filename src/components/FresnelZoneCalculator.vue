<template>
  <div>
    <h3>Cálculo Fresnel Zone</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="dao">Distância do Transmissor até o Obstáculo (m):</label>
        <input
          type="number"
          id="dao"
          v-model="dao"
          placeholder="Insira a Distância do Transmissor até o Obstáculo"
        />
      </div>

      <div class="input-container">
        <label for="dbo">Distância do Receptor até o Obstáculo (m):</label>
        <input
          type="number"
          id="dbo"
          v-model="dbo"
          placeholder="Distância do Receptor até o Obstáculo"
        />
      </div>

      <div class="input-container">
        <label for="frequency">Frequência (MHz):</label>
        <input
          type="number"
          id="frequency"
          v-model="frequency"
          placeholder="Insira as Perdas no Cabo TX"
        />
      </div>

      <div class="input-container">
        <label for="distance"
          >Distância entre Transmissor e Receptor (m):
        </label>
        <input
          type="number"
          id="distance"
          v-model="distance"
          placeholder="Insira a Distância entre Transmissor e Receptor"
        />
      </div>

      <div class="button-container">
        <button class="calcular-button" @click="calculateFresnelZone">
          Calcular Fresnel Zone
        </button>
      </div>
    </div>

    <div class="resultado" v-if="fresnelRadius !== null">
      <div class="resultado-box">
        <p>
          O raio da zona de Fresnel é
          <span class="result-value">{{ fresnelRadius }} metros.</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dao: 0,
      dbo: 0,
      frequency: 0,
      distance: 0,
      fresnelRadius: null,
    };
  },
  methods: {
    calculateFresnelZone() {
      const dao = parseFloat(this.dao);
      const dbo = parseFloat(this.dbo);
      const f = parseFloat(this.frequency);
      const d = parseFloat(this.distance);

      if (!isNaN(dao) && !isNaN(dbo) && !isNaN(f) && !isNaN(d)) {
        const fresnelRadius = 550 * Math.sqrt((dao * dbo) / (d * f));
        this.fresnelRadius = fresnelRadius.toFixed(2);
      } else {
        this.fresnelRadius = null;
      }
    },
  },
};
</script>
