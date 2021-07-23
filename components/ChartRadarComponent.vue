<script lang="ts">
import { Component, Mixins, Prop, Watch } from 'vue-property-decorator'
import { ChartData, ChartOptions } from 'chart.js'
import { Radar, mixins } from 'vue-chartjs'

@Component
export default class ChartRadar extends Mixins(Radar, mixins.reactiveProp) {

  @Prop()
  public chartData!: ChartData

  @Prop()
  public chartOptions!: ChartOptions

  @Prop({ default: '50%' })
  public canvasWidth!: '25%' | '34%' | '50%' | '100%'

  @Prop({ default: '50%' })
  public canvasHeight!: '25%' | '34%' | '50%' | '100%'

  @Watch('chartData')
  onChartDataChanged() {
    this.load()
  }

  mounted() {
    this.addPlugin({
      beforeDraw: (c: { chart: { ctx: any; width: any; height: any; canvas: any }; }) => {
        c.chart.canvas.parentNode.style.height = this.canvasHeight
        c.chart.canvas.parentNode.style.width = this.canvasWidth
        c.chart.canvas.parentNode.style.margin = '0 auto'
        const ctx = c.chart.ctx
        ctx.fillStyle = 'hsla(0, 0%, 100%, 0.4)'
        ctx.fillRect(0, 0, c.chart.width, c.chart.height)
        ctx.save()
      }
    })
    this.renderChart(this.chartData, this.chartOptions)
  }

  load() {
    this.renderChart(this.chartData, this.chartOptions)
  }
}
</script>
