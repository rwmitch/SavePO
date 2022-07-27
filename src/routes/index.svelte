<script context="module" lang="ts">
	export const prerender = true;
</script>

<h1 class="title">#SaveYourPostOffice Resources</h1>
<ul>
  <a class="poster" href="/Click_and_Drop.pdf">
    <img src="Click_and_Drop.png" alt="Click and Drop Poster" />
  </a>
  <a class="poster" href="/ByeLocal.pdf">
    <img src="ByeLocal.png" alt="Bye Local Poster" />
  </a>
  <a class="poster" href="/SteveFrogatt_Banking.jpg">
    <img src="SteveFrogatt_Banking.jpg" alt="Banking Poster" />
  </a>
  <a class="poster" href="/SteveFrogatt_NominalFee.jpg">
    <img src="SteveFrogatt_NominalFee.jpg" alt="Nominal Poster" />
  </a>
</ul>


<style>
  * {
    font-family: 'Verdana', sans-serif;
  }

  :global(body) {
    background-color: #ccc;
  }

  .title {
    width: 100%;
    text-align: center;
    font-size: 2.5em;
  }

  ul {
    margin: 0;
    padding: 0;
    display: flex;
    width: 100vw;
    flex-wrap: wrap;
    justify-content: space-evenly;
  }

  .poster img {
    width: calc(100vw / 4 - 1vw);
  }
</style>
