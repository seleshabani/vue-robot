<template>
    <header>
        <nav>
            <RouterLink to="/">Home</RouterLink>
            <RouterLink to="/about">About</RouterLink>
        </nav>
    </header>
    <main class="container">
        <RouterView />
    </main>
    <footer>
        &copy; 2023
    </footer>
</template>

<script setup>
    //import { RouterLink, RouterView } from 'vue-router'
</script>

<style>

header{
    width: 100%;
    height: 50px;
    background: #fff;
    box-shadow: -2px 3px 30px -10px rgba(0,0,0,0.37);
}
nav{
    width: 100%;
    height: 100%;
    padding: 1rem;
    display: flex;
    flex-direction: row;
    gap: 1rem;
}

nav a.router-link-exact-active {
    background-color: cyan;
}

</style>

