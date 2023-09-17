<script>
  import { braileMap } from "./lib/alphabets/braileMap";

  let texto = "";
  let textoTraducido = "";

  function handleInput(e) {
    texto = e.target.value;
  }

  function handleSwitchLanguages(e) {
    console.log("idioma cambiado");
  }

  $: {
    textoTraducido = texto
      .split("")
      .map((letra) => braileMap[letra.toLowerCase()])
      .join("");
  }
</script>

<header>
  <img src="braille.svg" alt="Logo Braille" height="140px" width="140px" />
  <h1>Traductor <br /> Braille</h1>
</header>

<main>
  <div class="translate-container">
    <div class="translate-header">
      <h2>Español</h2>
      <button class="switch-languages" on:click={handleSwitchLanguages} />
      <h2>Braille</h2>
    </div>
    <div class="translate-area">
      <textarea name="from" on:input={handleInput} class="translate-from" />
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
  header {
    margin: 40px;
    display: flex;
    justify-content: center;
    gap: 16px;
  }

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

  h1 {
    margin: 0;
    font-size: 4em;
    line-height: 1em;
    text-align: left;
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
    min-width: 400px;
    min-height: 300px;
    margin: 0;
    padding: 16px;
    font-size: 1rem;
    resize: none;
    border: none;
    outline: none;
  }
</style>
