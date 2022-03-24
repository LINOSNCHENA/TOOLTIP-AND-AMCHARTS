<template>
  <div>
    <h2>Vue1b- CEZ Graph AMChart</h2>
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>

<style>
/* top scaler */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #50432c;
  margin-top: 90px;
  background-color: rgb(198, 241, 220);
  margin: 0;
  padding: 1;
  font: 9.15 sans-serif;
}
</style>
