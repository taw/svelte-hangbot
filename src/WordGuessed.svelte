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
  font-size: 30px;
  display: flex;
  justify-content: center;
  text-align: center;
  flex-wrap: wrap;
  line-height: 30px;
  margin: auto;
  max-width: 80vw;
}
.letter {
  margin: 10px;
  height: 50px;
  width: 50px;
  background-color: black;
  color: white;
  border: 1px solid grey;
  text-align: center;
  line-height: 50px;
}
</style>
