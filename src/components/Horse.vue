<script setup>
import { ref, onMounted } from "vue";

const marginLeft = ref(0)
const control = ref(false)
const finish =ref(null)

onMounted(() => {
  console.log(finish.value.offsetLeft - 110);
})
let myInterval;

const startHandler = () => {
    myInterval = setInterval(horseFunk, 1000)
    return myInterval
}


let horseFunk = function() {
    marginLeft.value = marginLeft.value + Math.floor((Math.random() * 40)+20);
    console.log(marginLeft.value);
    if (marginLeft.value >= (finish.value.offsetLeft - 100)) {
        marginLeft.value = (finish.value.offsetLeft - 100)
        clearInterval(myInterval)
        if (!control.value) {
            control.value = false;
            setTimeout( () => alert("Winner") , 1000);
            console.log("winner");
        } else {
            marginLeft.value = (finish.value.offsetLeft - 100)
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
    <button @click="startHandler">Start</button>

</template>

<style scoped>
img {
    width: 100px;
    height: 100px;
    transition: all 2s ease;
}

.final {
    width: 10px;
    height: 110px;
    position: relative;
    float: right;
    background-color: black;
}

.container{
    background-color: green;
}
</style>