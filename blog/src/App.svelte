<script>
	import Router  from 'svelte-spa-router';
	import Home from './routes/Home.svelte';
	import Test from './routes/About.svelte';
	import Post from './routes/Posts.svelte';

	const routes = {
    // Exact path
    '/': Home,
    '/Post/:id': Post,
	'/about': Test
    
};
</script>

<main>
    <Router {routes}/>
</main>


