<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";

  let players = [
    { name: "John Doe", points: 67 },
    { name: "Jane Done", points: 25 },
    { name: "David Moe", points: 93 },
    { name: "Janet Meta", points: 27 }
  ];

  function addNewPlayer(e) {
    let player = e.detail;
    players = [...players, player];
  }

  function deletePlayer(e) {
    let playername = e.detail;
    players = players.filter(player => player.name != playername);
  }
</script>

<style>

</style>

<Navbar />

<div class="container">
  <AddPlayer on:addnewplayer={addNewPlayer} />
  {#if players.length !== 0}
    {#each players as player}
      <Player {...player} on:removeplayer={deletePlayer} />
    {/each}
  {:else}
    <p>No players yet</p>
  {/if}
</div>
