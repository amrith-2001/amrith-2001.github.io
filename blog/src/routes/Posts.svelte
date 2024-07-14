<script>
    import { onMount } from 'svelte';
    import { wrap } from 'svelte-spa-router/wrap';
    import { Router, Route, Link } from 'svelte-routing';
    import { useParams } from 'svelte-routing';

    let post;
    let contentHtml = '';

    const {id} = useParams();
    
    onMount(async () => {
        const res = await fetch(`/api/posts.json`);
        const posts = await res.json();
        post = posts.find(p => p.id == id);

        if(post) {
            const contentRes = await fetch(post.contentUrl);
            contentHtml = await contentRes.text();
        }
    });
</script>

<main>
    {#if post}
        <h1>{post.title}</h1>
        <div>{@html contentHtml}</div>
    {/if}
</main>

<style></style>