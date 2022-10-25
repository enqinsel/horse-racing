<script setup>
import { ref } from "vue";

const marginLeft = ref(0);
const finish = ref(null);

const marginLeft2 = ref(0);
const finish2 = ref(null);

const marginLeft3 = ref(0);
const finish3 = ref(null);

const marginLeft4 = ref(0);
const finish4 = ref(null);

const marginLeft5 = ref(0);
const finish5 = ref(null);

const marginLeft6 = ref(0);
const finish6 = ref(null);

const marginLeft7 = ref(0);
const finish7 = ref(null);

const marginLeft8 = ref(0);
const finish8 = ref(null);

const rdn1 = ref(0);
const rdn2 = ref(0);
const rdn3 = ref(0);
const rdn4 = ref(0);
const rdn5 = ref(0);
const rdn6 = ref(0);
const rdn7 = ref(0);
const rdn8 = ref(0);

const show = ref(false);

let myInterval;
let count;

function startHandler() {
  showSecond.value = true;
  myInterval = setInterval(horseFunk, 1000);
  count = setInterval(countDown, 1000);
}

function restartHandler() {
  location.reload(true);
}

const horseOneroad = ref();
const horseTworoad = ref();
const horseThreeroad = ref();
const horseFourroad = ref();
const horseFiveroad = ref();
const horseSixroad = ref();
const horseSevenroad = ref();
const horseEightroad = ref();

const horseFunk = function () {
  myFunk(rdn1, finish, marginLeft, "ahmet", horseOneroad);
  myFunk(rdn2, finish2, marginLeft2, "ali", horseTworoad);
  myFunk(rdn3, finish3, marginLeft3, "engin", horseThreeroad);
  myFunk(rdn4, finish4, marginLeft4, "tarik", horseFourroad);
  myFunk(rdn5, finish5, marginLeft5, "selim", horseFiveroad);
  myFunk(rdn6, finish6, marginLeft6, "mehmet", horseSixroad);
  myFunk(rdn7, finish7, marginLeft7, "arif", horseSevenroad);
  myFunk(rdn8, finish8, marginLeft8, "ege", horseEightroad);
};

const myResults = ref([]);
const resultCount = ref(0);

function myFunk(rdn, fin, margin, name, road) {
  if (rdn.value < fin.value.offsetLeft - 50) {
    rdn.value += Math.floor(Math.random() * 100 + 20);

    if (rdn.value >= fin.value.offsetLeft - 50) {
      rdn.value = fin.value.offsetLeft - 50;
      myResults.value.push(name);
      resultCount.value++;
      if (resultCount.value == 8) {
        setTimeout(function isShow() {
          show.value = true;
          showSecond.value = false;
        }, 2000);
      }
      margin.value = fin.value.offsetLeft - 50;
    } else {
      margin.value = rdn.value;

      road.value = fin.value.offsetLeft - 50 - margin.value;
    }
  }
}

const second = ref(30);
const showSecond = ref(false);

function countDown() {
  if (second.value == 0) {
    clearInterval(count);
  } else {
    setTimeout(() => second.value--, 1000);
  }
}
</script>

<template>
  <div class="body">
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
    <div class="container">
      <div ref="finish4" class="final"></div>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeft4}px`" />
      <hr />
    </div>
    <div class="container">
      <div ref="finish5" class="final"></div>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeft5}px`" />
      <hr />
    </div>
    <div class="container">
      <div ref="finish6" class="final"></div>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeft6}px`" />
      <hr />
    </div>
    <div class="container">
      <div ref="finish7" class="final"></div>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeft7}px`" />
      <hr />
    </div>
    <div class="bottom-container">
      <div ref="finish8" class="final"></div>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeft8}px`" />
    </div>
    <hr class="barrier" />
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
  </div>
</template>

<style scoped>
img {
  width: 50px;
  height: 50px;
  transition: all 3s;
}

.final {
  width: 10px;
  height: 70px;
  position: relative;
  float: right;
  background-color: rgb(255, 0, 0);
}

.container {
  background-color: green;
  box-shadow: 0px 10px 0px 20px #754545;
}

.bottom-container {
  background-color: green;
  box-shadow: 0px -10px 0px 0px #754545;
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

.barrier {
  font-size: 0.3em;
  background: linear-gradient(315deg, rgb(255, 0, 0) 25%, transparent 25%) -3em 0,
    linear-gradient(45deg, rgb(255, 0, 0) 25%, transparent 25%) -3em 0,
    linear-gradient(135deg, #333 25%, transparent 25%),
    linear-gradient(225deg, #333 25%, transparent 25%);
  background-size: 7em 100%;
  background-color: #754545;
  height: 7em;
  border: none;
  margin: 0;
  width: 100%;
  position: relative;
  top: -17px;
}
</style>
