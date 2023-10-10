<template>
  <div>
    <h3>Cálculo EIRP</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="transmissionPower">Potência de Transmissão (dBm):</label>
        <input
          type="number"
          id="transmissionPower"
          v-model="transmissionPower"
          placeholder="Insira a Potência de Transmissão"
        />
      </div>

      <div class="input-container">
        <label for="antennaGain">Ganho da Antena (dBi):</label>
        <input
          type="number"
          id="antennaGain"
          v-model="antennaGain"
          placeholder="Insira o Ganho da Antena (dBi):"
        />
      </div>

      <div class="input-container">
        <label for="lossesCable">Perdas no Cabo (dB):</label>
        <input
          type="number"
          id="lossesCable"
          v-model="lossesCable"
          placeholder="Insira a modulação multinível"
        />
      </div>

      <div class="button-container">
        <button class="calcular-button" @click="calculate">
          Calcular EIRP
        </button>
      </div>
    </div>

    <div class="resultado" v-if="EIRPValue !== null">
      <div class="resultado-box">
        <p>
          O valor do EIRP é de
          <span class="result-value">{{ EIRPValue }} dBm.</span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      transmissionPower: null,
      antennaGain: null,
      lossesCable: null,
      EIRPValue: null,
    };
  },
  methods: {
    calculate() {
      this.EIRPValue =
        parseFloat(this.transmissionPower) +
        parseFloat(this.antennaGain) -
        parseFloat(this.lossesCable);
    },
  },
};
</script>
