<script>
    import "../app.css";
    import Navbar from "$lib/components/Navbar/Navbar.svelte";
    import Footer from "$lib/components/Footer/Footer.svelte";
</script>

<svelte:head>
    <title>Hello There~</title>
</svelte:head>

<div class="container content max-h-screen mx-auto">
    <Navbar />
    <slot />
    <Footer />
</div>
