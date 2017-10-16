<template>
  <div class="bar-area vertical">
    <ul>
      <li v-for="item in items" :key="item.id">
        <span class="count">{{item.count}}</span>
        <p class="bgbar">
          <span class="bg-progress" :style="item.progressw"></span>
        </p>
        <span class="title">{{item.name}}</span>
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
          alldata[idx]['progressw'] = 'height:' + parseFloat(ct).toFixed(2) * 1.6 + 'rem';
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
      list-style-type: none;
      float: left;
      width: 1.32rem;
      height: 2.35rem;
      font-size: 12px;
      color: #999;
      .title, .count {
        display: inline-block;
        width: 100%;
        height: .34rem;
        line-height: .34rem;
        text-align: center;
      }
      .bgbar {
        display: inline-block;
        position: relative;
        width: .24rem;
        height: 1.6rem;
        margin: .02rem auto;
        background: #f0f0f0;
        margin-left: .05rem;
        .bg-progress {
          position: absolute;
          bottom: 0;
          z-index: 1;
          left: 0;
          display: inline-block;
          width: 100%;
          background: #E30413;
        }
      }
    }
  }
</style>
