<script>
  import SwitchBtn from "../../icons/SwitchBtn.svelte";

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
  <div class="switch-languages" on:click={handleSwitchLanguages}>
    <SwitchBtn widthBtn="40px" heightBtn="40px" />
  </div>
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
    overflow-x: hidden;
  }

  .translate-header h2 {
    margin: 0;
    padding: 12px 16px;
    width: 100%;
    text-align: left;
  }

  .switch-languages {
    cursor: pointer;
  }
</style>
