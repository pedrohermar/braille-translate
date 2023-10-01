<script>
  export let spanishText;

  function handleInput(e) {
    spanishText = e.target.value;
  }
</script>

<textarea
  name="from-spanish"
  on:input={handleInput}
  value={spanishText}
  class="from-spanish"
/>

<style>
  .from-spanish {
    width: 400px;
    height: 300px;
    margin: 0;
    padding: 16px;
    font-size: 1rem;
    resize: none;
    border: none;
    outline: none;
  }
</style>
