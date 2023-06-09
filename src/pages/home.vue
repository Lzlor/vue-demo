<template>
    <div>
        <h1>这是首页</h1>
        <Todolist />
        <div>
            <span>{{ x }},{{ y }}</span>
        </div>
    </div>
</template>

<script setup>
import Todolist from "../components/Todolist.vue"
import { useMouse } from "../utiis/mouse";

let {x,y}=useMouse()

</script>

<style lang="scss" scoped>

</style>