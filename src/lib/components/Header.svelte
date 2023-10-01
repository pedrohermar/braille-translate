<header>
  <img src="braille.svg" alt="Logo Braille" height="140px" width="140px" />
  <div class="logo-title">
    <h1>Traductor</h1>
    <h1>Braille</h1>
  </div>
</header>

<style>
  header {
    width: 100%;
    margin: 40px;
    display: flex;
    justify-content: center;
    gap: 16px;
  }

  h1 {
    margin: 0;
    font-size: 4em;
    line-height: 1em;
    text-align: left;
  }

  @media (max-width: 768px) {
    header {
      width: 200px;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      margin: 40px auto;
    }

    .logo-title {
      display: flex;
      flex-direction: column;
      align-items: center;
    }
  }
</style>
