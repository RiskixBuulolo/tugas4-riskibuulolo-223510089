<template>
  <div class="child-container">
    <h2>Child Component</h2>
    <p>komponen ini berisi fungsi emit</p>
    <button class="child-button" @click="emitData">Send Data to Parent</button>
  </div>
</template>

<script>
export default {
  methods: {
    emitData() {
      const gameNames = ['Super Mario', 'The Legend of Zelda', 'Minecraft', 'Pokémon', 'Grand Theft Auto', 'Fortnite', 'League of Legends', 'Call of Duty', 'FIFA'];
      const randomIndex = Math.floor(Math.random() * gameNames.length);
      const gameName = gameNames[randomIndex];
      this.$emit('data-updated', gameName);
    }
  }
};
</script>

<style scoped>
.child-container {
  margin-top: 20px;
  padding: 20px;
  background-color: #00000000;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  ;
}

.child-button {
  padding: 10px 20px;
  background-color: #007bff;
  color: #ffffff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}

.child-button:hover {
  background-color: #0056b3;
}
</style>
