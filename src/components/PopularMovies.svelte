<script>
  export let popMovies;
  import Cards from "./Cards.svelte";
</script>

<h1>Popular movies page</h1>

<div class="popular-movies">
    {#each popMovies as movie}
    <Cards {movie} />
    {/each}
</div>

<style>
  h1{
    padding: 0 1rem;
  }
  .popular-movies {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-column-gap: 1rem;
    grid-row-gap: 2rem;
  }
</style>