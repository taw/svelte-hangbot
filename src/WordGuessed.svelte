<script>
  export let word;
  export let lettersChosen;
</script>

<div class="word">
  {#each word as char}
    {#if lettersChosen.includes(char.toUpperCase())}
      <div class="letter guessed">{char}</div>
    {:else}
      <div class="letter todo">?</div>
    {/if}
  {/each}
</div>

<style>
.word {
  display: flex;
}
.letter {
  height: 30px;
  width: 30px;
  background-color: black;
  color: white;
  border: 1px solid grey;
  text-align: center;
}
</style>
