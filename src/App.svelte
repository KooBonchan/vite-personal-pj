<script lang="ts">
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
  import axios from 'axios';
  import type { Photo } from './model/photos.svelte';

  const handleFetch = 
    axios.get('https://jsonplaceholder.typicode.com/albums/1/photos')
    .then((response):Photo[] => response.data)
    .catch()
</script>

<main>
  {#await handleFetch then data}
    {#each data as d}
      <div>{d.id} {d.title}</div>
    {/each}
  {/await}
  <!-- <div>
    <a href="https://vite.dev" target="_blank" rel="noreferrer">
      <img src={viteLogo} class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
  </div>
  <h1>Vite + Svelte</h1>

  <div class="card">
    <Counter />
  </div>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme" target="_blank" rel="noreferrer">SvelteKit</a>, the official Svelte app framework powered by Vite!
  </p>

  <p class="read-the-docs">
    Click on the Vite and Svelte logos to learn more
  </p> -->
</main>