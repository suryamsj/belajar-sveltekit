<script>
    import { fly, fade } from "svelte/transition";
    let param = "";
    let respon = null;
    let loading = false;

    const submitUrl = async (param) => {
        try {
            loading = true;
            const response = await fetch(
                "https://hadi-api.herokuapp.com/api/tiktok/?url=" + param,
                {
                    method: "GET",
                }
            );
            const data = await response.json();
            respon = data;
            return respon;
        } catch (error) {
            console.log(error);
        } finally {
            loading = false;
        }
    };
</script>

<svelte:head>
    <title>Sosial Media Downloader - Tiktok Downloader</title>
    <meta
        name="description"
        content="TD atau Tiktok Downloader adalah web yang dapat membantu anda untuk mendownload vidio Tiktok tanpa watermark dari mana saja dan kapan saja"
    />
</svelte:head>

<!-- Section -->
<div in:fly={{ y: -250, duration: 350, delay: 400 }}>
    <div class="row mb-3">
        <div class="col-lg-12 col-md-12 col-12">
            <h1>Tiktok Downloader</h1>
            <p>Website untuk mendownload vidio tiktok tanpa watermark.</p>
        </div>
    </div>
    <div class="row mb-3">
        <div class="col-lg-12 col-md-12 col-12">
            <div class="card" id="card__form">
                <div class="card-body">
                    <form on:submit|preventDefault={submitUrl(param)}>
                        <div class="form-floating mb-3">
                            <input
                                type="text"
                                class="form-control"
                                id="tiktok_link"
                                placeholder="Tiktok link here"
                                bind:value={param}
                                autocomplete="off"
                                required
                            />
                            <label for="tiktok_link">Tiktok link here</label>
                        </div>
                        <div class="mb-3">
                            <button
                                class="btn btn-primary btn-lg w-100"
                                type="submit">Download</button
                            >
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>
{#if loading === true}
    <img src="/loading.svg" alt="Loading" />
{:else if respon != null}
    {#if respon.status !== 200}
        <p>{respon.msg}</p>
    {:else if respon.status === 200}
        <div in:fade={{ y: -250, duration: 350, delay: 400 }}>
            <div class="row justify-content-center text-center mb-3">
                <div class="col-lg-6 col-md-12 col-12">
                    <div class="card">
                        <div class="card-body">
                            <video
                                controls
                                src={respon.result.video.mp4}
                                poster="/player.png"
                            >
                                <track kind="captions" />
                                Maaf browser kamu tidak support untuk menampilkan
                                vidio yang ingin kamu download. Tapi, jangan khawatir
                                karena kamu masih bisa untuk mendownload nya.
                            </video>
                            <div class="row justify-content-center text-center">
                                <div class="col-lg-12 col-md-12 col-12">
                                    <span class="title">Download :</span>
                                    <a
                                        class="btn btn-primary me-2 mb-2"
                                        href={respon.result.audio_only.audio1}
                                        download>Audio (Original)</a
                                    >
                                    <a
                                        class="btn btn-primary mb-2"
                                        href={respon.result.video.original}
                                        download>Video (Original)</a
                                    >
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    {/if}
{/if}

<style>
    video {
        width: 100%;
        height: auto;
    }

    img {
        width: 90px;
        height: auto;
    }
</style>
