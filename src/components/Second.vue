<script setup>
const props = defineProps(["second", "secondStyle"]);
</script>

<template>
  <div :class="props.secondStyle">
    <p>{{ props.second }}</p>
  </div>
</template>

<style scoped>
.second {
  background-color: rgb(0, 0, 0);
  width: 150px;
  height: 75px;
  font-size: 70px;
  border: 3px solid rgb(102, 101, 101);
  color: red;
  display: flex;
  align-items: center;
  justify-content: space-around;
  position: fixed;
  border-radius: 10px;
  right: 100px;
  bottom: 35px;
}
</style>
