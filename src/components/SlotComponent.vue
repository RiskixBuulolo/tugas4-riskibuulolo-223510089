<template>
  <div class="slot-container" :style="{ backgroundImage: `url(${backgroundImage})` }">
    <h1>Game Information</h1>
    <slot>Disini akan menampilkan info info game yang ada <br>Silahkan tekan
      tombol diatas yang berada ChildComponent
    </slot> <!-- Menampilkan konten yang dimasukkan dari ParentComponent -->
  </div>
</template>

<script>
export default {
  name: 'SlotComponent',
  props: {
    backgroundImage: {
      type: String,
      default: ''
    }
  }
};
</script>

<style scoped>

.slot-container {
  border: 1px solid rgba(204, 204, 204, 0);
  border-radius: 8px;
  padding: 20px;
  margin-top: 20px;
  background-size: cover;
  background-position: center;
  color: white;
}





</style>
