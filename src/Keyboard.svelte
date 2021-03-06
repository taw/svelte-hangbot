<script>
  export let lettersChosen;
  export let onLetter;

  let letters = [
    "A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "_"
  ]
</script>

<div>
  {#each letters as letter}
    {#if lettersChosen.includes(letter)}
      <button disabled>{letter}</button>
    {:else}
      <button on:click={() => onLetter(letter)}>{letter}</button>
    {/if}
  {/each}
</div>

<style>
  div {
    display: flex;
  }
</style>
