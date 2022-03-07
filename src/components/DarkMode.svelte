<script>
  let dark = false;
  function toggle() {
    window.document.body.classList.toggle("dark-mode");
    if (dark == false) {
      dark = true;
    } else {
      dark = false;
    }
  }
</script>

<main>
  {#if dark == true}
    <button on:click={toggle}>☀️</button>
  {:else}
    <button on:click={toggle}>🌙</button>
  {/if}
</main>

<style>
  :global(body) {
    background-color: #f2eee2;
    color: #0084f6;
    transition: background-color 0.3s;
  }
  :global(body.dark-mode) {
    background-color: #1d3030;
    color: #bfc2c7;
  }
  button {
    background-color: #f76027;
    border: none;
    border-radius: 4px;
    padding: 0.5rem;
    cursor: pointer;
    height: 3.5vh;
    width: 1.5vw;
    text-align: center;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 5px;
  }
  :global(body.dark-mode) button {
    background-color: #0084f6;
    color: white;
  }
</style>
