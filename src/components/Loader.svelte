<script>
    import { fade } from 'svelte/transition';
    export let show = false;
</script>

{#if show}
  <div class="loader" transition:fade="{{duration: 300}}">
    <div class="spinner">
      <div class="double-bounce1"></div>
      <div class="double-bounce2"></div>
    </div>
    <span class="loading">Loading...</span>
  </div>
{/if}

<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono&display=swap');

  .loader {
      align-items: center;
      display: flex;
      flex-direction: column;
  }

  .loading {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    margin-top: 0.5rem;
  }

  .spinner {
    width: 5rem;
    height: 5rem;
    position: relative;
    margin: 0 auto;
  }

  .double-bounce1, .double-bounce2 {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: linear-gradient(to bottom right, rgba(186, 30, 104, 0.9), rgba(86, 67, 253, 0.9));
    opacity: 0.6;
    position: absolute;
    top: 0;
    left: 0;

    -webkit-animation: sk-bounce 2.0s infinite ease-in-out;
    animation: sk-bounce 2.0s infinite ease-in-out;
  }

  .double-bounce2 {
    -webkit-animation-delay: -1.0s;
    animation-delay: -1.0s;
  }

  @-webkit-keyframes sk-bounce {
    0%, 100% { -webkit-transform: scale(0.0) }
    50% { -webkit-transform: scale(1.0) }
  }

  @keyframes sk-bounce {
    0%, 100% {
      transform: scale(0.0);
      -webkit-transform: scale(0.0);
    } 50% {
      transform: scale(1.0);
      -webkit-transform: scale(1.0);
    }
  }
</style>