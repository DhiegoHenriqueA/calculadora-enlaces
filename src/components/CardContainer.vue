<template>
  <div class="card-container">
    <div class="card">
      <div class="card-header">
        <div class="tabs">
          <div
            class="tab"
            v-for="(tab, index) in tabs"
            :key="index"
            @click="selectTab(index)"
            :class="{ active: selectedIndex === index }"
          >
            {{ tab.label }}
          </div>
        </div>
      </div>
      <div class="card-content">
        <div v-show="selectedIndex === 0">
          <ShannonCalculator />
        </div>
        <div v-show="selectedIndex === 1">
          <NyquistCalculator />
        </div>
        <div v-show="selectedIndex === 2">
          <ConversionToDbmCalculator />
        </div>
        <div v-show="selectedIndex === 3">
          <ConversionToMwCalculator />
        </div>
        <div v-show="selectedIndex === 4">
          <EIRPCalculator />
        </div>
        <div v-show="selectedIndex === 5">
          <FSLPCalculator />
        </div>
        <div v-show="selectedIndex === 6">
          <RSLCalculator />
        </div>
        <div v-show="selectedIndex === 7">
          <FresnelZoneCalculator />
        </div>
      </div>
      <div class="footer">
        by Dhiego Henrique Azevedo | @2023 | IFC Araquari
      </div>
    </div>
  </div>
</template>

<script>
import ShannonCalculator from "./ShannonCalculator.vue";
import NyquistCalculator from "./NyquistCalculator.vue";
import ConversionToDbmCalculator from "./ConversionToDbmCalculator.vue";
import ConversionToMwCalculator from "./ConversionToMwCalculator.vue";
import EIRPCalculator from "./EIRPCalculator.vue";
import FSLPCalculator from "./FSLPCalculator.vue";
import RSLCalculator from "./RSLCalculator.vue";
import FresnelZoneCalculator from "./FresnelZoneCalculator.vue";

export default {
  components: {
    ShannonCalculator,
    NyquistCalculator,
    ConversionToDbmCalculator,
    ConversionToMwCalculator,
    EIRPCalculator,
    FSLPCalculator,
    RSLCalculator,
    FresnelZoneCalculator,
  },
  data() {
    return {
      tabs: [
        { label: "Shannon" },
        { label: "Nyquist" },
        { label: "mW para dBm" },
        { label: "dBm para mW" },

        { label: "EIRP" },
        { label: "FSLP" },
        { label: "RSL" },
        { label: "Fresnel zone" },
      ],
      selectedIndex: 0,
    };
  },
  methods: {
    selectTab(index) {
      this.selectedIndex = index;
    },
  },
};
</script>

<style>
.footer {
  text-align: center;
  padding: 16px;
  font-size: 14px;
  color: rgb(77, 76, 76);
}
.card-container {
  margin: 0;
  padding: 0;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-image: url("../assets/home.jpg");
  background-size: cover;
  background-position: center;
}

.card {
  background-color: #f4f4f4;
  width: 840px;
  min-height: 260px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.5);
  border-radius: 8px;
  overflow: hidden;
}

.card-header {
  background-color: #075488;
  color: #fff;
}

.tabs {
  display: flex;
}

.tab {
  flex: 1;
  text-align: center;
  padding: 15px;
  cursor: pointer;
}

.tab.active {
  background-color: #467da1fb;
}

.card-content {
  text-align: center;
  margin: 0 auto;
  padding: 50px 180px 80px 180px;
  max-width: 340px;
  background-color: #f4f4f4;
}

body {
  font-family: Arial, sans-serif;
}

h3 {
  margin-top: 0;
}

.form-container {
  text-align: left;
  margin-top: 20px;
}

.input-container {
  margin-bottom: 20px;
}

.input-container label {
  display: block;
}

.input-container input {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.button-container {
  text-align: center;
}

.calcular-button {
  font-size: 14px;
  background-color: #075488;
  color: white;
  border: none;
  border-radius: 5px;
  padding: 12px 60px;
  cursor: pointer;
}

.resultado {
  font-size: 14px;
  margin-top: 20px;
}

.resultado-box {
  background-color: #afd6f0bc;
  border-radius: 5px;
  padding: 10px;
}

.error-box {
  background-color: #e09292bc;
  border-radius: 5px;
  padding: 10px;
}

.result-value {
  font-weight: bold;
  font-size: 16px;
}
</style>
