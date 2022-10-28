<script setup>
const props = defineProps(["name", "buttonStyle"]);
const emits = defineEmits(["start", "restart"]);

const clickHandler = () => {
  emits("restart");
  emits("start");
};
</script>

<template>
  <button :class="props.buttonStyle" @click="clickHandler">{{ props.name }}</button>
</template>

<style scoped>
F .restartButton {
  padding: 10px;
  width: 150px;
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-radius: 10px;
  background-color: rgb(86, 223, 13);
  color: white;
  cursor: pointer;
}

.startButton {
  width: 250px;
  height: 80px;
  font-size: 36px;
  margin-left: 40%;
  margin-top: 15px;
  cursor: pointer;
  border: none;
  border-radius: 10px;
  background-color: rgb(86, 223, 13);
  color: white;
}

.startButton:hover {
  transform: scale(1.2);
  transition: all 0.3s ease;
}
</style>
