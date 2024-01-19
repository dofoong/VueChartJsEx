<template>
  <div class="full-width">
    <q-page>
      <!-- 상단 섹션 (제목) -->
      <q-card style="width: 100%; height: 10vh;">
        <q-card-section class="q-pa-md">
          <h4 class="text-h6">Map</h4>
        </q-card-section>
      </q-card>

      <!-- 중간 섹션 (지도) -->
      <q-card style="width: 100%; height: 100vh; overflow: hidden;">
        <q-card-section style="height: 100%; padding: 0;">
          <div id="map" style="width: 100%; height: 100%;"></div>
        </q-card-section>
      </q-card>
    </q-page>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue';

export default defineComponent({
  name: 'MapComponent',
  setup() {
    let mapValue: any = null;

    function initMap() {
      const mapContainer = document.getElementById('map');
      const mapOption = {
        center: new window.kakao.maps.LatLng(35.9321, 128.567),
        level: 3,
      };

      mapValue = new window.kakao.maps.Map(mapContainer, mapOption);
    }

    onMounted(() => {
      if (window.kakao && window.kakao.maps) {
        initMap();
      }
    });

    return {
      mapValue,
    };
  },
});
</script>

<style scoped>
/* 필요한 경우 스타일 추가 */
</style>
