<script>
  import Navbar from './Navbar.svelte';
  import axios from 'axios';
  let players = [];
  const getPlayers = async () => {
	const res = await axios(`https://jsonplaceholder.typicode.com/users`);
	players = [...players, ...res.data];
  };
  getPlayers();
  const name = 'hell';
  let points = 100;
  let showControls = false;
  const addPoint = (e) => {
    points += 1;
  };
  const removePoint = (e) => {
    points -= 1;
  };
  const toggleControls = (e) => {
    showControls = !showControls;
  };
</script>

<style>
</style>

<Navbar />
<main>
  <div class="container">
    <h5>Name {name}</h5>
    <h5>Points {points}</h5>
    <button on:click={toggleControls} class="btn round pink">
      <i class="material-icons">{#if !showControls}add{:else}delete{/if}</i>
    </button>
    {#if showControls}
      <button class="btn green" on:click={addPoint}>Add</button>
      <button class="btn red" on:click={removePoint}>Remove</button>
      <input type="number" bind:value={points} />
    {/if}
  </div>
</main>
