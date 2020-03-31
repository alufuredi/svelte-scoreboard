<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    {
      name: "Anna Mark",
      points: 649
    },
    {
      name: "James Moimo",
      points: 648
    },
    {
      name: "Edith Flemy",
      points: 938
    },
    {
      name: "John Gowe",
      points: 100
    }
  ];
  const addPlayer = e => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };

  const deletePlayer = e => {
    let playerToRemove = e.detail;
    players = players.filter(player => player.name != playerToRemove);
  };
</script>

<Navbar />
<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length !== 0}
    {#each players as player}
      <Player {...player} on:removeplayer={deletePlayer} />
    {/each}
  {:else}
    <p>No players available</p>
  {/if}
</div>
