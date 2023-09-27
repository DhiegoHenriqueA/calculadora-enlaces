<template>
    <div class="card-container">
      <div class="card">
        <!-- Cabeçalho do card -->
        <div class="card-header">
          <!-- Abas do card -->
          <div class="tabs">
            <div
              class="tab"
              v-for="(tab, index) in tabs"
              :key="index"
              @click="selectTab(index)"
              :class="{ 'active': selectedIndex === index }"
            >
              {{ tab.label }}
            </div>
          </div>
        </div>
        <!-- Conteúdo da aba selecionada -->
        <div class="card-content">
          <div v-show="selectedIndex === 0">Shannon</div>
          <div v-show="selectedIndex === 1">Nyquist</div>
          <div v-show="selectedIndex === 2">Conversão de mW para dBm</div>
          <div v-show="selectedIndex === 3">EIRP</div>
          <div v-show="selectedIndex === 4">FSLP</div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        tabs: [
          { label: 'Shannon' },
          { label: 'Nyquist' },
          { label: 'Conversão de mW para dBm' },
          { label: 'EIRP' },
          { label: 'FSLP' },
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
  
  <style scoped>
  .card-container {
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-image: url('../assets/home.jpg'); 
    background-size: cover; 
    background-position: center; 
  }
  
  .card {
    background-color: rgba(131, 131, 131, 0.938);
    width: 800px;
    height: 500px;
    border: 1px solid #ccc;
    border-radius: 8px;
    overflow: hidden;
  }
  
  .card-header {
    background-color: #333;
    color: #fff;
  }
  
  .tabs {
    display: flex;
  }
  
  .tab {
    flex: 1;
    text-align: center;
    padding: 10px;
    cursor: pointer;
  }
  
  .tab.active {
    background-color: rgba(177, 173, 173, 0.808);
    color: #333;
  }
  
  .card-content {
    padding: 10px;
  }
  </style>
  