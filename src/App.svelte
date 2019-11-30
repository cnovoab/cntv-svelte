<script>
  import { Router, Route } from 'svero';
  import Catalog from './Catalog.svelte';
  import Show from './Show.svelte';
</script>

<style>
</style>

<Router>
  <Route path="/" component={Catalog} />
  <Route component={Show} path="/show/:slug" />
</Router>

