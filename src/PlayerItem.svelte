<script>
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  export let player;
  let points = player.points;
  let name = player.name;
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
  const deletePlayer = (e) => {
    dispatch('deletePlayer', name);
  };
</script>

<style>
</style>

<div class="container">
  <h5>{name} <span class="red-text">{points}</span></h5>
  <button on:click={toggleControls} class="btn round pink">
    <i class="material-icons">{#if !showControls}adjust{:else}adjust{/if}</i>
  </button>
  {#if showControls}
    <button class="btn green" on:click={addPoint}>+</button>
    <button class="btn red" on:click={removePoint}>-</button>
    <button class="btn black" on:click={deletePlayer}><i
        class="material-icons">delete</i></button>
    <input type="number" bind:value={points} />
  {/if}
</div>
