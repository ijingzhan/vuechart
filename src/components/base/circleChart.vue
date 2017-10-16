<template>
  <div class="circle-main">
    <div id="circle-cont" class="circle-cont"></div>
    <code class="circle-tips">{{count}}<i>%</i></code>
  </div>
</template>

<script>
  import echarts from 'echarts/lib/echarts'
  import 'echarts/lib/chart/pie';

  export default {
    props: ['cData'],
    components: {},
    data() {
      return {
        count:0
      }
    },
    watch:{
      cData(){
        this.drawCircle();
      }
    },
    methods: {
      drawCircle() {
        let circleChart = echarts.init(document.getElementById('circle-cont'));

        circleChart.setOption({
          color: ['#D92B1B', '#f0f0f0'], //每一项对应的颜色
          series: [
            {
              type:'pie',
//              clockwise:false,
              selectedMode:'single',
              selectedOffset:0,
              radius: ['45%', '55%'],
              label: {
                normal: {
                  color:'#333',
                  formatter: '{b} \n {c}只'
                }
              },
              labelLine:{
                normal:{
                  lineStyle:{
                    color:'#333'
                  }
                }
              },
              data:this.cData
            }
          ]
        });

        let selectCount = this.cData[0]['value'];
        this.count = parseFloat(selectCount / parseInt(selectCount + this.cData[1]['value']) * 100).toFixed(2);
      }
    }
  }
</script>

<style scoped lang="less">
  .circle-main {
    width: 100%;
    height: 200px;
    position: relative;
    z-index: 0;
    .circle-cont{
      width: 100%;
      height: 200px;
    }
    .circle-tips{
      position: absolute;
      left: 50%;
      top: 50%;
      z-index: 999;
      margin:-25px 0 0 -10%;
      display: inline-block;
      width: 20%;
      height: 50px;
      font-size: 22px;
      text-align: center;
      line-height: 50px;
      i{
        font-size: 14px;
      }
    }
  }
</style>
