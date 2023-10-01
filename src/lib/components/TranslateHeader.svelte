<script>
  export let languageFrom;
  export let languageTo;
  export let resetText;

  function handleSwitchLanguages(e) {
    resetText();
    [languageFrom, languageTo] = [languageTo, languageFrom];
  }
</script>

<div class="translate-header">
  <h2>{languageFrom}</h2>
  <button class="switch-languages" on:click={handleSwitchLanguages} />
  <h2>{languageTo}</h2>
</div>

<style>
  .translate-header {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
    background-color: rgb(254, 224, 80);
  }

  .translate-header h2 {
    margin: 0;
    padding: 12px 16px;
    width: 100%;
    text-align: left;
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
</style>
