<script>
    import "bootstrap/dist/css/bootstrap.min.css";
    import "../assets/css/app.css";
    import Navbar from "../components/Navbar.svelte";
    import Section from "../components/Section.svelte";
</script>

<svelte:head>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
        href="https://fonts.googleapis.com/css2?family=League+Spartan:wght@500;600;700;800;900&family=Poppins:wght@300;400;500;600;700;800;900&display=swap"
        rel="stylesheet"
    />
    <script
        src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.1/dist/js/bootstrap.bundle.min.js"
        integrity="sha384-u1OknCvxWvY5kfmNBILK2hRnQC3Pr17a+RTT6rIHI7NnikvbZlHgTPOOmMi466C8"
        crossorigin="anonymous"></script>
</svelte:head>

<Navbar />
<main class="flex-shrink-0">
    <Section>
        <slot />
    </Section>
</main>
