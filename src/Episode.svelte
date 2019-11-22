<script>
  import { afterUpdate } from 'svelte'
  const baseUrl = 'https://www.cntv.cl';
  export let season;
  export let number;
  export let title;
  export let description;
  export let path;
  let episodeVideo;

  afterUpdate(async () => {
    episodeVideo.load();
  })
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<h2>Season {season} - Episode {number}</h2>
<h3>{title}</h3>
<p>{description}</p> 

<video bind:this={episodeVideo} controls width="100%">
    <source src="{baseUrl}{path}" type="video/mp4">

    Sorry, your browser doesn't support embedded videos.
</video>
