<script>
  import Character from "./lib/Character.svelte";

  let info = {};
  let characters = [];
  let page = 9;

  async function loadCharacters() {
    const response = await fetch(
      "https://rickandmortyapi.com/api/character?page=" + page,
    );
    const data = await response.json();
    info = data.info;
    characters = data.results;
    //  console.log(info.pages)
  }

  function nextPage() {
    page++;
    loadCharacters();
  }
  function prevPage() {
    page--;
    loadCharacters();
  }

  loadCharacters();
</script>

<h1>Rick and Morty API Consume</h1>

<hr />
<h2>{info.count} characters in {info.pages} pages</h2>
<header>
  <button on:click={prevPage} disabled={page === 1}>Prev</button>
  <h3>{page} / {info.pages}</h3>
  <button on:click={nextPage} disabled={page === info.pages}>Next</button>
</header>

<main class="characters-container">
  {#each characters as character}
    <Character {character} />
  {/each}
</main>

<header>
  <button on:click={prevPage} disabled={page === 1}>Prev</button>
  <h3>{page} / {info.pages}</h3>
  <button on:click={nextPage} disabled={page === info.pages}>Next</button>
</header>

<style>
  header {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-around;
    align-items: baseline;
    padding: 2rem;
  }
  button {
    background-color: #213547;
    color: #fff;
  }

  main {
    max-width: 720px;
  }

  @media screen and (orientation: portrait) {
    .characters-container {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 2rem;
    }
  }

  @media screen and (orientation: landscape) {
    .characters-container {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 2rem;
    }
  }
</style>
