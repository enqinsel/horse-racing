<script setup>
import { ref, computed } from "vue";

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

const rdn1 = ref(null);
const rdn2 = ref(null);
const rdn3 = ref(null);
const rdn4 = ref(null);
const rdn5 = ref(null);
const rdn6 = ref(null);
const rdn7 = ref(null);
const rdn8 = ref(null);

const show = ref(false);

let myInterval;
let count;

const showRoad = ref(false);
const showStart = ref(true);

function startHandler() {
  showSecond.value = true;
  myInterval = setInterval(horseFunk, 1000);
  count = setInterval(countDown, 1000);
  showRoad.value = true;
  showStart.value = false;
  
}

function restartHandler() {
  location.reload(true);
}

const horseOneroad = ref(0);
const horseTworoad = ref(0);
const horseThreeroad = ref(0);
const horseFourroad = ref(0);
const horseFiveroad = ref(0);
const horseSixroad = ref(0);
const horseSevenroad = ref(0);
const horseEightroad = ref(0);

const array2 = ref([
  horseOneroad,horseTworoad,horseThreeroad,horseFourroad,horseFiveroad,horseSixroad,horseSevenroad,horseEightroad
])

const array = ref([
  { 
    name: "Ayabakan",
    roads: horseOneroad,
  },
  {
    name: "Yavuzhan",
    roads: horseTworoad,
  },
  {
    name: "Karayel",
    roads: horseThreeroad,
  },
  {
    name: "Sarıyerli",
    roads: horseFourroad,
  },
  {
    name: "Şahbatur",
    roads: horseFiveroad,
  },
  {
    name: "Tunca",
    roads: horseSixroad,
  },
  {
    name: "Toraman",
    roads: horseSevenroad,
  },
  {
    name: "Bold Pilot",
    roads: horseEightroad,
  },
]);

const test = computed(()=>{
  let sorting = array.value.sort((a,b) =>  a.roads - b.roads);
  return sorting
}) 

const horseFunk = function () {
  myFunk(rdn1, finish, marginLeft,  array2.value[0]);
  myFunk(rdn2, finish2, marginLeft2,  array2.value[1]);
  myFunk(rdn3, finish3, marginLeft3,  array2.value[2]);
  myFunk(rdn4, finish4, marginLeft4,  array2.value[3]);
  myFunk(rdn5, finish5, marginLeft5,  array2.value[4]);
  myFunk(rdn6, finish6, marginLeft6,  array2.value[5]);
  myFunk(rdn7, finish7, marginLeft7,  array2.value[6]);
  myFunk(rdn8, finish8, marginLeft8,  array2.value[7]);
};

const myResults = ref([]);
const resultCount = ref(0);

function myFunk(rdn, fin, margin, road) {
  if (rdn.value < fin.value.offsetLeft - 50) {
    rdn.value += Math.floor(Math.random() * 100 + 20);
    if (rdn.value >= fin.value.offsetLeft - 50) {
      rdn.value = fin.value.offsetLeft - 50;
      myResults.value = array.value
      resultCount.value++;
      if (resultCount.value === 8) {
        setTimeout(function isShow() {
          show.value = true;
          showSecond.value = false;
          showRoad.value = true;
        }, 2000);
      }
      margin.value = fin.value.offsetLeft - 50;
    } else {
      margin.value = rdn.value;
    }
    road.value = fin.value.offsetLeft - 50 - margin.value;
  }
}

const second = ref(0);
const showSecond = ref(false);

function countDown() {
  setTimeout(() => second.value++, 1000);
}
</script>

<template>
  <div class="body">
    <div class="container">
      <div ref="finish" class="final"></div>
      <img class="finishFlag" src="../../public/finish.svg" />
      <p class="lane">1 <span>Ayabakan</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft}px`"
        style="filter: saturate(2)"
      />
      <hr />
    </div>
    <div class="container">
      <div ref="finish2" class="final"></div>
      <p class="lane">2 <span>Yavuzhan</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft2}px`"
        style="filter: sepia(5)"
      />
      <hr />
    </div>
    <div class="container">
      <div ref="finish3" class="final"></div>
      <p class="lane">3 <span>Karayel</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft3}px`"
        style="filter: hue-rotate(30deg)"
      />
      <hr />
    </div>
    <div class="container">
      <div ref="finish4" class="final"></div>
      <p class="lane">4 <span>Sarıyerli</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft4}px`"
        style="filter: brightness(0.7)"
      />
      <hr />
    </div>
    <div class="container">
      <div ref="finish5" class="final"></div>
      <p class="lane">5 <span>Şahbatur</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft5}px`"
        style="filter: contrast(100%)"
      />
      <hr />
    </div>
    <div class="container">
      <div ref="finish6" class="final"></div>
      <p class="lane">6 <span>Tunca</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft6}px`"
        style="filter: contrast(200%)"
      />
      <hr />
    </div>
    <div class="container">
      <div ref="finish7" class="final"></div>
      <p class="lane">7 <span>Toraman</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft7}px`"
        style="filter: brightness(0.5)"
      />
      <hr />
    </div>
    <div class="bottom-container">
      <div ref="finish8" class="final"></div>
      <p class="lane">8 <span>Bold Pilot</span></p>
      <img
        src="../../public/horse.gif"
        :style="`margin-left:${marginLeft8}px`"
        style="filter: brightness(1.5)"
      />
    </div>
    <hr class="barrier" />
    <div v-if="showRoad" class="road">
          <div>
            <ul class="momentTable">
              <li class="rankColor" v-for="i in 3">{{ i }}</li>
              <li v-for="i in 5">{{ i + 3 }}</li>
            </ul>
            <hr class="line_moment ">
          </div>
      <div><span v-for="item in test" style="margin-left:45px;">{{item.name}}</span></div>
    </div>
    <div v-if="show" class="result">
      <div class="mask"></div>
      <div class="card">
        <div class="card__label">
          <h1>Sonuçlar</h1>
          <div class="label__line"></div>
        </div>
        <div class="card__wrapper">
          <ul>
            <li class="rankColor resultTable" v-for="i in 3">{{ i }}</li>
            <li  class="resultTable" v-for="i in 5">{{ i + 3 }}</li>
          </ul>
          <ul>
            <li class="resultTable" v-for="myResult in myResults">{{ myResult.name }}</li>
          </ul>
        </div>
        <button class="restartButton" @click="restartHandler">Yeniden Başlat</button>
      </div>
    </div>
    <div class="second" v-if="showSecond">
      <p>{{ second }}</p>
    </div>
  </div>
  <button v-if="showStart" class="startButton" @click="startHandler">Start</button>
</template>

<style scoped>
.line_moment{
  background-color: black;
  height:1.5px;
  border:0px;
}
.momentTable{
  display: flex;
  align-items: flex-start;
  gap: 100px;
  margin-left: 70px;
}

span {
  font-size: 18px;
  opacity: 0.8;
}
.finishFlag {
  width: 50px;
  height: 545px;
  position: fixed;
  top: 0px;
  right: 10px;
  opacity: 0.7;
}
.lane {
  display: inline;
  font-size: 50px;
  position: fixed;
  left: 50px;
  color: #fbe200a3;
}
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
.road {
  background: rgb(237, 252, 196);
  background: linear-gradient(0deg, #c56b05 0%, #e08a26 100%);
  border: 1px solid red;
  padding: 10px;
  width: auto;
  margin-left: 40%;
  margin-top: 50px;
  transform: translate(-50%, -50%);
}


.restartButton {
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
.rankColor {
  color: rgb(246, 255, 0);
}
.label__line {
  width: 100%;
  height: 2px;
  background-color: rgb(0, 0, 0);
  margin: 5px;
}

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
  box-shadow: 0px -10px 0px 0px #ff0000;
}

.container {
  background-color: green;
  box-shadow: 0px 10px 0px 20px #8b4513;
}

.bottom-container {
  background-color: green;
  box-shadow: 0px -10px 0px 0px #8b4513;
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
  background-color: #e19135;
  border: 1px solid red;
  text-align: center;
  padding: 15px;
  width: 300px;
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}

.card__wrapper {
  padding: 10px;
  width: auto;
  display: grid;
  grid-template-columns: repeat(2, 2fr);
}

.resultTable {
  padding: 10px;
  border-bottom: 1px solid rgb(0, 0, 0);
}

.barrier {
  font-size: 0.3em;
  background: linear-gradient(315deg, #333 25%, transparent 25%) -3em 0,
    linear-gradient(45deg, #333 25%, transparent 25%) -3em 0,
    linear-gradient(135deg, #333 25%, transparent 25%),
    linear-gradient(225deg, #333 25%, transparent 25%);
  background-size: 7em 100%;
  background-color: #6c3711;
  height: 7em;
  border: none;
  margin: 0;
  width: 100%;
  position: relative;
  top: -17px;
}
</style>
