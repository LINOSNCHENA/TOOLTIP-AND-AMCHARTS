<template>
  <div class="hello" ref="chartdiv">
  </div>
</template>

<script>
import * as am4core from "@amcharts/amcharts4/core";
import * as am4charts from "@amcharts/amcharts4/charts";
import am4themes_animated from "@amcharts/amcharts4/themes/animated";
am4core.useTheme(am4themes_animated);
export default {
  name: 'PembaPlot',
  mounted() {
    let chart = am4core.create(this.$refs.chartdiv, am4charts.XYChart);
    chart.paddingRight = 20;
    let data = [];
    chart.data = [{
      "country": "1-Lithuania",    
      "litres": 501.9,
      "units": 250,
      "date": new Date("2015-03-25"),
      "value": 25,
      "name": "Lithuania",
    }, {
      "country": "2-Czech Republic",
      "litres": 301.9,
      "units": 222,
      "date": new Date("2016-03-25"),
      "value": 29,
      "name": "cz",
    }, {
      "country": "3-Ireland",
      "litres": 201.1,
      "units": 170,
      "date": new Date("2017-03-25"),
      "value": 50,
      "name": "Ireland",
    }, {
      "country": "4-Germany",
      "litres": 165.8,
      "units": 122,
      "date": new Date("2018-03-25"),
      "value": 150,
      "name": "German",
    }, {
      "country": "5-Australia",
      "litres": 139.9,
      "units": 99,
      "date": new Date("2019-03-25"),
      "value": 255,
      "name": "Austithuania",
    }, {
      "country": "6-Austria",
      "litres": 128.3,
      "units": 85,
      "date": new Date("2020-03-25"),
      "value": 350,
      "name": "Austria",
    }, {
      "country": "7-UK",
      "litres": 499,
      "date": new Date("2021-03-25"),
      "value": 270,
      "name": "UK",
    }, {
      "country": "8-Belgium",
      "litres": 60,
      "units": 50,
      "date": new Date("2022-03-25"),
      "value": 290,
      "name": "Belgium",
    }, {
      "country": "9-The Netherlands",
      "litres": 50,
      "units": 42,
      "date": new Date("2023-03-25"),
      "value": 650,
      "name": "Holland",
    }];

    let dateAxis = chart.xAxes.push(new am4charts.DateAxis());
    dateAxis.renderer.grid.template.location = 0;

    let valueAxis = chart.yAxes.push(new am4charts.ValueAxis());
    valueAxis.tooltip.disabled = true;
    valueAxis.renderer.minWidth = 35;

    let series = chart.series.push(new am4charts.LineSeries());
    series.dataFields.dateX = "date";
    series.dataFields.valueY = "value";

    series.tooltipText = "{valueY.value}";
    chart.cursor = new am4charts.XYCursor();

    let scrollbarX = new am4charts.XYChartScrollbar();
    scrollbarX.series.push(series);
    chart.scrollbarX = scrollbarX;
    this.chart = chart;
   console.log("---------------------------data------1----------------")
   console.log(data);
   console.log("---------------------------data------2---------------")
  },

  beforeUnmount() {
    if (this.chart) {
      this.chart.dispose();
    }
  }
}
</script>

<style scoped>
.hello {
  width: 100%;
  height: 500px;
}
</style>
