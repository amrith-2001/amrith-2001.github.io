<script>
    import { onMount } from "svelte";
    import Layout from "../components/Layout.svelte";
    import { push } from 'svelte-spa-router';

    let posts = [];
    let error = null;

    onMount(async () => {
        try {
            const res = await fetch("/api/posts.json");
            if (!res.ok) throw new Error('Failed to fetch posts');
            posts = await res.json();
        } catch (err) {
            error = err.message;
        }
    });

    function goToPost(post) {
        push(`/Post/${post.id}`);
    }

    function goToAbout() {
        push('/about');
    }
</script>

<Layout title="Home">
    <h2>HTB Blog Posts</h2>
    {#if error}
        <p>Error: {error}</p>
    {:else if posts.length === 0}
        <p>Loading posts...</p>
    {:else}
        {#each posts as post}
            <article on:click={() => goToPost(post)} on:keydown={(e) => e.key === 'Enter' && goToPost(post)} tabindex="0" style="cursor: pointer;">
                <h3>{post.title}</h3>
                <p>{post.description}</p>
            </article>
        {/each}
    {/if}
</Layout>
