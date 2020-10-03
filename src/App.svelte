<script>
  import Navbar from './Navbar.svelte';
  import Players from './Players.svelte';
  import AddPlayer from './AddPlayer.svelte';

  let players = [
    {
      name: 'React',
      points: 10,
    },
    {
      name: 'Svelte',
      points: 9,
    },
    {
      name: 'Vue',
      points: 8,
    },
    {
      name: 'Angular',
      points: 7,
    },
  ];

  const addNewPlayer = (e) => {
    const player = e.detail;
    players = [...players, player];
  };

  const deletePlayer = (e) => {
    players = players.filter((player) => player.name !== e.detail);
  };
</script>

<Navbar />
<main>
  <div class="container">
    <AddPlayer on:addPLayer={addNewPlayer} />
    <Players {players} on:deletePlayer={deletePlayer} />
  </div>
</main>
