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
    width: 50%;
    height: 300px;
    padding: 12px;
    background-color: #e8e8e8;
    box-sizing: border-box;
    resize: none;
  }

  .from-braille button {
    width: 40px;
    height: 40px;
    margin: 8px;
    font-size: 24px;
    border-radius: 4px;
    border: 1px solid gray;
    background-color: #87f6ff;
    cursor: pointer;
    transition: transform 0.1s ease;
  }

  .from-braille button:hover {
    transform: scale(1.1);
  }

  @media (max-width: 768px) {
    .from-braille {
      width: 100%;
    }

    .from-braille button {
      width: 37px;
      height: 37px;
      margin: 6px;
    }
  }
</style>
