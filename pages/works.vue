<template>
  <div role="main" class="scroll-wrap">
    <section class="work-design">
      <h1>Design</h1>
      <div class="flexbox container">
        <a href="https://vulnerability-page.tk/" target="_blank" class="design-item">
          <img :src="b64VulnerabiritySite">
          <h2>Vulnerability Information Site</h2>
          <p> <img src="~/assets/img/pg-icon/nginx_icon.svg"> <img src="~/assets/img/pg-icon/vue-js_icon.svg"> <img src="~/assets/img/pg-icon/python_icon.svg"> </p>
          <p>{{ $t('WORKS_VUL_SITE_LABEL') }}</p>
        </a>
      </div>
      <div class="arrow-wrap">
        <svg viewBox="0 0 40 20" class="scroll-arrow"><path d="M20,13.8C11.4-1,0,0,0,0l20,20L40,0C40,0,28.6-1,20,13.8z"></path></svg>
      </div>
    </section>
    <section class="about-dataset">
      <h1>Data Set</h1>
      <div class="chart-container w-flexbox">
        <ChartRadar
          :chartData="chartData"
          :chartOptions="chartOptions('Language')"
        />
        <ChartRadar
          :chartData="chartDatabase"
          :chartOptions="chartOptions('Database')"
        />
        <ChartRadar
          :chartData="chartOssData"
          :chartOptions="chartOptions('OSS')"
        />
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import { ChartData, ChartOptions } from 'chart.js'
import ChartRadar from '~/components/ChartRadarComponent.vue'

import b64Img from '~/components/b64/b64'

@Component({
  components: {
    ChartRadar
  }
})
export default class Works extends Vue {

  get b64VulnerabiritySite(): string {
    return b64Img.vulnerabiritySite;
  }
  
  get chartData(): ChartData | null {
    return {
      // データセットプロパティに関する設定
      // See https://misc.0o0o.org/chartjs-doc-ja/charts/radar.html
      labels: ['Python', 'Node.js', 'Vue.js', 'Angular', 'React.js', 'Java', 'Scala', 'Shell'],
      datasets: [
        {
          label: 'Usage',
          data: [5, 4.5, 4, 3, 3, 4, 2, 4]
        }
      ]
    } as ChartData
  }

  get chartDatabase(): ChartData | null {
    return {
      labels: ['Oracle', 'MySQL', 'PostgreSQL', 'Cassandra', 'Hive'],
      datasets: [
        {
          label: 'Usage',
          data: [4, 4, 3, 4, 3.5]
        }
      ]
    } as ChartData
  }

  get chartOssData(): ChartData | null {
    return {
      labels: ['Docker', 'Kubernetes', 'Chef', 'Screwdriver.cd'],
      datasets: [
        {
          label: 'Usage',
          data: [5, 4, 3, 4]
        }
      ]
    } as ChartData
  }

  private chartOptions(title: string): ChartOptions {
    return {
      responsive: true, // コンテナサイズが変更された際に、チャートキャンバスサイズを変更します
      responsiveAnimationDuration: 0, // サイズ変更イベント後に新しいサイズにアニメーションするのに要する時間（ミリ秒）
      maintainAspectRatio: false, // サイズ変更の際に、元のキャンバスのアスペクト比(width / height)を維持します。
      // onResize(chart, size): void {
      //   // サイズ変更が発生したときに呼び出されます。チャートインスタンスと新しいサイズの2つの引数を渡します。
      // },
      layout: {
        // レイアウトに関する設定
        // See https://misc.0o0o.org/chartjs-doc-ja/configuration/layout.html
        padding: {
          left: 0,
          right: 0,
          top: 40,
          bottom: 40
        }
      },
      title: {
        // タイトル
        // See https://misc.0o0o.org/chartjs-doc-ja/configuration/title.html
        display: true, // タイトルを表示します。
        position: 'top', // タイトルの位置
        fontSize: 20, // タイトルのフォントサイズ
        padding: 20, // タイトルテキストの上下に追加するピクセル数
        text: title
      },
      legend: {
        // 凡例に関する設定
        // See https://misc.0o0o.org/chartjs-doc-ja/configuration/legend.html
        display: false, // 凡例を表示します。
        position: 'bottom', // 凡例の位置
        labels: {
          fontSize: 14
        }
      },
      tooltips: {
        // ツールチップに関する設定
        // See https://misc.0o0o.org/chartjs-doc-ja/configuration/tooltip.html
        enabled: false // キャンバス上でツールチップを有効にします
      },
      elements: {
        // 要素に関する設定
        // See https://misc.0o0o.org/chartjs-doc-ja/configuration/elements.html
        point: {
          // 点に関する設定
        },
        line: {
          // 線に関する設定
          borderColor: 'rgba(0,0,0,0.3)'
        },
        rectangle: {
          // 矩形に関する設定
        },
        arc: {
          // 円弧に関する設定
        }
      },
      scale: {
        angleLines: {
          display: false
        },
        ticks: {
          suggestedMin: 0,
          suggestedMax: 5
        }
      }
    } as ChartOptions
  }
}

</script>

<style scoped>
  .work-design {
    padding: 10% 0 25%;
    position: relative;
  }

  .work-design h1, .full-blog h1 {
    font-family: Sofia,cursive;
  }

  .work-design h2 {
    font-family: serif;
    font-weight: bold;
  }

  .work-design h1 {
    text-align: center;
    font-size: 4.375rem;
    margin-bottom: 2%;
  }

  .work-design .flexbox {
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .work-design .design-item {
    width: 48%;
    text-align: center;
    margin-top: 3%;
    color: #333;
  }

  .work-design .design-item h2 {
    margin: 1% 0 6%;
  }

  .work-design .design-item img {
    box-shadow: 0 3px 10px rgb(0 0 0 / 20%);
    transition: .3s;
    border-radius: 5px;
    margin-bottom: 0;
    display: inline-block;
  }

  .work-design a {
    width: 50%;
    display: inline-block;
    text-align: center;
    transition: .3s;
  }

  .work-design img:hover {
    box-shadow: 10px 10px 25px 15px rgba(0, 0, 0, 0.3);
    transform: translateY(-4px);
  }

  .work-design .design-item p {
    margin-block: 0;
  }

  .work-design .design-item p img {
    width: 20px;
    margin-left: 1%;
    box-shadow: none;
    margin-bottom: 0;
    display: inline-block;
  }

  .work-design .arrow-wrap {
    bottom: 8%;
  }

  .about-dataset {
    padding: 10% 0 25%;
    position: relative;
  }

  .about-dataset h1 {
    text-align: center;
    font-size: 4.375rem;
    font-family: "Sofia",cursive;
    margin-bottom: 1%;
  }

  .about-dataset .arrow-wrap {
    bottom: -48px;
  }

  @media (min-width: 1080px) {
    .container, .narrow-container {
      padding-right: 0;
      padding-left: 0;
    }
  }

  @media screen and (min-width: 860px) and (-webkit-min-device-pixel-ratio: 0) {
    .work-design .design-item h2 {
      margin-bottom: 0;
    }
  }

</style>
