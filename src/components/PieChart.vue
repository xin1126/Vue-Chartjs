<script>
import { Pie } from "vue-chartjs";

export default {
  extends: Pie,
  props: ["customChartData", "options"],
  data() {
    return {
      cartData: this.customChartData,
    };
  },
  mounted() {
    console.log(this.cartData);
    this.cartData.datasets[0].backgroundColor = [
      "coral",
      "darkcyan",
      "darkseagreen",
      "mediumvioletred",
      "plum",
    ];
    this.renderChart(this.cartData, this.options);
  },
  watch: {
    customChartData(value) {
      if (value) this.$data._chart.update();
    },
  },
};
</script>
<style>
.aa {
  color: plum;
}
</style>
