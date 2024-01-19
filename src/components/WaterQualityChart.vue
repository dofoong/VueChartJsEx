<template>
  <div>
    <q-card>
      <q-card-section class="q-pt-none">
        <div class="text-h6">지역별 수질 현황</div>
      </q-card-section>

      <q-card-section>
        <bar
          :options="chartOptions"
          :data="chartData"
        />
      </q-card-section>
    </q-card>
  </div>
</template>

<script lang="ts">
import {
  defineComponent, ref, onMounted, computed,
} from 'vue';
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  BarElement,
  Title,
  Tooltip,
  Legend,
} from 'chart.js';
import { Bar } from 'vue-chartjs';

// ChartJS 인스턴스 등록
ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  BarElement,
  Title,
  Tooltip,
  Legend,
);

export default defineComponent({
  name: 'WaterQualityChart',
  components: { Bar },
  setup() {
    function WaterQualityChartDataFetch() {
      const labels = ['지역1', '지역2', '지역3', '지역4'];

      return {
        labels,
        datasets: [
          {
            label: '수질 현황',
            data: [75, 60, 85, 90], // 각 지역의 수질 데이터 배열 (최대값은 100)
            backgroundColor: 'rgba(75, 192, 192, 0.2)', // 막대 그래프 색상
            borderColor: 'rgba(75, 192, 192, 1)', // 막대 그래프 테두리 색상
            borderWidth: 1, // 막대 그래프 테두리 두께
          },
        ],
      };
    }

    return {
      chartData: computed(WaterQualityChartDataFetch),
      chartOptions: {
        responsive: true,
        scales: {
          y: {
            display: true,
            max: 400,
            stepSize: 50, // 눈금 간격
          },
        },
      },
    };
  },
});
</script>
