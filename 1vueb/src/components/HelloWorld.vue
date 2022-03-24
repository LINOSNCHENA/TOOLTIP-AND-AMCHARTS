<template>
  <div class="hello" ref="chartdiv2"></div>
</template>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";
am4core.useTheme(am4themes_animated);

export default {
  name: "HelloWorld2",
  props: {
    msg: String,
  },
  mounted() {
    let chart = am4core.create(this.$refs.chartdiv2, am4charts.XYChart);
    chart.paddingRight = 20;
  
    let data = [];
    let visits = 11;

    for (let i = 1; i < 366; i++) {
      visits += Math.round((Math.random() < 0.5 ? 1 : -1) * Math.random() * 10);

      data.push({
        date: new Date(2022, 0, i),
        name: "name" + i,
        value: visits,
      });
    }

    chart.data = data;

    let dateAxis = chart.xAxes.push(new am4charts.DateAxis());
    dateAxis.renderer.grid.template.location = 0;

    let valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
    valueAxis.tooltip.disabled = false;
    valueAxis.renderer.minWidth = 15;

    let series = chart.series.push(new am4charts.LineSeries());
    series.dataFields.dateX = "date";
    series.dataFields.valueY = "value";
    series.tooltipText = "{valueY.value}";

    series.propertyFields.stroke = "red"; /// red
    series.propertyFields.fill = "orange";
    series.strokeWidth = 2;
    series.stroke = am4core.color("#ff0000"); // red

    chart.cursor = new am4charts.XYCursor();

    let scrollbarX = new am4charts.XYChartScrollbar();
    scrollbarX.series.push(series);
    chart.scrollbarX = scrollbarX;

    this.chart = chart;
  },

  beforeUnmunt() {
    if (this.chart) {
      this.chart.dispose();
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.hello {
  width: 99%;
  height: 899px;
  margin: 0 auto;
  margin-top: 10px;
  background-color: rgb(28, 250, 246);
  font-size: 1.3rem;
  line-height: 1.31579;
  font: 1.15 sans-serif;
}
h3 {
  margin: 40px 0 0;
  background-color: rgb(194, 28, 250);
}
ul {
  list-style-type: none;
  padding: 0;
  background-color: rgb(28, 250, 220);
}
li {
  display: inline-block;
  margin: 0 10px;
  background-color: rgb(250, 246, 28);
}
a {
  color: #b9427d;
  background-color: rgb(28, 250, 157);
}
</style>
