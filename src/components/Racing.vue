<script setup>
import { ref, computed } from "vue";
import ButtonComp from "./ButtonComp.vue";
import Second from "./Second.vue";

const marginLeftAyabakan = ref(0);
const finishAyabakan = ref(null);

const marginLeftYavuzhan = ref(0);
const finishYavuzhan = ref(null);

const marginLeftKarayel = ref(0);
const finishKarayel = ref(null);

const marginLeftSariyerli = ref(0);
const finishSariyerli = ref(null);

const marginLeftSahbatur = ref(0);
const finishSahbatur = ref(null);

const marginLeftTunca = ref(0);
const finishTunca = ref(null);

const marginLeftToraman = ref(0);
const finishToraman = ref(null);

const marginLeftBoldpilot = ref(0);
const finishBoldpilot = ref(null);

const fastAyabakan = ref(null);
const fastYavuzhan = ref(null);
const fastKarayel = ref(null);
const fastSariyerli = ref(null);
const fastSahbatur = ref(null);
const fastTunca = ref(null);
const fastToraman = ref(null);
const fastBoldpilot = ref(null);

const horseOneroad = ref(0);
const horseTworoad = ref(0);
const horseThreeroad = ref(0);
const horseFourroad = ref(0);
const horseFiveroad = ref(0);
const horseSixroad = ref(0);
const horseSevenroad = ref(0);
const horseEightroad = ref(0);

const showResult = ref(false);
const showRoad = ref(false);
const showStart = ref(true);
const showSecond = ref(false);

const myResults = ref([]);
const resultCount = ref(0);
const second = ref(0);

let myInterval;
let count;


function startHandler() {
  showSecond.value = true;
  myInterval = setInterval(myHorses, 1000);
  count = setInterval(countDown, 1000);
  showRoad.value = true;
  showStart.value = false;
}

function restartHandler() {
  location.reload(true);
}

const arrayRoads = ref([
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

const myHorses = function () {
  runHorse(fastAyabakan, finishAyabakan, marginLeftAyabakan,  arrayRoads.value[0]);
  runHorse(fastYavuzhan, finishYavuzhan, marginLeftYavuzhan,  arrayRoads.value[1]);
  runHorse(fastKarayel, finishKarayel, marginLeftKarayel,  arrayRoads.value[2]);
  runHorse(fastSariyerli, finishSariyerli, marginLeftSariyerli,  arrayRoads.value[3]);
  runHorse(fastSahbatur, finishSahbatur, marginLeftSahbatur,  arrayRoads.value[4]);
  runHorse(fastTunca, finishTunca, marginLeftTunca,  arrayRoads.value[5]);
  runHorse(fastToraman, finishToraman, marginLeftToraman,  arrayRoads.value[6]);
  runHorse(fastBoldpilot, finishBoldpilot, marginLeftBoldpilot,  arrayRoads.value[7]);
};


function runHorse(fast, finish, marginLeft, road) {
  if (fast.value < finish.value.offsetLeft - 50) {
    fast.value += Math.floor(Math.random() * 100 + 20);
    if (fast.value >= finish.value.offsetLeft - 50) {
      fast.value = finish.value.offsetLeft - 50;
      myResults.value = array.value
      resultCount.value++;
      if (resultCount.value === 8) {
        clearInterval(count)
        setTimeout(function isShow() {
          showResult.value = true;
          showRoad.value = false;
        }, 2000);
      }
      marginLeft.value = finish.value.offsetLeft - 50;
    } else {
      marginLeft.value = fast.value;
    }
    road.value = finish.value.offsetLeft - 50 - marginLeft.value;
  }
}

function countDown() {
  setTimeout(() => second.value++, 1000);
}
</script>

<template>
  <div class="body">
    <div class="container">
      <div ref="finishAyabakan" class="final"></div>
      <img class="finishFlag" src="../../public/finish.svg" />
      <p class="lane">1 <span>Ayabakan</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftAyabakan}px`" style="filter: saturate(2)" />
      <hr />
    </div>
    <div class="container">
      <div ref="finishYavuzhan" class="final"></div>
      <p class="lane">2 <span>Yavuzhan</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftYavuzhan}px`" style="filter: sepia(5)" />
      <hr />
    </div>
    <div class="container">
      <div ref="finishKarayel" class="final"></div>
      <p class="lane">3 <span>Karayel</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftKarayel}px`" style="filter: hue-rotate(30deg)" />
      <hr />
    </div>
    <div class="container">
      <div ref="finishSariyerli" class="final"></div>
      <p class="lane">4 <span>Sarıyerli</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftSariyerli}px`" style="filter: brightness(0.7)" />
      <hr />
    </div>
    <div class="container">
      <div ref="finishSahbatur" class="final"></div>
      <p class="lane">5 <span>Şahbatur</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftSahbatur}px`" style="filter: contrast(100%)" />
      <hr />
    </div>
    <div class="container">
      <div ref="finishTunca" class="final"></div>
      <p class="lane">6 <span>Tunca</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftTunca}px`" style="filter: contrast(200%)" />
      <hr />
    </div>
    <div class="container">
      <div ref="finishToraman" class="final"></div>
      <p class="lane">7 <span>Toraman</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftToraman}px`" style="filter: brightness(0.5)" />
      <hr />
    </div>
    <div class="bottom-container">
      <div ref="finishBoldpilot" class="final"></div>
      <p class="lane">8 <span>Bold Pilot</span></p>
      <img src="../../public/horse.gif" :style="`margin-left:${marginLeftBoldpilot}px`" style="filter: brightness(1.5)" />
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
    <div v-if="showResult" class="result">
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
        <ButtonComp @restart="restartHandler" name="Yeniden Başlat" buttonStyle="restartButton"></ButtonComp>
      </div>
    </div>
    <Second secondStyle="second" :second="second" v-if="showSecond"></Second>
  </div>
  <ButtonComp name="Başlat" buttonStyle="startButton" @start="startHandler" v-if="showStart"></ButtonComp>
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
/* .second {
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
} */

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