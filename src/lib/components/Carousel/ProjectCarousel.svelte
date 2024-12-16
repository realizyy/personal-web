<script>
    import { onMount } from "svelte";
    import emblaCarouselSvelte from 'embla-carousel-svelte';
    import Autoplay from "embla-carousel-autoplay";

    let emblaApi;
    let options = { loop: true };
    let plugins = [Autoplay({ delay: 3000, stopOnInteraction: false })];

    export let images = [];
    export let title = '';

    function onInit(event) {
        emblaApi = event.detail;
    }
</script>

<div class="embla w-full h-48 overflow-hidden">
    <div class="embla__container flex" use:emblaCarouselSvelte={{ }} on:emblaInit={onInit}>
        <div class="embla__container h-full">
            {#each images as image, index}
                <div class="embla__slide flex-[0_0_100%] h-full">
                    <img
                            src={image}
                            alt={`${title} - Image ${index + 1}`}
                            class="w-full h-full object-cover"
                    />
                </div>
            {/each}
        </div>
    </div>
</div>