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
/* Global Variables */
:root {

      /* Tile Dimensions */
      --carousel-tile-height:  calc(var(--carousel-tile-width) / (16 / 9));

      /* Growth Factor */
      --carousel-growth-factor: 1.5;

      /* Fade to Opacity */
      --carousel-fade-opacity:   0.25;
      --carousel-normal-opacity: 1;

      /* Automatic Offsets - DO NOT ALTER */
      --carousel-offset-left:  calc(-1 * (var(--carousel-tile-width) * (var(--carousel-growth-factor) - 1) / 2));
      --carousel-offset-right: calc(var(--carousel-tile-width) * (var(--carousel-growth-factor) - 1));

      /* Transition Speeds */
      --carousel-transition-1: 1s;
      --carousel-transition-2: 0.5s;
      --carousel-transition-3: 0.3s;

}

/* Carousel Container */
.carousel {
      margin: 0;
      box-sizing: border-box;
      width: 100%;
      overflow-x: auto;
      overflow-y: hidden;
}

/* Carousel Row */
.carousel-row {
      white-space: nowrap;
      margin-top: calc((var(--carousel-tile-height) * (var(--carousel-growth-factor) - 1)) / 2);
      margin-bottom: calc((var(--carousel-tile-height) * (var(--carousel-growth-factor) - 1)) / 2);
      margin-left: calc((var(--carousel-tile-width) * (var(--carousel-growth-factor) - 1)) / 2);
      margin-right: calc((var(--carousel-tile-width) * (var(--carousel-growth-factor) - 1)) / 2);
      transition: var(--carousel-transition-2);
}

/* Content Tile */
.carousel-tile {
      position: relative;
      display: inline-block;
      width: var(--carousel-tile-width);
      height: var(--carousel-tile-height);
      margin-right: var(--carousel-tile-spacing);
      transition: var(--carousel-transition-2);
      -webkit-transform-origin: center left;
      transform-origin: center left;
      cursor: pointer;
      cursor: hand;
}

/* Add Extra Margin to Last Carousel Tile */
.carousel-tile:last-of-type {
      margin-right: calc(var(--carousel-tile-width)/2);
}

/* Ensure All Elements Inside Tile are Block */
.carousel-tile * {
      display: block;
}

/* Carousel Row on Hover */
.carousel-row:hover {
      -webkit-transform: translate3d(var(--carousel-offset-left), 0, 0);
      transform: translate3d(var(--carousel-offset-left), 0, 0);
}

/* Content Tile on Carousel Row Hover */
.carousel-row:hover .carousel-tile {
      opacity: var(--carousel-fade-opacity);
}

/* Content Tile on Hover on Carousel Row Hover */
.carousel-row:hover .carousel-tile:hover {
      -webkit-transform: scale(var(--carousel-growth-factor));
      transform: scale(var(--carousel-growth-factor));
      opacity: var(--carousel-normal-opacity);
}

/* Content Tile on Hover */
.carousel-tile:hover ~ .carousel-tile {
      -webkit-transform: translate3d(var(--carousel-offset-right), 0, 0);
      transform: translate3d(var(--carousel-offset-right), 0, 0);
}
</style>

<h1>Videoteca CNTV</h1>

<div class="carousel">
{#each categories as category}
<h1>{category}</h1>
  <div class="carousel-row">
  {#each filterBy(category) as show}
    <Link href="/show/{show.slug}">
    <div class="carousel-tile">
      <ShowThumbnail 
        title={show.title}
        description="lorem ipsum"
        image={show.img}
      />
    </div>
    </Link>
  {/each}
  </div>
{/each}
</div>
