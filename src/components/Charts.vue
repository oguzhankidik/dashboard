<template>
  <div class="main">
    <div class="card" style="height: 20rem">
      <highcharts class="hc" :options="chartOptions" ref="chart"></highcharts>    </div>
  </div>
</template>

<script>
export default {
  props:{
    message:{

    }
  },

  data() {
    return {
      chartOptions: {
        chart:{
          height:340,
          width:1800
        },
        xAxis:{
          categories:['00:00','01:00','02:00']
        },
        title:null,
        series: [
          {
            data :this.message
          }
        ]
      }
    };
  }
}
</script>
<style scoped>
.main{
  padding: 20px;
}

</style>


