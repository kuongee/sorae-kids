<script lang="ts">
  import { Confetti } from 'svelte-confetti';
  import garland from '../assets/garland2.png';
  import church from '../assets/church.png';
</script>

<div class="container mx-auto max-w-screen-md">
  <div class="fixed left-2/4 -top-5 z-20">
    <Confetti
      x={[-5, 5]}
      y={[0, 0.1]}
      delay={[500, 2000]}
      duration={5000}
      amount={200}
      fallDistance="100vh"
      size={10}
      colorArray={["#ff7158", "#ffc783", "#a7d345", "#a7d3e4", "#cd3072"]}
    />
  </div>

  <img class="mb-4" alt="garland" src={garland} />
  <div class="mt-6 px-4">
    <slot />
  </div>
  <img alt="church" src={church} />
</div>

<style lang="postcss">
</style>
