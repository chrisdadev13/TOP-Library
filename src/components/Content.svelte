<script>
  import DarkMode from "./DarkMode.svelte";
  let read = 0;
  let unread = 0;
  let total = read + unread;
</script>

<main>
  <div class="libraryData">
    <p>Books read: {read}</p>
    <p>Books unread: {unread}</p>
    <p>Total Books: {total}</p>
    <DarkMode />
  </div>
</main>

<style>
  main {
    width: 100%;
  }
  .libraryData {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  .libraryData > p {
    margin: 10px 20px;
  }
</style>
