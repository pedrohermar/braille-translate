<script>
  import { brailleAlphabet } from "./lib/alphabets/braileAlphabet";
  import Header from "./lib/components/Header.svelte";
  import FromBraille from "./lib/components/FromBraille.svelte";
  import FromSpanish from "./lib/components/FromSpanish.svelte";
  import TranslateHeader from "./lib/components/TranslateHeader.svelte";
  import ReloadBtn from "./icons/ReloadBtn.svelte";

  const fullAlphabet = {...brailleAlphabet.mayus, ...brailleAlphabet.minus, ...brailleAlphabet.num}

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
      .map((char) => { 
        return fullAlphabet[char]
      })
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
        <!-- <button class="reload-btn" on:click={resetText} /> -->
        <div class="reload-btn" on:click={resetText}>
          <ReloadBtn heightBtn="40px" widthBtn="40px" />
        </div>
      </div>
    </div>
  </div>
</main>

<style>
  .translate-container {
    width: 750px;
    border: 2px solid gray;
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 40px auto;
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 0 10px black;
  }

  .translate-area {
    display: flex;
    width: 100%;
    overflow: hidden;
  }

  .translate-to {
    position: relative;
    width: 50%;
    height: 300px;
    font-size: 24px;
    padding: 16px;
    background-color: #e8e8e8;
    word-wrap: break-word;
    box-sizing: border-box;
    resize: none;
  }

  hr {
    margin: 0;
    border: 1pt solid gray;
  }

  .reload-btn {
    position: absolute;
    right: 10px;
    bottom: 0;
    cursor: pointer;
  }

  @media (max-width: 768px) {
    .translate-container {
      width: 85%;
    }

    .translate-area {
      flex-direction: column;
    }

    .reload-btn {
      height: 30px;
      width: 30px;
      right: 15px;
      bottom: 15px;
    }

    .translate-to {
      width: 100%;
    }
  }
</style>
