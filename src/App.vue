<script setup>
import Racing from "./components/Racing.vue";
import Intro from "./components/Intro.vue";
import { ref } from "vue";

const showRacing = ref(false);
const showIntro = ref(true);

const clickHandler = () => {
  showRacing.value = true;
  showIntro.value = false;
};
</script>

<template>
  <Intro v-if="showIntro" @clickButton="clickHandler"></Intro>
  <Racing v-if="showRacing"></Racing>
</template>
