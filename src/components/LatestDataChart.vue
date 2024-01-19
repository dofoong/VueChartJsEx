latest 바꾸기 전
<template>
  <div>
    <q-card>
      <q-card-section class="q-pt-none">
        <div class="text-h6">지역별 최근 수질 데이터</div>
      </q-card-section>

      <q-card-section>
        <bar
          :options="latestchartOptions"
          :data="latestchartData"
          class="chart-canvas"
        />
      </q-card-section>
    </q-card>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted } from 'vue';
import { Bar } from 'vue-chartjs';

export default defineComponent({
  name: 'BarChart',
  components: { Bar },
  setup() {
    const latestchartId = 'chart-id';

    const latestchartData = ref({
      labels: ['지역1', '지역2', '지역3', '지역4', '지역5', '지역6', '지역7'],
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
          backgroundColor: 'rgba(75, 192, 192, 0.2)',
          borderColor: 'rgba(75, 192, 192, 1)',
          borderWidth: 0.5,
        },
        {
          label: '전압',
          data: [20, 40, 60, 80, 100, 10],
          backgroundColor: 'rgba(128, 128, 128, 0.2)',
          borderColor: 'rgba(128, 128, 128, 1)',
          borderWidth: 0.5,
        },
      ],
    });

    const latestchartOptions = {
      scales: {
        y: {
          beginAtZero: true,
          max: 400,
          stepSize: 50, // 눈금 간격
        },
      },
      maintainAspectRatio: false, // 종횡비 유지 비활성화
      aspectRatio: 2, // 원하는 세로 비율로 조정 (가로 비율은 자동으로 조정됨)
    };

    return {
      latestchartId,
      latestchartData,
      latestchartOptions,
    };
  },
});
</script>
