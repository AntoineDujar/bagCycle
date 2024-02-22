<script lang="ts">
  import Flicking, { FlickingPanel } from "@egjs/svelte-flicking";
  import { AutoPlay, Arrow } from "@egjs/flicking-plugins";

  import "@egjs/flicking-plugins/dist/arrow.css";
  import "@egjs/flicking-plugins/dist/pagination.css";
  import "@egjs/svelte-flicking/dist/flicking.css";

  let flicking: Flicking;

  const plugins = [
    new AutoPlay({ duration: 4000, direction: "NEXT", stopOnHover: true }),
    new Arrow(),
  ];
</script>

<Flicking
  {plugins}
  options={{ circular: true, duration: 450, preventDefaultOnDrag: true }}
  bind:this={flicking}
>
  <FlickingPanel><slot name="image-1" /></FlickingPanel>
  <FlickingPanel><slot name="image-2" /></FlickingPanel>
  <FlickingPanel><slot name="image-3" /></FlickingPanel>
  <FlickingPanel><slot name="image-4" /></FlickingPanel>
  <svelte:fragment slot="viewport">
    <span class="flicking-arrow-prev"></span>
    <span class="flicking-arrow-next"></span>
  </svelte:fragment>
</Flicking>

<style>
  .flicking-arrow-prev::before,
  .flicking-arrow-prev::after,
  .flicking-arrow-next::before,
  .flicking-arrow-next::after {
    background-color: rgb(50, 230, 58);
  }
</style>
