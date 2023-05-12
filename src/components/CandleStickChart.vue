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
import { Prop } from "vue-facing-decorator";
import { Options, Vue } from "vue-class-component";
import VueApexCharts from "vue3-apexcharts";

@Options({
  components: {
    VueApexCharts,
  },
})

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