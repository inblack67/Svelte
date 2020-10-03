<script>
  import PlayerItem from './PlayerItem.svelte';
  export let players;
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();
  const deletePlayer = (e) => {
    dispatch('deletePlayer', e.detail);
  };
</script>

<ul class="collection-item">
  {#if players.length > 0}
    {#each players as player}
      <PlayerItem {player} on:deletePlayer={deletePlayer} />
    {/each}
  {/if}
</ul>

<pre>
    {JSON.stringify(players, null, 3)}
</pre>
