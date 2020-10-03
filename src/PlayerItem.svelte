<script>
  export let player;
  let points = player.id;
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
</script>

<style>
</style>

<div class="container">
  <h5>{name} <span class="red-text">{points}</span></h5>
  <button on:click={toggleControls} class="btn round pink">
    <i class="material-icons">{#if !showControls}add{:else}delete{/if}</i>
  </button>
  {#if showControls}
    <button class="btn green" on:click={addPoint}>Add</button>
    <button class="btn red" on:click={removePoint}>Remove</button>
    <input type="number" bind:value={points} />
  {/if}
</div>
