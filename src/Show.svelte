<script>
	import { onMount } from 'svelte';
	import { Router, Link } from 'svero';
  import Episode from './Episode.svelte';
  import shows from './data/catalog.json';
  export let data = {};
  let episodes = [];
  let currentEpisode = {};
  export let router = {};
  const baseUrl = 'https://www.cntv.cl';
  onMount(() => {
    data = shows.find(s => s.slug === router.params.slug);
    episodes = data.episodes;
    currentEpisode = episodes[0];
  });
  const changeEpisode = (event) => {
    const episodeNumber = event.target.dataset.episodeNumber;
    loadEpisode(episodeNumber);
  }
  const loadEpisode = (episodeNumber) => {
    currentEpisode = episodes[episodeNumber - 1];
  }

</script>

<style>
/* Split the screen in half */
.split {
  height: 100%;
  width: 50%;
  position: fixed;
  z-index: 1;
  top: 0;
  overflow-x: hidden;
  padding-top: 20px;
}

/* Control the left side */
.left {
  left: 0;
  background-color: #111;
}

/* Control the right side */
.right {
  right: 0;
  background-color: red;
}

/* If you want the content centered horizontally and vertically */
.episodes {
  position: absolute;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: left;
}
</style>


<div class="split left">
  <Link href="/home">
    <div id="back">Back</div>
  </Link>

  <h1>{data.title}</h1>
  <img src="{baseUrl}{data.img}" alt="some alt" />
  <div class="episodes">
    <ul>
      {#each episodes as episode}
      <li>
        <button data-episode-number={episode.number} on:click={changeEpisode}>
          Ep. {episode.number}: {episode.title}
        </button>
      </li>
      {/each}
    </ul>
  </div>
</div>

<div class="split right">
  <Episode
    season=1
    number={currentEpisode.number}
    title={currentEpisode.title}
    description={currentEpisode.description}
    path={currentEpisode.path}
  />
</div>
