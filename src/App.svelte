<script>
  import Header from "./lib/components/Header.svelte";
  import { braileMap } from "./lib/alphabets/braileMap";

  let texto = "";
  let textoTraducido = "";

  let languageFrom = "Español";
  let languageTo = "Braille";

  function handleInput(e) {
    texto = e.target.value;
  }

  function handleSwitchLanguages(e) {
    [languageFrom, languageTo] = [languageTo, languageFrom];
  }

  $: {
    textoTraducido = texto
      .split("")
      .map((letra) => braileMap[letra.toLowerCase()])
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
      {#if languageTo === "Braille"}
        <div class="translate-from">
          {#each Object.values(braileMap) as letter}
            <button>{letter}</button>
          {/each}
        </div>
      {:else}
        <textarea name="from" on:input={handleInput} class="translate-from" />
      {/if}
      <hr />
      <textarea
        name="to"
        class="translate-to"
        value={textoTraducido}
        disabled
      />
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

  div .translate-from {
    width: 400px;
    height: 300px;
    padding: 16px;
  }

  .translate-from button {
    width: 40px;
    height: 40px;
    margin: 5px;
    font-size: 24px;
    border-radius: 4px;
    border: none;
    cursor: pointer;
  }
</style>
