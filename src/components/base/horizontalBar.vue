<template>
  <div class="bar-area">
    <ul>
      <li v-for="item in items" :key="item.id">
        <span class="title">{{item.name}}</span>
        <p class="bgbar">
          <span class="bg-progress" :style="item.progressw"></span>
        </p>
        <span class="count">{{item.count}}只</span>
        <span class="percent">{{item.percent}}</span>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    props: ['lists', 'total'],
    components: {},
    data() {
      return {
        items: [
          {
            name:'',
            count:0
          },
          {
            name:'',
            count:0
          },
          {
            name:'',
            count:0
          },
          {
            name:'',
            count:0
          },
          {
            name:'',
            count:0
          }
        ]
      }
    },
    watch: {
      lists() {
        this.greatData()
      },
      total() {
        this.greatData()
      }
    },
    methods: {
      greatData() {
        let alldata = this.lists || this.items;

        alldata.forEach(function (val, idx) {
          let ct = alldata[idx]['count'] / this.total;
          alldata[idx]['percent'] = parseFloat(ct * 100).toFixed(2) + '%';
          alldata[idx]['progressw'] = 'width:' + parseFloat(ct).toFixed(2) * 3.65 + 'rem';
        }.bind(this));

        this.items = alldata;
      }
    },
    created() {
      this.greatData();
    }
  }
</script>

<style scoped lang="less">
  .bar-area {
    width: 6.62rem;
    margin: 0 auto;
    overflow: hidden;
    li {
      width: 6.62rem;
      height: .2rem;
      margin: .4rem 0;
      line-height: .2rem;
      font-size: 12px;
      color: #999;
      .title {
        display: inline-block;
        float: left;
        width: 1.2rem;
        height: .2rem;
        text-align: right;
      }
      .bgbar {
        display: inline-block;
        float: left;
        width: 3.65rem;
        height: .2rem;
        background: #f0f0f0;
        margin-left: .05rem;
        .bg-progress {
          display: inline-block;
          float: left;
          height: .2rem;
          background: #E30413;
        }
      }
      .count {
        display: inline-block;
        float: left;
        width: .8rem;
        text-align: right;
        margin-left: .05rem;

      }
      .percent {
        display: inline-block;
        float: left;
        margin-left: .05rem;

      }
    }
  }
</style>
