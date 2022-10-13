<script>
import { Radar } from "vue-chartjs";

export default {
  extends: Radar,
  props: ["customChartData", "options"],
  mounted() {
    this.renderChart(this.customChartData, this.options);
  },
  watch: {
    customChartData(value) {
      if (value) this.$data._chart.update();
    },
  },
};
</script>
