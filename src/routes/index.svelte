<script>
  import { Router, Route } from 'svelte-routing';
  import Home from '../pages/Home.svelte';
  import Redirect from '../pages/Redirect.svelte';
  export let url = '';
</script>

<Router {url}>
  <div>
    <Route path="/" component={Home} />
    <Route component={Redirect} />
  </div>
</Router>