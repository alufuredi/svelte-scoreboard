<script>
  import { createEventDispatcher } from "svelte";

  export let name = "John Doe";
  export let points = 300;

  // $: if (points === undefined) {
  //   points = 0;
  // }
  const dispatch = createEventDispatcher();

  let showControls = false;
  //   $: btnText = showControls ? "hide" : "show";
  function addPoints() {
    points += 1;
  }
  function removePoints() {
    points -= 1;
  }
  const toggle = () => (showControls = !showControls);
  function removePlayer() {
    dispatch("removeplayer", name);
  }
</script>

<style>
  h1 {
    color: #204f6e;
  }
  h3 {
    margin-bottom: 10px;
  }
</style>

<div class="card">
  <h1>
    {name}
    <button class="btn btn-sm" on:click={toggle}>
      <!-- {#if showControls}-{:else}+{/if} -->
      {showControls ? 'hide' : 'show'}
    </button>
    <button class="btn btn-danger btn-sm" on:click={removePlayer}>
      Delete
    </button>
  </h1>

  <h3>{points}</h3>
  {#if showControls}
    <button class="btn" on:click={addPoints}>+1</button>
    <button class="btn btn-dark" on:click={removePoints}>-1</button>
    <input type="number" bind:value={points} />
  {/if}
</div>
