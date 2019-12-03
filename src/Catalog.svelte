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
h2 {
  color: #fff;
}
.scrolling-wrapper {
  overflow-x: scroll;
  overflow-y: hidden;
  white-space: nowrap;
}
.scrolling-wrapper .card {
  display: inline-block;
}

.scrolling-wrapper-flexbox {
  display: flex;
  flex-wrap: nowrap;
  overflow-x: auto;
}
.scrolling-wrapper-flexbox .card {
  flex: 0 0 auto;
  margin-right: 3px;
}

.card {
  border: 2px solid #a6192d;
  width: 150px;
  height: 75px;
  background: black;
}

.scrolling-wrapper,
.scrolling-wrapper-flexbox {
  height: 80px;
  margin-bottom: 20px;
  width: 100%;
  -webkit-overflow-scrolling: touch;
}
.scrolling-wrapper::-webkit-scrollbar,
.scrolling-wrapper-flexbox::-webkit-scrollbar {
  display: none;
}

</style>

<h1>Videoteca CNTV</h1>

{#each categories as category}
<h1>{category}</h1>
  <div class="scrolling-wrapper">
  {#each filterBy(category) as show}
    <div class="card">
      <ShowThumbnail 
        title={show.title}
        description="lorem ipsum"
        image={show.img}
      />
    </div>
  {/each}
  </div>
{/each}
