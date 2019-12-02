<script>
  const baseUrl = 'https://www.cntv.cl';
  export let title;
  export let description;
  export let image; 
</script>

<style>
#bottom-vids {
 height: 200px;
 width: 360px;
 display: relative;
 transition: transform .4s;
}
#bottom-vids:hover {
 transform: scale(1.3);
}
</style>

<img id="bottom-vids" src="{baseUrl}{image}" alt=""  />
