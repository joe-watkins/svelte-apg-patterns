<script>
    import Header from "../components/global/Header.svelte";
    import Footer from "../components/global/Footer.svelte";
    import "../app.css";
</script>

<Header />

<main class="container mx-auto xl mb-10" tabindex="-1">
    <slot />
</main>

<Footer />