<script>
    import Login from "./Login.svelte"
</script>

<style>
    .links {
        display: flex;
        list-style-type: none;
        padding: 0.5rem;
    }

    .links > li {
        margin: 0 0.5rem;
    }

    nav {
        height: 3rem;
    }
</style>

<nav>
    <ul class="links">
        <li><a href="/">Home</a></li>
        <li><a href="/">My loadouts</a></li>
        <li><Login /></li>
    </ul>
</nav>