<template>
  <div>
    <h3>Cálculo Fresnel Zone</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="dao">Distância do Transmissor até o Obstáculo (km):</label>
        <input
          type="number"
          id="dao"
          v-model="dao"
          placeholder="Insira a Distância do Transmissor até o Obstáculo"
        />
      </div>

      <div class="input-container">
        <label for="dbo">Distância do Receptor até o Obstáculo (km):</label>
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
          >Distância entre Transmissor e Receptor (km):
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
      dao: null,
      dbo: null,
      frequency: null,
      distance: null,
      fresnelRadius: null,
      error: null,
    };
  },
  methods: {
    calculateFresnelZone() {
      this.error = false;

      const dao = parseFloat(this.dao);
      const dbo = parseFloat(this.dbo);
      const f = parseFloat(this.frequency);
      const d = parseFloat(this.distance);

      if (isNaN(dao) || isNaN(dbo) || isNaN(f) || isNaN(d)) {
        this.error = true;
        this.fresnelRadius = null;
        return;
      }

      //550 * √(DAO * DBO / ( D * f )), onde DAO eDBO são as distâncias do transmissor e receptor até o obstáculo, f é a frequência em MHz e D é a distância entre o transmissor e o receptor.
      const fresnelRadius = 550 * Math.sqrt((dao * dbo) / (d * f));
      this.fresnelRadius = fresnelRadius.toFixed(2);
    },
  },
};
</script>
