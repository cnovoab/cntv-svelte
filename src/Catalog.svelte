<script>
  import { Router, Route, Link } from 'svero';
  import categories from './data/categories.json';
  import shows from './data/catalog.json';
  import Show from './Show.svelte';
  import ShowThumbnail from './catalog/ShowThumbnail.svelte';
  const filterBy = (category) =>
    shows.filter(show => show.categories.includes(category));
</script>

<style>
</style>

<Router>
  <Route path="/show/:slug" component={Show} />
</Router>

{#each categories as category}
<h1>{category}</h1>
  {#each filterBy(category) as show}

  <Link href="/show/{show.slug}" episodes={show.episodes}>
    console.log('hola');
    <ShowThumbnail 
      title={show.title}
      description="lorem ipsum"
      image={show.img}
      episodes={show.episodes}
    />
  </Link>
  {/each}
{/each}
