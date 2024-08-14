<script>
    import { onMount } from 'svelte';
    import { location } from 'svelte-spa-router';

    let post;
    let contentHtml = '';
    let loading = true;
    let error = '';

    $: postId = $location.split('/')[2]; // Adjusted to match '/Post/:id' route

    onMount(async () => {
        try {
            const res = await fetch('/api/posts.json');
            if (!res.ok) throw new Error('Failed to fetch posts');

            const posts = await res.json();
            post = posts.find(p => p.id === postId);

            if (post && post.contentURL) {
                const contentRes = await fetch(post.contentURL);
                if (!contentRes.ok) throw new Error('Failed to fetch post content');

                contentHtml = await contentRes.text();
            } else {
                error = 'Post not found';
            }
        } catch (err) {
            error = err.message;
        } finally {
            loading = false;
        }
    });
</script>

<main>
    {#if loading}
        <p>Loading...</p>
    {:else if error}
        <p>Error: {error}</p>
    {:else if post}
        <h1>{post.title}</h1>
        <div>{@html contentHtml}</div>
    {:else}
        <p>Post not found</p>
    {/if}
</main>
