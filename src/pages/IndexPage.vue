<template>
  <q-page>
    <div class="row fit full-width">
      <div class="col-4">
        <!-- <MapComponent class="fit" /> -->
        <MarkerComp class="fit" />
      </div>
      <div class="col">
        <!-- WaterQuarlityChart 그래프 -->
        <div class="row q-pa-sm">
          <WaterQualityChart class="fit q-mb-none" />
        </div>
        <div class="row q-pa-sm">
          <LatestDataChart class="fit q-mb-none" />
        </div>
        <div class="row q-pa-sm">
          <LineChart class="fit q-mb-none" />
        </div>
      </div>
    </div>
  </q-page>
</template>

<script lang="ts">
import MarkerComp from 'components/MarkerComp.vue';
import WaterQualityChart from 'components/WaterQualityChart.vue';
import LatestDataChart from 'components/LatestDataChart.vue';
import LineChart from 'components/LineChart.vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'IndexPage',
  components: {
    // MapComponent,
    MarkerComp,
    WaterQualityChart,
    LatestDataChart,
    LineChart,
  },
  setup() {
    return {};
  },
});
</script>
