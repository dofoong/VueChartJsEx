<template>
  <div>
    <!-- 지도를 표시할 div -->
    <div id="map" style="width: 100%; height: 100vh; overflow: hidden;"></div>
  </div>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue';

export default defineComponent({
  name: 'MapComponent',
  setup() {
    let mapValue: any = null;
    const markers: { [key: string]: any } = {};

    const initMap = () => {
      const mapContainer = document.getElementById('map');
      const mapOption = {
        center: new window.kakao.maps.LatLng(35.9321, 128.567),
        level: 3,
      };

      mapValue = new window.kakao.maps.Map(mapContainer, mapOption);

      window.kakao.maps.event.addListener(mapValue, 'click', (mouseEvent: any) => {
        const clickedLatLng = mouseEvent.latLng;

        // 마커 식별자 생성
        const markerId = `${clickedLatLng.getLat()},${clickedLatLng.getLng()}`;

        // 이미 해당 위치에 마커가 있는지 확인
        if (markers[markerId]) {
          // 이미 클릭한 마커를 삭제
          markers[markerId].setMap(null);
          delete markers[markerId];
        } else {
          // 새로운 마커를 생성하고 지도에 추가
          const marker = new window.kakao.maps.Marker({
            position: clickedLatLng,
          });

          marker.setMap(mapValue);

          // 마커를 식별자에 매핑
          markers[markerId] = marker;
        }
      });
    };

    onMounted(() => {
      if (window.kakao && window.kakao.maps) {
        initMap();
      }
    });

    return {
      mapValue,
      markers,
    };
  },
});
</script>
