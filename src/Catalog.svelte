<script>
  import { Link } from 'svero'; 
  import categories from './data/categories.json';
  import shows from './data/catalog.json';
  import Show from './Show.svelte';
  import ShowThumbnail from './catalog/ShowThumbnail.svelte';
  const filterBy = (category) =>
    shows.filter(show => show.categories.includes(category));
</script>

<style>
.bottom-vids {
  height:230px;
  display: inline-block;
  color: #f1f1f1;
  position: relative;
  left:0;
  right:0;
  overflow-x: scroll;
  width: 100%;
}
a {
 text-decoration: none;
 color: rgba(100,100,100, 0.2);
}
</style>

<h1>Videoteca CNTV</h1>

{#each categories as category}
<h1>{category}</h1>
<div class="bottom-vids">
  {#each filterBy(category) as show}
    <ShowThumbnail 
      title={show.title}
      description="lorem ipsum"
      image={show.img}
    />
  {/each}
</div>
{/each}
