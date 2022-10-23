<script setup>
import { ref } from "vue";
import Results from "./Results.vue";

const marginLeft = ref(0)
// const control = ref(false)
const finish = ref(null)

const marginLeft2 = ref(0)
const finish2 = ref(null)

const marginLeft3 = ref(0)
const finish3 = ref(null)

const rdn1 = ref(0)
const rdn2 = ref(0)
const rdn3 = ref(0)



let myInterval;

const startHandler = () => {
    myInterval = setInterval(horseFunk, 1000)
}

const horseFunk = function () {
    horse()
    horse2()
    horse3()
}
const horseOneroad = ref()
const horseTworoad = ref()
const horseThreeroad = ref()

const myResults = ref([])

function horse() {
    if (rdn1.value < (finish.value.offsetLeft - 100)) {
        rdn1.value += (Math.floor(Math.random() * (40 - 20)) + 20) *10
        
        if (rdn1.value >= (finish.value.offsetLeft - 100)) {
            rdn1.value = (finish.value.offsetLeft - 100)

            myResults.value.push("ahmet")
            console.log("winner1");
            marginLeft.value = (finish.value.offsetLeft - 100)
        } else {
            marginLeft.value = rdn1.value
           
            horseOneroad.value = (finish.value.offsetLeft - 100) - marginLeft.value // KALAN YOL

        }
    }
}

function horse2() {
    if (rdn2.value < (finish2.value.offsetLeft - 100)) {
        rdn2.value += (Math.floor(Math.random() * (40 - 20)) + 20) *10
        
        if (rdn2.value >= (finish2.value.offsetLeft - 100)) {
            rdn2.value = (finish2.value.offsetLeft - 100)
            myResults.value.push("ali")
            console.log("winner2");
            marginLeft2.value = (finish2.value.offsetLeft - 100)
        } else {
            marginLeft2.value = rdn2.value
            horseTworoad.value = (finish2.value.offsetLeft - 100) - marginLeft2.value
        }
    }
}
function horse3() {
    if (rdn3.value < (finish3.value.offsetLeft - 100)) {
        rdn3.value += (Math.floor(Math.random() * (40 - 20)) + 20) *10
        
        if (rdn3.value >= (finish3.value.offsetLeft - 100)) {
            rdn3.value = (finish3.value.offsetLeft - 100)
            myResults.value.push("engin")
            console.log("winner3");
            marginLeft3.value = (finish3.value.offsetLeft - 100)
        } else {
            marginLeft3.value = rdn3.value
            horseThreeroad.value = (finish3.value.offsetLeft - 100) - marginLeft3.value
        }
    }
}
</script>

<template>
    <div class="container">
        <div ref="finish" class="final"></div>
        <img src="../../public/horse.gif" :style="`margin-left:${marginLeft}px`">
        <hr>
    </div>
    <div class="container">
        <div ref="finish2" class="final"></div>
        <img src="../../public/horse.gif" :style="`margin-left:${marginLeft2}px`">
        <hr>
    </div>
    <div class="container">
        <div ref="finish3" class="final"></div>
        <img src="../../public/horse.gif" :style="`margin-left:${marginLeft3}px`">
        <hr>
    </div>
    <div>
        <ul>
            <li>horseOneroad: {{ horseOneroad }}</li>
            <li>horseTworoad: {{ horseTworoad }}</li>
            <li>horseThreeroad: {{ horseThreeroad }}</li>
        </ul>
    </div>
    <Results v-for="myResult in myResults" :result="myResult"></Results>
    <button @click="startHandler">Start</button>

</template>

<style scoped>
img {
    width: 100px;
    height: 100px;
    transition: all 2s;
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
</style>