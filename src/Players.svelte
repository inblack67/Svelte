<script>
  import PlayerItem from './PlayerItem.svelte';
  import axios from 'axios';
  let players = [];
  const getPlayers = async () => {
    const res = await axios(`https://jsonplaceholder.typicode.com/users`);
    players = [...players, ...res.data];
  };
  getPlayers();
</script>

<ul class="collection-item">
  {#if players.length > 0}
    {#each players as player}
      <PlayerItem {player} />
    {/each}
  {/if}
</ul>

<pre>
    {JSON.stringify(players, null, 3)}
</pre>
