<script setup>
const emits = defineEmits(["clickButton"]);

const clickHandler = () => {
  emits("clickButton");
};
</script>

<template>
  <div>
    <button @click="clickHandler">İlerle</button>
    <img src="../../public/introHorse.gif" class="horse" />
    <img src="../../public/intro.svg" style="width: 100%" />
  </div>
</template>

<style scoped>
.horse {
  position: fixed;
  width: 550px;
  top: 30%;
  left: 32%;
}

button {
  position: fixed;
  top: 90%;
  left: 43%;
  width: 150px;
  border: none;
  padding: 5px;
  font-size: 36px;
  font-family: "Grenze Gotisch", cursive;
  background-color: #6bb1dd;
  border-radius: 10px;
  cursor: pointer;
}

button:hover {
  transform: scale(1.2);
}

</style>
