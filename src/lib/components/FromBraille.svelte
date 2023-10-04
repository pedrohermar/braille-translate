<script>
  import { brailleAlphabet } from "../alphabets/braileAlphabet";
  export let translatedText;
  let lettersType = "minus"

  function handleClick(letter) {
    translatedText = translatedText.concat(letter);
  }

  function handleChangeType(e) {
    lettersType = e.target.textContent.toLowerCase();
  }
</script>

<div class="from-braille">
  <div class="letters-type">
    <button class={`type-btn ${lettersType === "mayus" ? "active" : ""}`} on:click={handleChangeType}>Mayus</button>
    <button class={`type-btn ${lettersType === "minus" ? "active" : ""}`} on:click={handleChangeType}>Minus</button>
    <button class={`type-btn ${lettersType === "num" ? "active" : ""}`} on:click={handleChangeType}>Num</button>
  </div>
  <div class="letters-area">
    {#each Object.entries(brailleAlphabet[lettersType]) as [spanishLetter, brailleLetter]}
      <button class="braille-letter" on:click={() => handleClick(spanishLetter)}>{brailleLetter}</button>
    {/each}
  </div>
</div>

<style>
  .from-braille {
    width: 50%;
    height: 300px;
    padding: 12px;
    background-color: #e8e8e8;
    box-sizing: border-box;
    resize: none;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .letters-type {
    border: 1px solid gray;
    border-radius: 10px;
    margin-bottom: 16px;
  }
  
  .type-btn {
    border: none;
    padding: 6px 8px;
    background-color: transparent;
    cursor: pointer;
  }

  .active {
    background-color: #87f6ff;
    border-radius: 10px;
    box-sizing: border-box;
  }

  .letters-area {
    display: flex;
    flex-wrap: wrap;
    justify-content: baseline;
    gap: 12px;
  }

  .braille-letter {
    width: 39px;
    height: 39px;
    font-size: 22px;
    border-radius: 4px;
    border: 1px solid gray;
    background-color: #87f6ff;
    cursor: pointer;
    transition: transform 0.2s ease;
    padding: 0;
  }

  .braille-letter:hover {
    transform: scale(1.1);
  }

  @media (max-width: 768px) {
    .from-braille {
      width: 100%;
    }

    .braille-letter {
      width: 37px;
      height: 37px;
      font-size: 20px;
    }
  }
</style>