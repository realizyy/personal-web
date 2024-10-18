<script>
    import "../app.css";
    import Navbar from "$lib/components/Navbar/Navbar.svelte";
</script>

<svelte:head>
    <title>Hello There~</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,200..900;1,200..900&display=swap');
    </style>
</svelte:head>

<div class="container mx-auto">
    <Navbar />
    <div class="content container">
        <slot />
    </div>
</div>

<style lang="scss">


</style>