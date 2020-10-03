<script>
  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  let player = {
    name: '',
    points: 0,
  };

  const onAddPLayer = (e) => {
    e.preventDefault();
    dispatch('addPLayer', player);
    player = {
      name: '',
      points: 0,
    };
  };
</script>

<form on:submit={onAddPLayer}>
  <div class="input-field">
    <input type="text" bind:value={player.name} />
    <label for="name">Name</label>
  </div>
  <div class="input-field">
    <input type="number" bind:value={player.points} />
    <label for="points">Points</label>
  </div>
  <div class="input-field">
    <button type="submit" class="btn green">Add</button>
  </div>
</form>
