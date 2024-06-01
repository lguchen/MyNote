## <center>vue可视化



```vue
<template>
  <div>
    <div id="myChart" />
  </div>
</template>
<script>
import * as echarts from "echarts";
export default {
  name: "HomeView",
  data() {
    return {
      data: [],
    };
  },

  mounted() {
    this.request.get("/list").then((res) => {
      const data = res.data;
      const chartData = data.map((item) => ({
        name: item.education,
        value: item.cnt,
      }));

      const myChart = echarts.init(document.getElementById("myChart"));
      myChart.setOption({
        title: {
          text: "Referer of a Website",
          subtext: "Fake Data",
          left: "center",
        },
        tooltip: {
          trigger: "item",
          formatter: "{a} <br/>{b}:{c} ({d}%)",
        },
        legend: {
          orient: "vertical",
          left: "left",
          data: chartData.map((item) => item.name),
        },
        series: [
          {
            name: "Access From",
            type: "pie",
            radius: "40%",
            data: chartData,
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: "rgba(0, 0, 0, 0.5)",
              },
            },
          },
        ],
      });
    });
  },
};
</script>

<style scoped>
#myChart {
  position: absolute;
  left: 10%;
  top: 15%;
  height: 300px;
  width: 550px;
}
</style>
```

