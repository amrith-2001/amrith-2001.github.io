<script>
    import { onMount } from "svelte";
    import Layout from "../components/Layout.svelte";
    import { push } from 'svelte-spa-router';
   

    let posts = [];

    onMount(async ()=>{
        const res = await fetch("/api/posts.json");
        posts = await res.json();
    });

    function goToPost(post) {
        push(`/posts/${post.id}`);
    }
</script>

<!-- svelte-ignore missing-declaration -->
<main>
<Layout title="Home">
    <h2>HTB Blog Posts</h2>
    {#each posts as post}
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <article on:click={() => goToPost(post)} style="cursor: pointer;" >
            <h3>{post.title}</h3>
            <p>{post.description}</p>
        </article>
    {/each}
</Layout>
</main>

<style>
    article {
        margin-bottom: 2rem;
    }
</style>