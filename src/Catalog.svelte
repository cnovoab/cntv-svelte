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
body,
html {
  padding: 0 10px;
  margin: 0;
  background: #0e0f11;
  color: #ecf0f1;
  font-family: 'Open Sans', sans-serif;
  min-height: 100vh;
  display: flex;
  flex-direction: row;
  align-items: center;
  width: 100%;
}
* {
  box-sizing: border-box;
}
h1,
p {
  text-align: center;
}
p {
  width: 100%;
  max-width: 500px;
  margin: auto;
}
a:link,
a:hover,
a:active,
a:visited {
  transition: color 150ms;
  color: #95a5a6;
  text-decoration: none;
}
a:hover {
  color: #7f8c8d;
  text-decoration: underline;
}
.contain {
  width: 100%;
}
.row {
  overflow: scroll;
  width: 100%;
}
.row__inner {
  transition: 450ms -webkit-transform;
  transition: 450ms transform;
  transition: 450ms transform, 450ms -webkit-transform;
  font-size: 0;
  white-space: nowrap;
  margin: 70.3125px 0;
  padding-bottom: 10px;
}
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
