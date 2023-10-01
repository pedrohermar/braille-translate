<script>
  import { brailleAlphabet } from "../alphabets/braileAlphabet";
  export let translatedText;

  function handleClick(letter) {
    translatedText = translatedText.concat(letter);
  }
</script>

<div class="from-braille">
  {#each Object.entries(brailleAlphabet) as [spanishLetter, brailleLetter]}
    <button on:click={() => handleClick(spanishLetter)}>{brailleLetter}</button>
  {/each}
</div>

<style>
  .from-braille {
    width: 400px;
    height: 300px;
    padding: 16px;
  }

  .from-braille button {
    width: 40px;
    height: 40px;
    margin: 8px;
    font-size: 24px;
    border-radius: 4px;
    border: none;
    cursor: pointer;
  }
</style>
