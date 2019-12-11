<script>
  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();

  let player = {
    name: "",
    points: 0
  };

  function addPlayer(e) {
    e.preventDefault();
    dispatch("addnewplayer", player);
    player = {
      name: "",
      points: 0
    };
  }
</script>

<form class="grid-3">
  <input type="text" bind:value={player.name} placeholder="Player's name" />
  <input type="number" bind:value={player.points} placeholder="Points" />
  <button class="btn btn-primary" on:click={addPlayer}>Add player</button>
</form>
