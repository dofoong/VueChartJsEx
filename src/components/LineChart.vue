<template>
  <div>
    <q-card>
      <q-card-section class="q-pt-none">
        <div class="text-h6">지역별 수질 검색</div>
      </q-card-section>

      <q-card-section>
        <div style="width: 500px;">
          <base-line
            :options="linechartOptions"
            :data="linechartData"
          />
        </div>
      </q-card-section>
    </q-card>
  </div>
</template>

<script lang="ts">
import {
  defineComponent, ref, onMounted, computed,
} from 'vue';
import { Line } from 'vue-chartjs';
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
  name: 'LineChart',
  components: { BaseLine: Line }, // 이름 변경 및 등록
  setup() {
    function lineChartDataFetch() {
      const labels = ['2024-0109-1234', '2024-0109-1244', '2024-0109-1246', '2024-0109-1259', '2024-0209-1021', '2024-0221-2214'];

      return {
        labels,
        datasets: [
          {
            label: '수온',
            data: [0, 20, 40, 60, 80, 100],
            backgroundColor: 'rgba(255, 0, 0, 0.2)',
            borderColor: 'rgba(255, 192, 192, 1)',
            borderWidth: 0.5,
          },
          {
            label: '탁도',
            data: [20, 40, 60, 80, 100, 10],
            backgroundColor: 'rgba(255, 165, 0, 0.2)',
            borderColor: 'rgba(255, 165, 0, 1)',
            borderWidth: 0.5,
          },
          {
            label: 'PH',
            data: [20, 40, 60, 80, 100, 10],
            backgroundColor: 'rgba(255, 255, 0, 0.2)',
            borderColor: 'rgba(255, 255, 0, 1)',
            borderWidth: 0.5,
          },
          {
            label: 'DO',
            data: [20, 40, 60, 80, 100, 10],
            backgroundColor: 'rgba(64, 224, 208, 0.2)',
            borderColor: 'rgba(64, 224, 208, 1)',
            borderWidth: 0.5,
          },
          {
            label: 'COD',
            data: [20, 40, 60, 80, 100, 10],
            backgroundColor: 'rgba(135, 206, 235, 0.2)',
            borderColor: 'rgba(135, 206, 235, 1)',
            borderWidth: 0.5,
          },
          {
            label: 'NH4',
            data: [20, 40, 60, 80, 100, 10],
            backgroundColor: 'rgba(128, 0, 128, 0.2)',
            borderColor: 'rgba(128, 0, 128, 1)',
            borderWidth: 0.5,
          },
          {
            label: 'CHLO',
            data: [20, 40, 60, 80, 100, 10],
            backgroundColor: 'rgba(128, 128, 128, 0.2)',
            borderColor: 'rgba(128, 128, 128, 1)',
            borderWidth: 0.5,
          },
          {
            label: '전압',
            data: [20, 40, 60, 80, 100, 10],
            backgroundColor: 'rgba(255, 182, 193, 0.2)',
            borderColor: 'gba(255, 182, 193, 1)',
            borderWidth: 0.5,
          },
        ],
      };
    }

    return {
      linechartData: computed(lineChartDataFetch),
      linechartOptions: {
        responsive: true,
        scales: {
          y: {
            display: true,
            type: 'linear',
            max: 14,
            stepSize: 2,
          },
        },
      },
    };
  },
});
</script>
