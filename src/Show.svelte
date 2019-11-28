<script>
  export let router = {};
  const baseUrl = 'https://www.cntv.cl';
  import Episode from './Episode.svelte';
  export let episodes = [];
  console.log('Router Params', router.params);
  console.log('Episodes', episodes);
  let currentEpisodeIndex = 0;
  let currentEpisode = episodes[0];
  const changeEpisode = (event) => {
    const episodeNumber = event.target.dataset.episodeNumber;
    loadEpisode(episodeNumber);
  }
  const loadEpisode = (episodeNumber) => {
    currentEpisodeIndex = episodeNumber - 1;
    currentEpisode = episodes[currentEpisodeIndex];
  }
</script>

<style>
	h1 {
		color: black;
	}
</style>

<h1>{title}</h1>
<img src="{baseUrl}{data.img}" alt="some alt" />
  {#each data.episodes as episode}
    <li>
      <button data-episode-number={episode.number} on:click={changeEpisode}> pitrili</button>
    </li>
  {/each}

  <Episode
    season=1
    number={currentEpisode.number}
    title={currentEpisode.title}
    description={currentEpisode.description}
    path={currentEpisode.path}
  />
