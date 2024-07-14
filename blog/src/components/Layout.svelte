<script>
    export const title = "HTB Blog";
</script>

<header>
    <h1>HTB Blog</h1>
    <nav>
        <a href="/">Home</a>
        <a href="/about">About</a>
    </nav>

    <main>
        <slot></slot>
    </main>

    <footer>
        <p>2024 HTB Blog</p>
    </footer>

    <style>
        header {
            background: #333;
            color: white;
            padding: 1rem;
        }
        nav a {
            margin: 0 1rem;
            color: white;
            text-decoration: none;
        }
        main {
            padding: 1rem;
        }
        footer {
            text-align: center;
            padding: 1rem;
            background: #eee;
        }
    </style>

</header>