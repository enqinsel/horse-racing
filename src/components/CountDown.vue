<template>
  <div class="mask"></div>
  <div class="circle">
    <img src="../../public/horseHead.png" />
  </div>
</template>

<style scoped>
.mask {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(171, 163, 151, 0.426);
}

img {
  position: fixed;
  left: 50%;
  top: 30%;
  transform: translate(-50%, -50%);
  width: 150px;
}

p {
  position: fixed;
  left: 60%;
  top: 70%;
  transform: translate(-50%, -50%);
  width: 100px;
  font-size: 72px;
}

.circle {
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 100px;
  height: 100px;
  background-color: rgb(211, 149, 14);
  border-radius: 50%;
  animation: blinker 1.2s linear infinite;
}

@keyframes blinker {
  50% {
    opacity: 0.5;
  }
}
</style>
