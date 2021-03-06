<script>
  import RobotGallows from "./RobotGallows.svelte";
  import Keyboard from "./Keyboard.svelte";
  import WordGuessed from "./WordGuessed.svelte";
  import {dictionary} from "./dictionary.js";

  let lettersChosen = [];
  let word = randomElement(dictionary);
  let stage = 0;
  let enabled = true;

  console.log("word is", word);

  function randomElement(array) {
    return array[Math.floor(Math.random() * array.length)];
  }

  function badGuess(letter) {
    return !word.toUpperCase().includes(letter.toUpperCase())
  }

  function isGameWon() {
    let characters = word.toUpperCase().split("")
    return (characters.every(c => lettersChosen.includes(c)))
  }

  function onLetter(letter) {
    lettersChosen = [...lettersChosen, letter];

    if (badGuess(letter)) {
      stage += 1;
    }
    if (isGameWon()) {
      alert("YOU WON!")
      enabled = false;
    }
    if (stage == 8) {
      alert(`GAME LOST! Word was ${word}`);
      enabled = false
    }
    console.log("letter", stage, lettersChosen);
  }

  function restart() {
    lettersChosen = [];
    word = randomElement(dictionary);
    stage = 0;
    enabled = true;
  }
</script>

<style>
  header {
    font-size: 400%;
  }
  body {
    margin: 0 auto;
  }
</style>

<header>Hangbot</header>

<RobotGallows stage={stage} />

<WordGuessed word={word} lettersChosen={lettersChosen} />

{#if enabled}
  <Keyboard lettersChosen={lettersChosen} onLetter={onLetter} />
{:else}
  <button on:click={restart}>RESTART GAME</button>
{/if}

