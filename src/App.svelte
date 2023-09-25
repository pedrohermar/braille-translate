<script>
  import Header from "./lib/components/Header.svelte";
  import { brailleAlphabet } from "./lib/alphabets/braileAlphabet";

  let spanishText = "";
  let translatedText = "";

  let languageFrom = "Español";
  let languageTo = "Braille";

  function resetText() {
    spanishText = "";
    translatedText = "";
  }

  function handleInput(e) {
    spanishText = e.target.value;
  }

  function handleClick (letter) {
    translatedText = translatedText.concat(letter)
  }

  function handleSwitchLanguages(e) {
    resetText();
    [languageFrom, languageTo] = [languageTo, languageFrom];
  }

  $: {
    translatedText = spanishText
      .split("")
      .map((letter) => brailleAlphabet[letter.toLowerCase()])
      .join("");
  }
</script>

<Header />

<main>
  <div class="translate-container">
    <div class="translate-header">
      <h2>{languageFrom}</h2>
      <button class="switch-languages" on:click={handleSwitchLanguages} />
      <h2>{languageTo}</h2>
    </div>
    <div class="translate-area">
      {#if languageFrom === "Braille"}
        <div class="translate-from">
          {#each Object.entries(brailleAlphabet) as [spanishLetter, brailleLetter]}
            <button on:click={() => handleClick(spanishLetter)}>{brailleLetter}</button>
          {/each}
        </div>
      {:else}
        <textarea name="from" on:input={handleInput} value={spanishText} />
      {/if}
      <hr />
      <div
        class="translate-to"
      >
      {translatedText}
      <img src="reload.svg" alt="reload" class="reload" on:click={resetText}>
      </div>
    </div>
  </div>
</main>

<style>
  .translate-container {
    border: 2px solid gray;
    display: flex;
    flex-direction: column;
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 0 10px black;
  }

  .translate-header {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    background-color: rgb(254, 224, 80);
  }

  .translate-area {
    display: flex;
  }

  .translate-to {
    position: relative;
    width: 400px;
    height: 300px;
    font-size: 24px;
    padding: 16px;
    word-wrap: break-word;
  }

  .switch-languages {
    background-image: url(switch-horizontal.svg);
    background-size: cover;
    background-color: transparent;
    height: 40px;
    width: 80px;
    border: none;
    cursor: pointer;
  }

  h2 {
    margin: 0;
    padding: 12px 16px;
    width: 100%;
    text-align: left;
  }

  hr {
    margin: 0;
    border: 1pt solid gray;
  }

  textarea {
    width: 400px;
    height: 300px;
    margin: 0;
    padding: 16px;
    font-size: 1rem;
    resize: none;
    border: none;
    outline: none;
  }

  .translate-from {
    width: 400px;
    height: 300px;
    padding: 16px;
  }

  .translate-from button {
    width: 40px;
    height: 40px;
    margin: 8px;
    font-size: 24px;
    border-radius: 4px;
    border: none;
    cursor: pointer;
  }

  .reload {
    height: 40px;
    width: 40px;
    position: absolute;
    right: 10px;
    bottom: 10px;
    cursor: pointer;
  }
</style>
