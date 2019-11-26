<script>
  const baseUrl = 'https://www.cntv.cl';
  export let title;
  export let description;
  export let image; 
</script>

<style>
</style>

<div class="tile">
  <div class="tile__media">
    <img class="tile__img" src="{baseUrl}{image}" alt=""  />
  </div>
  <div class="tile__details">
    <div class="tile__title">
      {title}
    </div>
  </div>
</div>
