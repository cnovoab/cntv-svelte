<script>
  import { Router, Route, Link } from 'svero';
  import categories from './data/categories.json';
  import shows from './data/catalog.json';
  import Show from './Show.svelte';
  import ShowThumbnail from './catalog/ShowThumbnail.svelte';
  const filterBy = (category) =>
    shows.filter(show => show.categories.includes(category));
  let data = {id: 1};
</script>

<style>
</style>

<Router>
  <Route path="/show/:slug">
    <Show {data} />
  </Route>
</Router>

{#each categories as category}
<h1>{category}</h1>
  {#each filterBy(category) as show}
  data = show;
  <Link href="/show/{show.slug}" {data}>
    <ShowThumbnail 
      title={show.title}
      description="lorem ipsum"
      image={show.img}
    />
  </Link>
  {/each}
{/each}
