<script>
  import Content from "./Content.svelte";
  const logo = "📦";
  const brandName = "Dpad Library";

  let check = false;

  let title = "";
  let author = "";
  let pages = "";

  let data = [];

  function addBook() {
    if (
      (title == "") == false &&
      (author == "") == false &&
      (pages == "") == false
    ) {
      let readed = check;
      let newBook = {
        title: title,
        author: author,
        pages: pages,
        readed: readed,
      };

      title = "";
      author = "";
      pages = "";
      check = false;

      data = [...data, newBook];
    } else {
      console.log("MI loco escribe algo");
    }
  }

  function removeBook(index) {
    data.splice(index, 1);
    data = data;
  }
</script>

<main>
  <!--Logo-->
  <nav>
    <div class="brandContainer">
      <h1 class="brandLogo">{logo}</h1>
      <h1 class="brandName">{brandName}</h1>
    </div>
    <div class="dataContainer">
      <input
        type="text"
        placeholder="What's the name of the book?"
        bind:value={title}
      />
      <input
        type="text"
        placeholder="Who's the author of the book?"
        bind:value={author}
      />
      <input
        type="number"
        placeholder="How many pages are in the book?"
        bind:value={pages}
      />
      <form class="checkContainer">
        <input type="checkbox" bind:checked={check} />
        {#if check}
          <span>I already read this book 😎</span>
        {:else}
          <span>I have not read this book 🙂</span>
        {/if}
      </form>
      <button on:click={addBook}> Add to the library </button>
    </div>
  </nav>
</main>

<div class="content">
  <Content />
  <div class="infoContainer">
    <p>Title</p>
    <p>Author</p>
    <p>Pages</p>
    <p>Readed</p>
  </div>
  <div class="booksContainer">
    {#each data as book, index}
      <div class="books">
        <p class="bookAttribute">{book.title}</p>
        <p class="bookAttribute">{book.author}</p>
        <p class="bookAttribute">{book.pages}</p>
        {#if book.readed == true}
          <p class="bookAttribute">Yes</p>
        {:else}
          <p class="bookAttribute">No</p>
        {/if}
        <p on:click={() => removeBook(index)} class="bookAttribute remove">X</p>
      </div>
    {/each}
  </div>
</div>

<style>
  main {
    margin-top: -8px;
    width: 20vw;
    height: 100vh;
    margin-left: 20px;
  }
  .brandContainer {
    display: flex;
    cursor: pointer;
  }
  .brandName {
    margin-left: 15px;
  }
  .dataContainer {
    display: flex;
    flex-direction: column;
  }
  input {
    margin: 20px 0;
    border-top: none;
    border-right: none;
    border-left: none;
    background-color: #f2eee2;
    transition: background-color 0.3s;
  }
  input:active {
    border: none;
  }
  :global(body.dark-mode) input {
    background-color: #1d3030;
    color: white;
  }
  button {
    transition: 0.3s ease-in-out;
    cursor: pointer;
  }
  button:hover {
    background-color: #99c1f1;
    color: white;
  }
  .content {
    width: 100%;
  }
  .booksContainer {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .books {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 70vw;
    border: 1px solid black;
  }
  .bookAttribute {
    margin: 5px 50px;
    width: 10vw;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .infoContainer {
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    width: 70vw;
  }
  .infoContainer > p {
    margin: 5px 100px;
    font-weight: 700;
  }
  .remove {
    color: red;
    cursor: pointer;
  }
</style>
