
<template>
  
  <div>
    <h2 @click="toggle">全屏</h2>
    <router-link to="/">首页</router-link>
    <router-link to="/about">关于</router-link>
  </div>
  <router-view></router-view>
</template>
<script setup>
import { useFullscreen } from "@vueuse/core";
const { toggle} = useFullscreen()
</script>

<style scoped>

</style>
