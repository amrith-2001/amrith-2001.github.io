<script>
    export const title = "HTB Blog";
</script>

<div class="layout">
    <header>
        <div class="header-content">
            <h1>{title}</h1>
            <nav>
                <a href="/">Home</a>
                <a href="/#/about">About</a>
            </nav>
        </div>
    </header>

    <main>
        <slot></slot>
    </main>

    <footer>
        <p>&copy; 2024 HTB Blog</p>
    </footer>
</div>

<style>
    /* Global styles */
    :global(body) {
        font-family: Arial, sans-serif;
        line-height: 1.6;
        color: #333;
        margin: 0;
        padding: 0;
        background-color: #f4f4f4;
    }

    .layout {
        display: flex;
        flex-direction: column;
        min-height: 100vh;
    }

    /* Header styles */
    header {
        background: #2c3e50;
        color: white;
        padding: 1rem 0;
        box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }

    .header-content {
        max-width: 1200px;
        margin: 0 auto;
        padding: 0 1rem;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    h1 {
        margin: 0;
        font-size: 1.8rem;
    }

    nav {
        display: flex;
        gap: 1rem;
    }

    nav a {
        color: white;
        text-decoration: none;
        padding: 0.5rem 1rem;
        border-radius: 4px;
        transition: background-color 0.3s;
    }

    nav a:hover {
        background-color: rgba(255,255,255,0.1);
    }

    /* Main content styles */
    main {
        flex: 1;
        max-width: 1200px;
        margin: 2rem auto;
        padding: 0 1rem;
        background-color: white;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
        border-radius: 8px;
    }

    /* Footer styles */
    footer {
        text-align: center;
        padding: 1rem;
        background: #34495e;
        color: white;
        font-size: 0.9rem;
    }
</style>
