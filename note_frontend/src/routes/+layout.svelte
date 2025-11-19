<script lang="ts">
  import '../app.css';
  import Header from '$lib/components/Header.svelte';
  let { children } = $props();
</script>

<div class="shell">
  <Header />
  <main>
    {@render children()}
  </main>
</div>

<style>
  .shell {
    display: grid;
    grid-template-rows: auto 1fr;
    min-height: 100vh;
  }
  main {
    display: grid;
    grid-template-columns: 320px 1fr;
    min-height: 0;
  }
  @media (max-width: 840px) {
    main {
      grid-template-columns: 1fr;
    }
  }
</style>
