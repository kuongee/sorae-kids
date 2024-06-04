<script lang="ts">
  import { onMount } from 'svelte';
  import Layout from './components/Layout.svelte';
  import Clock from './components/icons/Clock.svelte';
  import FaceGrinWink from './components/icons/FaceGrinWink.svelte';
  import Heart from './components/icons/Heart.svelte';
  import LocationDot from './components/icons/LocationDot.svelte';

  onMount(async () => {
    const script = document.createElement('script');

    script.onload = () => {
      window.kakao.maps.load(() => {
        const lat = 37.621398;
        const lng = 127.027308;

        // 지도 생성
        const mapContainer = document.getElementById('map');
        const mapOption = {
          center: new window.kakao.maps.LatLng(lat, lng),
          level: 2,
        };
        const map = new window.kakao.maps.Map(mapContainer, mapOption);

        // 마커 표시
        const markerPosition = new window.kakao.maps.LatLng(lat, lng);
        const marker = new window.kakao.maps.Marker({
          position: markerPosition,
        });
        marker.setMap(map);
      });
    };

    script.async = true;
    script.src = `//dapi.kakao.com/v2/maps/sdk.js?appkey=${import.meta.env.VITE_KAKAO_KEY}&autoload=false`;
    document.head.appendChild(script);
  });
</script>

<Layout>
  <h1 class="flex justify-center mb-2"><Heart />초대해요<Heart /></h1>
  <h2>서울소래교회 아동부</h2>
  <div class="divide-y-2 divide-dashed divide-lime-300">
    <section class="text-center my-4 text-pretty text-2xl md:text-3xl">
      <p><Clock />매주 일요일 오전 11시</p>
      <p><LocationDot />소래교회 교육관</p>
      <section class="my-4 text-xl md:text-2xl">
        <p>어서와~ 교회는 처음이지?</p>
        <p>행복하고 재미있는 일이</p>
        <p>
          마구마구 쏟아지는 소래교회에서 만나요 <FaceGrinWink />
        </p>
      </section>
    </section>
    <section class="my-4">
      <h3 class="mt-4">오는 길</h3>
      <p>미아역에서</p>
      <div id="map" style="width:100%;height:200px;"></div>
    </section>
    <section>
      <h3 class="mt-4">교회 소개</h3>
      <p>교회 소개</p>
      <p>교회 소개</p>
      <p>교회 소개</p>
    </section>
  </div>
</Layout>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.yellow.50);
    font-family: 'NanumSquareRound', 'Noto Sans KR', sans-serif;
  }

  p {
    font-family: 'star', 'NanumSquareRound', 'Noto Sans KR', sans-serif;
    /* font-size: 1.5rem; */
  }
</style>
