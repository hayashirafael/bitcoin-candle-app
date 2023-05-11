<template>
  <div>
    <apexchart
      type="candlestick"
      height="350"
      :options="chartOptions"
      :series="series"
    ></apexchart>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "vue-facing-decorator";
import VueApexCharts from "vue3-apexcharts";

@Component({
  components: {
    VueApexCharts,
  },
})
@Component
export default class CandleStickChart extends Vue {
  @Prop()
  candles = [];

  chartOption = {
    chart: {
      type: "candlestick",
      height: 350,
    },
    title: {
      text: "Bitcoin last prices",
      align: "center",
    },
    xaxis: {
      type: "time",
    },
    yaxis: {
      tooltip: {
        enabled: true,
      },
    },
  };
  
  series = [{
    data: this.candles
  }]
}
</script>

<style>
</style>