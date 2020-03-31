<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  let showErrors = false;

  let player = {
    name: "",
    points: ""
  };

  function btnAddPlayerClicked() {
    if (player.name !== "" && player.points !== undefined) {
      dispatch("addplayer", player);
      player = {
        name: "",
        points: ""
      };
      showErrors = false;
    } else {
      showErrors = true;
    }
  }
</script>

<style>
  .error {
    font-size: 0.75em;
    color: red;
  }
</style>

<div class="grid-3 ">

  <input type="text" bind:value={player.name} placeholder="Player's name" />

  <input
    type="number"
    bind:value={player.points}
    placeholder="Player's points" />

  <button class="btn btn-primary" on:click={btnAddPlayerClicked}>
    Add Player
  </button>
</div>
<p class="error">{showErrors ? 'Invalid values for player' : ''}</p>
