<script>
  import shows from './data/catalog.json';
  import ShowThumbnail from './catalog/ShowThumbnail.svelte';
  const categories = Array.from(
    new Set(shows.map(show => show.categoryCodes).flat())
  );
  console.log('CATEGORIES', categories);
  const filterBy = (category) =>
    shows.filter(show => show.categoryCodes.includes(category));
</script>

<style>
</style>

{#each categories as category}
<h1>{category}</h1>
<div class="row">
  <div class="row__inner">
    {#each filterBy(category) as show}
      <ShowThumbnail 
        title={show.title}
        description="lorem ipsum"
        image={show.img}
      />
    {/each}
  </div>
</div>
{/each}
