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
    width: 50%;
    height: 300px;
    margin: 0;
    padding: 16px;
    font-size: 16px;
    background-color: #e8e8e8;
    border: none;
    outline: none;
    box-sizing: border-box;
    resize: none;
  }

  @media (max-width: 768px) {
    .from-spanish {
      width: 100%;
    }
  }
</style>
