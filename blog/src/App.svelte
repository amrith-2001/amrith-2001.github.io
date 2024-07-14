<script>
	import Router  from 'svelte-spa-router';
	import Home from './routes/Home.svelte';
	import About from './routes/About.svelte';
	import Post from './routes/Posts.svelte';

	const routes = {
    // Exact path
    '/': Home,

    
    '/about': About,

   
    '/Post/:id': Post
    
}
</script>

<main>
    <Router {routes}/>
</main>


