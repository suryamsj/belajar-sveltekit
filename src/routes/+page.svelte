<script>
    import { fly } from "svelte/transition";
</script>

<svelte:head>
    <title>Sosial Media Downloader</title>
    <meta
        name="description"
        content="SMD atau Sosial Media Downloader adalah sebuah website untuk mendownload foto dan vidio dari sosial media
        yang tersedia kapanpun secara gratis."
    />
</svelte:head>

<!-- Section -->
<div class="row">
    <div class="col-lg-12 col-md-12 col-12">
        <div in:fly={{ y: -250, duration: 350, delay: 400 }}>
            <h1>Sosial Media Downloader</h1>
            <p>
                Website untuk download foto dan vidio dari sosial media yang
                tersedia kapanpun secara gratis.
            </p>
            <a class="btn btn-primary" href="/tiktok">Tiktok</a>
            <a class="btn btn-primary" href="/instagram">Instagram</a>
        </div>
    </div>
</div>

<style>
    .btn-primary {
        width: 250px;
        height: fit-content;
        padding: 10px 0;
        border-radius: 30px;
        margin: 5px 5px;
    }
</style>
