<script>
  import RobotGallows from "./RobotGallows.svelte";
  import Keyboard from "./Keyboard.svelte";
  import WordGuessed from "./WordGuessed.svelte";
  import {dictionary} from "./dictionary.js";

  let lettersChosen = [];
  let word = randomDictionaryWord();
  let stage = 0;
  let enabled = true;

  function restart() {
    lettersChosen = [];
    word = randomDictionaryWord();
    stage = 0;
    enabled = true;
  }

  function randomElement(array) {
    return array[Math.floor(Math.random() * array.length)];
  }

  // Get another one if word contains numbers or special characters
  // like $
  function randomDictionaryWord() {
    while (true) {
      let word = randomElement(dictionary);
      if (!/[^A-Za-z_]/.test(word)) {
        return word;
      }
    }
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
    // alert is blocking so we need to put it in setTimeout 0
    // so the page can update what's displayed
    if (isGameWon()) {
      setTimeout(() => alert("YOU WON!"), 0)
      enabled = false;
    }
    if (stage == 8) {
      setTimeout(() => alert(`GAME LOST! Word was ${word}`), 0);
      enabled = false
    }
    console.log("letter", stage, lettersChosen);
  }
</script>

<h1>Hangbot</h1>

<RobotGallows stage={stage} />

<h2>Secret word:</h2>

<WordGuessed word={word} lettersChosen={lettersChosen} />

{#if enabled}
  <h2>Keyboard:</h2>
  <Keyboard lettersChosen={lettersChosen} onLetter={onLetter} />
{:else}
  <button on:click={restart}>RESTART GAME</button>
{/if}

<style>
  h1 {
    font-size: 400%;
  }
  h2 {
    font-size: 150%;
  }
</style>
