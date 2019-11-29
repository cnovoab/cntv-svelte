<script>
  import { Link } from 'svero'; 
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

<h1>Videoteca CNTV</h1>

{#each categories as category}
<h1>{category}</h1>
  {#each filterBy(category) as show}
  <Link href="/show/{show.slug}">
    <ShowThumbnail 
      title={show.title}
      description="lorem ipsum"
      image={show.img}
    />
  </Link>
  {/each}
{/each}
