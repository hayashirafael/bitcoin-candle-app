<template>
  <div>
    <apexchart
      type="candlestick"
      height="350"
      :options="chartOption"
      :series="series"
    ></apexchart>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from 'vue-facing-decorator'
import VueApexCharts from "vue3-apexcharts";

@Component({
  components: {
    VueApexCharts,
  },
})
export default class CandleStickChart extends Vue {
    @Prop({default: []}) candles!:[]

  mounted() {
    console.log(this.candles)
  }

  chartOption = {
    chart: {
      type: "candlestick",
      height: 350,
    },
    title: {
      text: "Bitcoin last prices",
      align: "left",
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
  
  get series() {
    const series = [{
        data: this.candles
    }]
    return series
  }
}
</script>

<style>
</style>