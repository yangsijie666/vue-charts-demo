<template>
  <div>
    <h1>echarts</h1>
    <div id="main" style="width: 100%; height: 400px"></div>
  </div>
</template>

<script>
import * as echarts from 'echarts';

export default {
  data() {
    return {
      data: [],
      charts: "",
    };
  },
  methods: {
    initFakeData() {
      let base = +new Date(1988, 9, 3);
      let oneDay = 24 * 3600 * 1000;
      this.data = [[base, Math.random() * 300]];
      for (let i = 1; i < 20000; i++) {
        let now = new Date((base += oneDay));
        this.data.push([+now, Math.round((Math.random() - 0.5) * 20 + this.data[i - 1][1])]);
      }
    },
    drawChart(id) {
      this.charts = echarts.init(document.getElementById(id));
      this.charts.setOption({
        tooltip: {
          trigger: 'axis',
          position: function (pt) {
            return [pt[0], '10%'];
          }
        },
        title: {
          left: 'center',
          text: 'Large Ara Chart'
        },
        toolbox: {
          feature: {
            dataZoom: {
              yAxisIndex: 'none'
            },
            restore: {},
            saveAsImage: {}
          }
        },
        xAxis: {
          type: 'time',
          boundaryGap: false
        },
        yAxis: {
          type: 'value',
          boundaryGap: [0, '100%']
        },
        dataZoom: [
          {
            type: 'inside',
            start: 0,
            end: 20
          },
          {
            start: 0,
            end: 20
          }
        ],
        series: [
          {
            name: 'Fake Data',
            type: 'line',
            smooth: true,
            symbol: 'none',
            areaStyle: {},
            data: this.data
          }
        ]
      })
    }
  },
  mounted() {
    this.initFakeData();
    this.$nextTick(function () {
      this.drawChart("main");
    });
  },
};
</script>
