<script>
    import "../app.css";
    import Navbar from "$lib/components/Navbar/Navbar.svelte";
    import Footer from "$lib/components/Footer/Footer.svelte";
</script>

<svelte:head>
    <title>Hello There~</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Source+Sans+3:ital,wght@0,200..900;1,200..900&display=swap');
    </style>
</svelte:head>

<div class="container content max-h-screen mx-auto">
    <Navbar />
    <slot />
    <Footer />
</div>
