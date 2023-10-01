<script>
  import { brailleAlphabet } from "./lib/alphabets/braileAlphabet";
  import Header from "./lib/components/Header.svelte";
  import FromBraille from "./lib/components/FromBraille.svelte";
  import FromSpanish from "./lib/components/FromSpanish.svelte";
  import TranslateHeader from "./lib/components/TranslateHeader.svelte";

  let spanishText = "";
  let translatedText = "";

  let languageFrom = "Español";
  let languageTo = "Braille";

  function resetText() {
    spanishText = "";
    translatedText = "";
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
    <TranslateHeader bind:languageFrom bind:languageTo {resetText} />
    <div class="translate-area">
      {#if languageFrom === "Braille"}
        <FromBraille bind:translatedText />
      {:else}
        <FromSpanish bind:spanishText />
      {/if}
      <hr />
      <div class="translate-to">
        {translatedText}
        <img
          src="reload.svg"
          alt="reload"
          class="reload"
          on:click={resetText}
        />
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

  hr {
    margin: 0;
    border: 1pt solid gray;
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
