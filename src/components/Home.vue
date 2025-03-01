<template>
  <div class="home" v-if="isOutEnv" style="background: deepskyblue">
    <h2>Home-Out-System</h2>
  </div>
  <div class="home" v-else style="background: red">
    <h2>Home-Inner-System</h2>
  </div>
  <div style="text-align: center">
    <button @click="clickBtn">点击</button>
  </div>

</template>

<script setup lang="ts" name="Home">
import {computed} from "vue";

const isOutEnv = computed(() => import.meta.env?.VITE_ENV.includes('out'))
function clickBtn() {
  console.log('%VITE_ENV%')
  console.log('import.meta.env?.VITE_ENV', import.meta.env?.VITE_ENV)
  console.log('isOutEnv', isOutEnv)
  if (isOutEnv.value) {
    console.log('执行外部系统点击逻辑')
  } else {
    console.log('执行内部系统点击逻辑')
  }
}

</script>

<style scoped>
  .home {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 20%;
  }
</style>