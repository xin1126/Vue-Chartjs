<template>
  <div class="home">
    <button type="button" @click="update" class="add">
      點擊隨機新增一筆資料數值
    </button>
    <div class="container">
      <LineChart
        :customChartData="customChartData"
        :options="options"
        class="item"
      />
      <BarChart
        :customChartData="customChartData"
        :options="options"
        class="item"
      />
      <PieChart
        :customChartData="customChartData"
        :options="options"
        class="item"
      />
      <RadarChart
        :customChartData="customChartData"
        :options="options"
        class="item"
      />
    </div>
  </div>
</template>

<script>
import LineChart from "@/components/LineChart.vue";
import BarChart from "@/components/BarChart.vue";
import PieChart from "@/components/PieChart.vue";
import RadarChart from "@/components/RadarChart.vue";

export default {
  name: "App",
  components: {
    LineChart,
    BarChart,
    PieChart,
    RadarChart,
  },
  data() {
    return {
      customChartData: {
        labels: ["小明", "小王", "小花", "小乖", "小美"],
        datasets: [
          {
            label: "Data",
            data: [10, 15, 9, 32, 20],
            borderColor: "#05CBE1",
            pointBackgroundColor: "white",
            pointBorderColor: "white",
            borderWidth: 1,
            backgroundColor: "rgba(0, 231, 255, 0.25)",
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        title: {
          display: true,
          // text: "My Data",
        },
      },
    };
  },
  methods: {
    update() {
      const key = Math.floor(
        Math.random() * this.customChartData.datasets[0].data.length
      );
      this.customChartData.datasets[0].data[key]++;
      this.customChartData = {
        ...this.customChartData,
      };
    },
  },
};
</script>

<style scoped>
.home {
  text-align: center;
}

.add {
  background: darkseagreen;
  border: 0;
  color: white;
  border-radius: 10px;
  padding: 8px 10px;
  margin: 10px 0;
  font-size: 18px;
  cursor: pointer;
}

.container {
  display: flex;
  flex-wrap: wrap;
}

.item {
  width: 50%;
}
</style>
