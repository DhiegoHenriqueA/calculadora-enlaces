<template>
  <div>
    <h3>Cálculo RSL</h3>

    <div class="form-container">
      <div class="input-container">
        <label for="powerTransmission">Potência de Transmissão (dBm):</label>
        <input
          type="number"
          id="powerTransmission"
          v-model="powerTransmission"
          placeholder="Insira a Potência de Transmissão"
        />
      </div>

      <div class="input-container">
        <label for="gainAntennaTX">Ganho da Antena TX (dBi): </label>
        <input
          type="number"
          id="gainAntennaTX"
          v-model="gainAntennaTX"
          placeholder="Insira o Ganho da Antena TX"
        />
      </div>

      <div class="input-container">
        <label for="lossesCaboTX">Perdas no Cabo TX (dB): </label>
        <input
          type="number"
          id="lossesCaboTX"
          v-model="lossesCaboTX"
          placeholder="Insira as Perdas no Cabo TX"
        />
      </div>

      <div class="input-container">
        <label for="fslp">FSLP:</label>
        <input
          type="number"
          id="fslp"
          v-model="fslp"
          placeholder="Insira o FSLP"
        />
      </div>

      <div class="input-container">
        <label for="gainAntennaRX">Ganho da Antena RX (dBi): </label>
        <input
          type="number"
          id="gainAntennaRX"
          v-model="gainAntennaRX"
          placeholder="Insira o Ganho da Antena RX"
        />
      </div>

      <div class="input-container">
        <label for="lossesCaboRX">Perdas no Cabo RX (dB) </label>
        <input
          type="number"
          id="lossesCaboRX"
          v-model="lossesCaboRX"
          placeholder="Insira as Perdas no Cabo RX"
        />
      </div>

      <div class="button-container">
        <button class="calcular-button" @click="calculateRSL">
          Calcular RSL
        </button>
      </div>
    </div>

    <div class="resultado" v-if="rsl !== null">
      <div class="resultado-box">
        <p>
          Nível de Sinal Recebido RSL é de
          <span class="result-value">{{ rsl }} dBm.</span>
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
      powerTransmission: null,
      gainAntennaTX: null,
      lossesCaboTX: null,
      gainAntennaRX: null,
      lossesCaboRX: null,
      fslp: null,
      rsl: null,
      error: false,
    };
  },
  methods: {
    calculateRSL() {
      this.error = false;

      if (
        !this.powerTransmission ||
        !this.gainAntennaTX ||
        !this.lossesCaboTX ||
        !this.gainAntennaRX ||
        !this.lossesCaboRX
      ) {
        this.error = true;
        this.rsl = null;
        return;
      }

      // Potência de Transmissão (dBm) + Ganho da Antena TX (dBi) - Perdas no Cabo TX (dB) - Free Space Loss Path  + Ganho da Antena RX (dBi) - Perdas no Cabo RX (dB)
      const rsl =
        parseFloat(this.powerTransmission) +
        parseFloat(this.gainAntennaTX) -
        parseFloat(this.lossesCaboTX) -
        parseFloat(this.fslp) +
        parseFloat(this.gainAntennaRX) -
        parseFloat(this.lossesCaboRX);

      this.rsl = rsl.toFixed(2);
    },
  },
};
</script>
