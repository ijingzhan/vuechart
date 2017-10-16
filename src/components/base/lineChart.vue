<template>
  <div id="line-chart" class="main">

  </div>
</template>

<script>
  import echarts from 'echarts/lib/echarts'
  import 'echarts/lib/chart/line';

  export default {
    props: ['xData','yData'],
    components: {},
    data() {
      return {

      }
    },
    watch: {
      xData() {
        this.drawCharts()
      },
      yData() {
        this.drawCharts()
      },
    },
    methods: {
      drawCharts() {
        let lineChart = echarts.init(document.getElementById('line-chart'));

        lineChart.setOption({
          xAxis: {
            type: 'category',
            boundaryGap: false,
            axisTick:{
              show:false
            },
            axisLine:{
              lineStyle:{
                color:'#999'
              }
            },
            axisLabel:{
              padding:[3,0,0,0]
            },
            data: this.xData
          },
          yAxis: {
            axisLine:{
              show:false
            },
            axisTick:{
              show:false
            },
            axisLabel:{
              color:'#999'
            }
          },
          series: [
            {
              type: 'line',
              lineStyle: {
                normal: {
                  width: 1,
                  color: '#ce5857'
                }
              },
              areaStyle: {
                normal: {
                  color: '#fad2d3'
                }
              },
              data: this.yData
            }
          ]
        })
      }
    },
    mounted() {
      this.drawCharts();
    }
  }
</script>

<style scoped>
  .main {
    clear: both;
    width: 100%;
    height: 300px;
  }
</style>
