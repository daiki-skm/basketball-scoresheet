<script>
import { Bar, mixins } from 'vue-chartjs';
const { reactiveProp } = mixins

export default {
  extends: Bar,
  mixins: [reactiveProp],
  data: function() {
    return {
      options: {
        scales: {
          xAxes: [{
            scaleLabel: {
              display: true,
            }
          }],
          yAxes: [{
            ticks: {
              beginAtZero: true,
              stepSize: 10,
            }
          }],
          legend: {
            display: true
          },
          responsive: true,
          maintainAspectRatio: false,
        }
      }
    }
  },
  mounted () {
    this.renderChart(this.chartData, this.options);
  }
}
</script>
