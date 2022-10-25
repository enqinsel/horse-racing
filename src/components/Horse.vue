<script setup>
import { ref } from "vue";

const marginLeft = ref(0);
const finish = ref(null);

const marginLeft2 = ref(0);
const finish2 = ref(null);

const marginLeft3 = ref(0);
const finish3 = ref(null);

const rdn1 = ref(0);
const rdn2 = ref(0);
const rdn3 = ref(0);

const show = ref(false);

let myInterval;
let count;

function startHandler() {
  showSecond.value = true
  myInterval = setInterval(horseFunk, 1000);
  count = setInterval(countDown,1000);
}

function restartHandler() {
  location.reload(true);
}

const horseOneroad = ref();
const horseTworoad = ref();
const horseThreeroad = ref();

const horseFunk = function () {
  myFunk(rdn1, finish, marginLeft, "ahmet", horseOneroad);
  myFunk(rdn2, finish2, marginLeft2, "ali", horseTworoad);
  myFunk(rdn3, finish3, marginLeft3, "engin", horseThreeroad);
};

const myResults = ref([]);
const resultCount = ref(0)

function myFunk(rdn, fin, margin, name, road) {
  if (rdn.value < fin.value.offsetLeft - 110) {
    rdn.value += Math.floor(Math.random() * 100 + 20);

    if (rdn.value >= fin.value.offsetLeft - 110) {
      rdn.value = fin.value.offsetLeft - 110;
      myResults.value.push(name);
    
      resultCount.value ++
      console.log(testCount.value);
      if(resultCount.value == 3){
        setTimeout(function isShow() {
              show.value = true;
              showSecond.value = false
            }, 2000);
      }
      margin.value = fin.value.offsetLeft - 110;
    } else {
      margin.value = rdn.value;

      road.value = fin.value.offsetLeft - 110 - margin.value;
    }
  }
}

const second = ref(25)
const showSecond = ref(false)

function countDown()
{
	if(second.value == 0){
        clearInterval(count)
	}
    else{
        setTimeout(()=>second.value --, 1000)
    }
}

</script>

<template>
  <div class="container">
    <div ref="finish" class="final"></div>
    <img src="../../public/horse.gif" :style="`margin-left:${marginLeft}px`" />
    <hr />
  </div>
  <div class="container">
    <div ref="finish2" class="final"></div>
    <img src="../../public/horse.gif" :style="`margin-left:${marginLeft2}px`" />
    <hr />
  </div>
  <div class="container">
    <div ref="finish3" class="final"></div>
    <img src="../../public/horse.gif" :style="`margin-left:${marginLeft3}px`" />
    <hr />
  </div>
  <div>
    <ul>
      <li>ahmet: {{ horseOneroad }}</li>
      <li>ali: {{ horseTworoad }}</li>
      <li>engin: {{ horseThreeroad }}</li>
    </ul>
  </div>
  <div v-if="show" class="result">
    <div class="mask"></div>
    <div class="card">
      <div class="card__label">
        <h1>Sonuçlar</h1>
      </div>
      <div class="card__wrapper">
        <ul>
          <li v-for="myResult in myResults">{{ myResult }}</li>
        </ul>
      </div>
      <button @click="restartHandler">Yeniden Başlat</button>
    </div>
  </div>
  <div v-if="showSecond">
    <p>{{ second }}</p>
  </div>
  <button @click="startHandler">Start</button>
</template>

<style scoped>
img {
  width: 100px;
  height: 100px;
  transition: all 3s;
}

.final {
  width: 10px;
  height: 110px;
  position: relative;
  float: right;
  background-color: black;
}

.container {
  background-color: green;
}

.mask {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(194, 141, 60, 0.5);
}

.card {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  background: rgb(237, 252, 196);
  background: linear-gradient(
    0deg,
    rgba(237, 252, 196, 1) 0%,
    rgba(253, 187, 45, 1) 100%
  );
  border: 1px solid red;
  text-align: center;
  padding: 5px;
  width: 300px;
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
</style>
