<template>
  <div>
    <!--
        数据可以均参考 js 内 data 对应模拟数据
    -->
    <!--
      x-data  折线图 X 轴数据
      y-data  折线图 Y 轴数据
    -->
    <line-chart :x-data="base.lineDataX" :y-data="base.lineDataY"></line-chart>

    <!--
      lists  数据 [array]
      total  总数
    -->
    <horizontal-bar :lists="base.horizontalData" :total="500"></horizontal-bar>
    <vertical-bar :lists="base.verticalData" :total="390"></vertical-bar>

    <!--
      目前包含 2 个，参见 js 内 data 对应模拟数据说明
    -->
    <circle-chart :c-data="base.cirData"></circle-chart>
  </div>
</template>

<script>
  import lineChart from './base/lineChart.vue'
  import horizontalBar from './base/horizontalBar.vue'
  import verticalBar from './base/verticalBar.vue'
  import circleChart from './base/circleChart.vue'

  export default {
    components: {
      'line-chart': lineChart,
      'horizontal-bar': horizontalBar,
      'vertical-bar': verticalBar,
      'circle-chart': circleChart,
    },
    data() {
      return {
        base: {}
      }
    },
    computed: {},
    created() {
      setTimeout(() => {
          this.base = {
            lineDataX: ['9.11', '9.12', '9.13', '9.14', '9.15', '9.16', '9.17'],
            lineDataY: [50, 78, 130, 180, 200, 230, 260,],
            cirData: [

              {
                value: 1048, name: '宠物狗'
              },  //当前选中数据需要放到索引0，且添加属性 selected:true
              {
                value: 251, name: '宠物猫', selected: true,
                label: {
                  normal: {color: '#E30413'}
                },
                labelLine: {
                  normal: {
                    lineStyle: {color: '#E30413'}
                  }
                }
              },

            ],
            horizontalData: [
              {
                name: '波斯猫',
                count: 120
              },
              {
                name: '大型小猫咪',
                count: 20
              },
              {
                name: '小猫咪',
                count: 120
              },
              {
                name: '野狗小猫咪',
                count: 120
              },
              {
                name: '野狗小猫咪',
                count: 120
              }
            ],
            verticalData: [
              {
                name: '小猫咪',
                count: 10
              },
              {
                name: '大型小猫咪',
                count: 20
              },
              {
                name: '小猫咪',
                count: 120
              },
              {
                name: '野狗小猫咪',
                count: 120
              },
              {
                name: '野狗小猫咪',
                count: 120
              }
            ]
          }
        },
        3000
      )
    },
    methods: {},
  }
</script>

<style scoped>

</style>
