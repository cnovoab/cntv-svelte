<script>
  import categories from './data/categories.json';
  import shows from './data/catalog.json';
  import ShowThumbnail from './catalog/ShowThumbnail.svelte';
  const filterBy = (category) =>
    shows.filter(show => show.categoryCodes.includes(category));
</script>

<style>
</style>

{#each categories as category}
<h1>{category}</h1>
  {#each filterBy(category) as show}
    <ShowThumbnail 
      title={show.title}
      description="lorem ipsum"
      image={show.img}
    />
  {/each}
{/each}
