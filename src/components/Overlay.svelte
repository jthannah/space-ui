<script>
    export let menuActive;

    import { fade } from 'svelte/transition';
</script>

{#if menuActive}
  <div transition:fade="{{duration: 300}}" id="overlay" on:click={() => menuActive = !menuActive}></div>
{/if}

<style lang="stylus">
  #overlay
    background #000000
    opacity 0.5
    position absolute
    top 0
    bottom 0
    left 0
    right 0
    width 100%
    height 100%
    z-index: 1
</style>