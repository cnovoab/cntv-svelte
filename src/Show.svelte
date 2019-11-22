<script>
  const baseUrl = 'https://www.cntv.cl';
  import Episode from './Episode.svelte';
  import data from './data/el-reemplazante-1.json';
  let currentEpisodeIndex = 0;
  let currentEpisode = data.episodes[0];
  const changeEpisode = (event) => {
    const episodeNumber = event.target.dataset.episodeNumber;
    loadEpisode(episodeNumber);
  }
  const loadEpisode = (episodeNumber) => {
    currentEpisodeIndex = episodeNumber - 1;
    currentEpisode = data.episodes[currentEpisodeIndex];
  }
</script>

<style>
	h1 {
		color: black;
	}
</style>

<h1>{data.title}</h1>
<img src="{baseUrl}{data.img}" />
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
