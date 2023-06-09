<template>
    <div>
        <h1>这是关于页面</h1>
        <h2 @click="add">{{ count }}</h2>
    </div>
    <div class="box" :style="{width:width+'px'}"></div>
    <button @click="change">click</button>
    <div class="box1"></div>
    <button @click="toggle">display</button>
    <transition name="fade">
    <h1 v-if="isTitle">我又回来了</h1>
        
    </transition>
</template>

<script setup>
import { ref } from "vue";

let count = ref(1)
let color = ref('red')
let width = ref(100)
let isTitle=ref(true)

function toggle() {
    isTitle.value=!isTitle.value
    
}

function change() {
    width.value+=50
}

function add(){
    count.value++
    color.value = Math.random()>0.5?"blue":"red"
}

</script>

<style  scoped>
h2 {
    color:v-bind(color)
}
.box {
    background-color: aqua;
    height: 100px;
    transition: width 1s linear;
}
.box1 {
    width: 30px;
    height: 20px;
    position: relative;
    background: #d88986;
    animation: move 2s linear infinite;
}
@keyframes move {
    0% {left:0px}
    50% {left:500px}
    100% {left: 0;}
}

.fade-enter-active,
.fade-leave-active{
    transition: opacity 0.5s linear;
}
.fade-enter-from,
.fade-leave-to{
    opacity: 0;
}

</style>