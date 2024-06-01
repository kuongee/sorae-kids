<script lang="ts">
  import { onMount } from 'svelte';
  import Layout from './components/Layout.svelte';
  import garland from './assets/garland.png';
  import image1 from './assets/image1.png';
  import image2 from './assets/image2.jpeg';

  onMount(async () => {
    const script = document.createElement('script');

    script.onload = () => {
      window.kakao.maps.load(() => {
        const mapContainer = document.getElementById('map');
        const mapOption = {
          center: new window.kakao.maps.LatLng(37.621482, 127.027384), // 지도의 중심좌표
          level: 2, // 지도의 확대 레벨
          marker: {
            position: new window.kakao.maps.LatLng(37.621482, 127.027384),
            text: '서울소래교회',
          },
        };
        new window.kakao.maps.StaticMap(mapContainer, mapOption);
      });
    };

    script.async = true;
    script.src = `//dapi.kakao.com/v2/maps/sdk.js?appkey=${import.meta.env.VITE_KAKAO_KEY}&autoload=false`;
    document.head.appendChild(script);
  });
</script>

<div>
  <Layout>
    <img alt="garland" src={garland} />
    <h1 class="text-center">소래교회 아동부</h1>
    <h1 class="text-center">초청장</h1>
    <section class="mx-4 text-center mt-4">
      <p>소래교회 아동부로 놀러오세요!</p>
      <p>매주 일요일 아침 11시</p>
    </section>
    <section class="mx-4">
      <div class="columns-2">
        <img class="w-full rounded-md" src={image1} />
        <img class="w-full rounded-md" src={image2} />
        <!-- ... -->
      </div>
    </section>
    <section class="mx-4">
      <h2>오는 길</h2>
      <p>미아역에서</p>
      <div id="map" style="width:100%;height:200px;"></div>
    </section>
  </Layout>
</div>

<style lang="postcss">
  :global(html) {
    background-color: theme(colors.orange.100);
  }
</style>
