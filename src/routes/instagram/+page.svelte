<script>
    import { fly, fade } from "svelte/transition";

    let param = "";
    let respon = null;
    let loading = false;

    const submitUrl = async (param) => {
        try {
            loading = true;
            const response = await fetch(
                `https://instagram-downloader-download-instagram-videos-stories.p.rapidapi.com/index?url=${encodeURIComponent(
                    param
                )}`,
                {
                    method: "GET",
                    headers: {
                        "X-RapidAPI-Key":
                            "db34aef518mshd72bed26734648cp1821d5jsn504923a9ae87",
                        "X-RapidAPI-Host":
                            "instagram-downloader-download-instagram-videos-stories.p.rapidapi.com",
                    },
                }
            );
            const data = await response.json();
            respon = data[0];
            return respon;
        } catch (error) {
            console.log(error);
        } finally {
            loading = false;
        }
    };
</script>

<svelte:head>
    <title>Sosial Media Downloader - Instagram</title>
    <meta
        name="description"
        content="ID atau Instagram Downloader adalah sebuah website untuk mendownload foto dan vidio dari instagram kapanpun secara gratis."
    />
</svelte:head>

<!-- Section -->
<div in:fly={{ y: -250, duration: 350, delay: 400 }}>
    <div class="row mb-3">
        <div class="col-lg-12 col-md-12 col-12">
            <h1>Instagram Downloader</h1>
            <p>
                Website untuk mendownload Reels, IGTV , Videos , Photos ,
                Stories , Carousel & Profile Pictures Instagram.
            </p>
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
                                id="instagram_link"
                                placeholder="Instagram link here"
                                bind:value={param}
                                autocomplete="off"
                                required
                            />
                            <label for="instagram_link"
                                >Instagram link here</label
                            >
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
    <div in:fade={{ y: -250, duration: 350, delay: 400 }}>
        <div class="row justify-content-center text-center mb-3">
            <div class="col-lg-6 col-md-12 col-12">
                <div class="card">
                    <div class="card-body">
                        <div class="row justify-content-center text-center">
                            <div class="col-lg-12 col-md-12 col-12">
                                <span class="title">Download :</span>
                                <a
                                    class="btn btn-primary me-2 mb-2"
                                    href={respon.media}
                                    target="_blank">Original</a
                                >
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
{/if}

<style>
    img {
        width: 90px;
        height: auto;
    }
</style>
