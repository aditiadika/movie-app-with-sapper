<script>
  import { onMount } from "svelte";

  let movie;
  const POSTER_PATH = "http://image.tmdb.org/t/p/w154";

  onMount(async () => {
    const res = await fetch(
      `https://api.themoviedb.org/3/discover/movie?api_key=c1593a564f54f40619768a13410661be&language=en-US&sort_by=popularity.desc&include_adult=false&include_video=false&page=1`
    );
    movie = await res.json();
    console.log(movie)
  });
</script>

<style>
  .wrapper {
    display: grid;
    grid-template-columns: repeat(6, 1fr);
    grid-row-gap: 1rem;
  }
  .item {
    margin: 1em 0.5em;
    width: 182px;
  }
  img {
    box-shadow: 0 0 35px black;
  }
</style>

<svelte:head>
  <title>Movie App!</title>
</svelte:head>

{#if movie}
  <div class="wrapper">
    {#each movie.results as row}
      <div class="" style="justify-content: space-between; ">
        <a href="{row.id}">
          <img src={`${POSTER_PATH}${row.poster_path}`} alt="" />
        </a>
        <p>{row.title}</p>
      </div>
    {/each}
  </div>
{:else}
  <p>Loading...</p>
{/if}
