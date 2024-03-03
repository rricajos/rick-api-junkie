<script>
  export let character;

  function toggle() {
    let img = document.getElementById(character.id).children[0];
    img.classList.toggle("close-img");

    let article = document.getElementById(character.id).children[2];
    article.classList.toggle("show-article");
  }

  setTimeout(
    function () {
      toggle();
    },
    Math.floor(Math.random() * 1000),
  );
  console.log(character);
</script>

<button id={character.id} class="character" on:click={toggle}>
  <span class="close-img">
    <img
      id="{character.id}-img"
      src={character.image}
      alt={character.species}
    />
  </span>

  <h3>{character.name}</h3>

  <article class="show-article">
    <p>#{character.species}</p>
    <p>#{character.status}</p>

    <sup><i>{character.location.name}</i></sup>

    <p></p>
  </article>
</button>

<style>
  i {
    font-weight: lighter;
  }
  h3 {
    font-size: 1em;
    padding: 16px;
    margin: auto;
    text-shadow: 1px 1px 2px black;
  }
  img {
    border-top-right-radius: 8px;
    border-top-left-radius: 8px;
    width: 100%;
    height: 100%;
  }

  span {
    display: block;
    overflow: hidden;
    width: 100%;
    height: 256px;
    -webkit-transition: height .05s ease-in-out;
    -moz-transition: height .05s ease-in-out;
    -ms-transition: height .05s ease-in-out;
    -o-transition: height .05s ease-in-out;
    transition: height .05s ease-in-out;
  }
  .close-img {
    height: 0px;
  }

  @media screen and (orientation: portrait) {
    .character {
      width: 40vw;
      height: 64vw;
    }
  }

  @media screen and (orientation: landscape) {
    .character {
      width: 160px;
      height: 256px;
    }
  }

  .character {
    display: flex;
    flex-flow: column nowrap;
    align-items: center;
    overflow: hidden;
    margin-bottom: 0px;
    padding: 0;
    background-color: #213547;
    color: #fff;
    border: none;
    border-radius: 8px;
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.5);
    filter: brightness(100%);

    transform: scale(1);
    -webkit-transition: transform .05s ease-in-out;
    -moz-transition: transform .05s ease-in-out;
    -ms-transition: transform .05s ease-in-out;
    -o-transition: transform .05s ease-in-out;
    transition: transform .05s ease-in-out;

 
  }

  .character:hover {
    cursor: pointer;
    filter: brightness(108%);
    transform: scale(1.05);
    box-shadow: 0px 0px 16px rgba(0, 0, 0, 0.75);
  }

  article {
    display: none;
  }

  .show-article {
    display: block;
    widows: 100%;
  }
</style>
