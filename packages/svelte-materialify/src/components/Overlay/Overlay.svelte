<script>
  import { fade } from 'svelte/transition';
  import BackgroundColor from '../../internal/BackgroundColor';

  let klass = '';
  export let active = true;
  export let opacity = 0.46;
  export let color = 'rgb(33, 33, 33)';
  export let index = 5;
  export let absolute = false;
  export let fadeOptions = {};
  export let style = '';
  export { klass as class };
</script>

<style lang="scss" src="./Overlay.scss">
</style>

{#if active}
  <div
    transition:fade={fadeOptions}
    class="s-overlay {klass}"
    class:absolute
    on:click
    style="z-index:{index};{style}">
    <div class="s-overlay__scrim" use:BackgroundColor={color} style="opacity:{opacity}" />
    <div class="s-overlay__content">
      <slot />
    </div>
  </div>
{/if}
