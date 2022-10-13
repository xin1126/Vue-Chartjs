<script>
import { Line } from "vue-chartjs";

export default {
  extends: Line,
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
