<script lang="ts">
  import garland from '../assets/garland2.png';
  import church from '../assets/church.png';
</script>

<div class="container mx-auto max-w-screen-md">
  <img class="mb-4" alt="garland" src={garland} />
  <div class="mt-6 px-4 pb-32">
    <slot />
  </div>
  <img class="fixed bottom-0" alt="church" src={church} />
</div>

<style lang="postcss">
</style>
