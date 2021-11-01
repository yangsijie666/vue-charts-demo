<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <MixChart/>
    <EChart/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import MixChart from "@/components/MixChart";
import EChart from "@/components/EChartDemo";

import VueCompositionAPI from '@vue/composition-api'
import Vue from "vue";

Vue.use(VueCompositionAPI)

export default {
  name: 'App',
  components: {
    EChart,
    HelloWorld,
    MixChart
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
